---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

<h1>
    Stream.FM <span class="reference" data-ref="streamfm"></span>: Real-Time Streamable Generative Speech Restoration with Flow Matching
</h1>

<p class="left-align">
    Simon Welker, Bunlong Lay, Maris Hillemann, Tal Peer, Timo Gerkmann
</p>
<p class="left-align">
    <a href="#todo">arXiv preprint (coming soon)</a>
</p>

<h2>
    Abstract
</h2>

<p class="abstract">
    Diffusion-based generative models have greatly impacted the speech processing field in recent years,
    exhibiting high speech naturalness and spawning a new research direction. Their application in real-time
    communication is, however, still lagging behind due to their computation-heavy nature involving multiple
    calls of large DNNs.
</p>
<p class="abstract">
    Here, we present Stream.FM <span class="reference" data-ref="streamfm"></span>, a frame-causal flow-based generative model with an algorithmic latency of 32
    milliseconds (ms) and a total latency of 48 ms, paving the way for generative speech processing in
    real-time communication. We propose a buffered streaming inference scheme and an optimized DNN architecture,
    show how learned few-step numerical solvers can boost output quality at a fixed compute budget, explore
    model weight compression to find favorable points along a compute/quality tradeoff, and contribute a model
    variant with 24 ms total latency for the speech enhancement task.
</p>
<p>
    Our work looks beyond theoretical latencies, showing that high-quality streaming generative speech processing
    can be realized on consumer GPUs available today. Stream.FM <span class="reference" data-ref="streamfm"></span> can solve a variety of speech processing tasks in
    a streaming fashion: speech enhancement, dereverberation, codec post-filtering, bandwidth extension, STFT
    phase retrieval, and Mel vocoding. As we verify through comprehensive evaluations and a MUSHRA listening test,
    Stream.FM <span class="reference" data-ref="streamfm"></span> establishes a state-of-the-art for generative streaming speech restoration, exhibits only a
    reasonable reduction in quality compared to a non-streaming variant, and outperforms our recent work
    (Diffusion Buffer <span class="reference" data-ref="diffbuff-interspeech"></span><span class="reference" data-ref="diffbuff-journal"></span>) on generative streaming speech enhancement while operating at a lower latency.
</p>


<h2>Speech Enhancement</h2>
<p>Select an audio file: &nbsp;&nbsp; <br class="smallmobile-only">
    <select id="audioSelect0" onchange="playAudio0()">
        <option value="p102_84" selected>p102_84</option>
            <option value="p102_382">p102_382</option>
            <option value="p103_731">p103_731</option>
            <option value="p103_299">p103_299</option>
            <option value="p104_302">p104_302</option>
            <option value="p104_825">p104_825</option>
            <option value="p105_784">p105_784</option>
            <option value="p105_353">p105_353</option>
            <option value="p106_843">p106_843</option>
            <option value="p106_813">p106_813</option>
            <option value="p107_800">p107_800</option>
            <option value="p107_216">p107_216</option>
    </select>
</p>

<p class="black">
Clean: <br>
 <audio id="audioPlayer0_clean" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Noisy: <br>
 <audio id="audioPlayer0_noisy" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (4xEuler): <br>
 <audio id="audioPlayer0_stream_fm_4xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Diffusion Buffer <span class="reference" data-ref="diffbuff-interspeech"></span><span class="reference" data-ref="diffbuff-journal"></span> (d=0): <br>
 <audio id="audioPlayer0_diffusion_buffer_d_0" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Diffusion Buffer <span class="reference" data-ref="diffbuff-interspeech"></span><span class="reference" data-ref="diffbuff-journal"></span> (d=9): <br>
 <audio id="audioPlayer0_diffusion_buffer_d_9" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
DEMUCS <span class="reference" data-ref="demucs"></span>: <br>
 <audio id="audioPlayer0_demucs" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
DeepFilterNet3 <span class="reference" data-ref="deepfilternet3"></span>: <br>
 <audio id="audioPlayer0_deepfilternet3" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
HiFi-Stream <span class="reference" data-ref="hifistream"></span>: <br>
 <audio id="audioPlayer0_hifi_stream" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
aTENNuate <span class="reference" data-ref="attenuate"></span>: <br>
 <audio id="audioPlayer0_atennuate" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
FM <span class="reference" data-ref="streamfm"></span> (4xEuler): <br>
 <audio id="audioPlayer0_fm_4xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br>
</p>

<script>
    let variants0 = ["clean","noisy","stream_fm_4xeuler","diffusion_buffer_d_0","diffusion_buffer_d_9","demucs","deepfilternet3","hifi_stream","atennuate","fm_4xeuler"];
    function playAudio0() {
        let selectedAudio = document.getElementById("audioSelect0").value;
        if(selectedAudio) {
            variants0.forEach((variant) => {
                let audioPlayer = document.getElementById("audioPlayer0_" + variant);
                let audioSource = audioPlayer.getElementsByTagName('source')[0];
                audioSource.src = "assets/audios/0_" + selectedAudio + "_" + variant + ".wav";
                audioPlayer.load();
            })
        }
    }
    playAudio0();
</script>
        

<h2>Dereverberation</h2>
<p>Select an audio file: &nbsp;&nbsp; <br class="smallmobile-only">
    <select id="audioSelect1" onchange="playAudio1()">
        <option value="p102_84" selected>p102_84</option>
            <option value="p102_382">p102_382</option>
            <option value="p103_731">p103_731</option>
            <option value="p103_299">p103_299</option>
            <option value="p104_302">p104_302</option>
            <option value="p104_825">p104_825</option>
            <option value="p105_784">p105_784</option>
            <option value="p105_353">p105_353</option>
            <option value="p106_843">p106_843</option>
            <option value="p106_813">p106_813</option>
            <option value="p107_800">p107_800</option>
            <option value="p107_216">p107_216</option>
    </select>
</p>

<p class="black">
Clean: <br>
 <audio id="audioPlayer1_clean" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Reverberant: <br>
 <audio id="audioPlayer1_reverberant" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer1_stream_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (LRK5): <br>
 <audio id="audioPlayer1_stream_fm_lrk5" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer1_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br>
</p>

<script>
    let variants1 = ["clean","reverberant","stream_fm_5xeuler","stream_fm_lrk5","fm_5xeuler"];
    function playAudio1() {
        let selectedAudio = document.getElementById("audioSelect1").value;
        if(selectedAudio) {
            variants1.forEach((variant) => {
                let audioPlayer = document.getElementById("audioPlayer1_" + variant);
                let audioSource = audioPlayer.getElementsByTagName('source')[0];
                audioSource.src = "assets/audios/1_" + selectedAudio + "_" + variant + ".wav";
                audioPlayer.load();
            })
        }
    }
    playAudio1();
</script>
        

<h2>Codec Postfiltering (Lyra V2)</h2>
<p>Select an audio file: &nbsp;&nbsp; <br class="smallmobile-only">
    <select id="audioSelect2" onchange="playAudio2()">
        <option value="p102_84" selected>p102_84</option>
            <option value="p102_382">p102_382</option>
            <option value="p103_731">p103_731</option>
            <option value="p103_299">p103_299</option>
            <option value="p104_302">p104_302</option>
            <option value="p104_825">p104_825</option>
            <option value="p105_784">p105_784</option>
            <option value="p105_353">p105_353</option>
            <option value="p106_843">p106_843</option>
            <option value="p106_813">p106_813</option>
            <option value="p107_800">p107_800</option>
            <option value="p107_216">p107_216</option>
    </select>
</p>

<p class="black">
Clean: <br>
 <audio id="audioPlayer2_clean" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Lyra V2 Decoder: <br>
 <audio id="audioPlayer2_lyra_v2_decoder" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer2_stream_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (LRK5): <br>
 <audio id="audioPlayer2_stream_fm_lrk5" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer2_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br>
</p>

<script>
    let variants2 = ["clean","lyra_v2_decoder","stream_fm_5xeuler","stream_fm_lrk5","fm_5xeuler"];
    function playAudio2() {
        let selectedAudio = document.getElementById("audioSelect2").value;
        if(selectedAudio) {
            variants2.forEach((variant) => {
                let audioPlayer = document.getElementById("audioPlayer2_" + variant);
                let audioSource = audioPlayer.getElementsByTagName('source')[0];
                audioSource.src = "assets/audios/2_" + selectedAudio + "_" + variant + ".wav";
                audioPlayer.load();
            })
        }
    }
    playAudio2();
</script>
        

<h2>Bandwidth Extension</h2>
<p>Select an audio file: &nbsp;&nbsp; <br class="smallmobile-only">
    <select id="audioSelect3" onchange="playAudio3()">
        <option value="p102_84" selected>p102_84</option>
            <option value="p102_382">p102_382</option>
            <option value="p103_731">p103_731</option>
            <option value="p103_299">p103_299</option>
            <option value="p104_302">p104_302</option>
            <option value="p104_825">p104_825</option>
            <option value="p105_784">p105_784</option>
            <option value="p105_353">p105_353</option>
            <option value="p106_843">p106_843</option>
            <option value="p106_813">p106_813</option>
            <option value="p107_800">p107_800</option>
            <option value="p107_216">p107_216</option>
    </select>
</p>

<p class="black">
Clean: <br>
 <audio id="audioPlayer3_clean" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Downsampled: <br>
 <audio id="audioPlayer3_downsampled" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer3_stream_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (LRK5): <br>
 <audio id="audioPlayer3_stream_fm_lrk5" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer3_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br>
</p>

<script>
    let variants3 = ["clean","downsampled","stream_fm_5xeuler","stream_fm_lrk5","fm_5xeuler"];
    function playAudio3() {
        let selectedAudio = document.getElementById("audioSelect3").value;
        if(selectedAudio) {
            variants3.forEach((variant) => {
                let audioPlayer = document.getElementById("audioPlayer3_" + variant);
                let audioSource = audioPlayer.getElementsByTagName('source')[0];
                audioSource.src = "assets/audios/3_" + selectedAudio + "_" + variant + ".wav";
                audioPlayer.load();
            })
        }
    }
    playAudio3();
</script>
        

<h2>STFT Phase Retrieval</h2>
<p>Select an audio file: &nbsp;&nbsp; <br class="smallmobile-only">
    <select id="audioSelect4" onchange="playAudio4()">
        <option value="p102_84" selected>p102_84</option>
            <option value="p102_382">p102_382</option>
            <option value="p103_731">p103_731</option>
            <option value="p103_299">p103_299</option>
            <option value="p104_302">p104_302</option>
            <option value="p104_825">p104_825</option>
            <option value="p105_784">p105_784</option>
            <option value="p105_353">p105_353</option>
            <option value="p106_843">p106_843</option>
            <option value="p106_813">p106_813</option>
            <option value="p107_800">p107_800</option>
            <option value="p107_216">p107_216</option>
    </select>
</p>

<p class="black">
Clean: <br>
 <audio id="audioPlayer4_clean" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Zero-phase: <br>
 <audio id="audioPlayer4_zero_phase" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer4_stream_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (LRK5): <br>
 <audio id="audioPlayer4_stream_fm_lrk5" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer4_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
RTISI-DM <span class="reference" data-ref="rtisi-ng"></span>: <br>
 <audio id="audioPlayer4_rtisi_dm" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br>
</p>

<script>
    let variants4 = ["clean","zero_phase","stream_fm_5xeuler","stream_fm_lrk5","fm_5xeuler","rtisi_dm"];
    function playAudio4() {
        let selectedAudio = document.getElementById("audioSelect4").value;
        if(selectedAudio) {
            variants4.forEach((variant) => {
                let audioPlayer = document.getElementById("audioPlayer4_" + variant);
                let audioSource = audioPlayer.getElementsByTagName('source')[0];
                audioSource.src = "assets/audios/4_" + selectedAudio + "_" + variant + ".wav";
                audioPlayer.load();
            })
        }
    }
    playAudio4();
</script>
        

<h2>Mel Vocoding</h2>
<p>Select an audio file: &nbsp;&nbsp; <br class="smallmobile-only">
    <select id="audioSelect5" onchange="playAudio5()">
        <option value="p102_84" selected>p102_84</option>
            <option value="p102_382">p102_382</option>
            <option value="p103_731">p103_731</option>
            <option value="p103_299">p103_299</option>
            <option value="p104_302">p104_302</option>
            <option value="p104_825">p104_825</option>
            <option value="p105_784">p105_784</option>
            <option value="p105_353">p105_353</option>
            <option value="p106_843">p106_843</option>
            <option value="p106_813">p106_813</option>
            <option value="p107_800">p107_800</option>
            <option value="p107_216">p107_216</option>
    </select>
</p>

<p class="black">
Clean: <br>
 <audio id="audioPlayer5_clean" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Pseudoinverse + Zero-phase: <br>
 <audio id="audioPlayer5_pseudoinverse_zero_phase" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer5_stream_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
Stream.FM <span class="reference" data-ref="streamfm"></span> (LRK5): <br>
 <audio id="audioPlayer5_stream_fm_lrk5" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
FM <span class="reference" data-ref="streamfm"></span> (5xEuler): <br>
 <audio id="audioPlayer5_fm_5xeuler" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br> 
HiFi-GAN <span class="reference" data-ref="hifi-gan"></span> <span class="reference" data-ref="speechbrain"></span> (16 kHz): <br>
 <audio id="audioPlayer5_hifi_gan_16_khz" controls>
     <source src="" type="audio/wav">
     Your browser does not support the audio element.
 </audio><br>
</p>

<script>
    let variants5 = ["clean","pseudoinverse_zero_phase","stream_fm_5xeuler","stream_fm_lrk5","fm_5xeuler","hifi_gan_16_khz"];
    function playAudio5() {
        let selectedAudio = document.getElementById("audioSelect5").value;
        if(selectedAudio) {
            variants5.forEach((variant) => {
                let audioPlayer = document.getElementById("audioPlayer5_" + variant);
                let audioSource = audioPlayer.getElementsByTagName('source')[0];
                audioSource.src = "assets/audios/5_" + selectedAudio + "_" + variant + ".wav";
                audioPlayer.load();
            })
        }
    }
    playAudio5();
</script>

<h2 id="citation">
    Citation
</h2>

<p>
    If you use our models, methods, or any derivatives thereof, please cite our
    <a href="#todo" target="_blank">research paper</a>:
</p>

<div class="container">
    <div class="inner-container" dir="auto" data-snippet-clipboard-copy-content="{% raw %}@article{
    welker2025streamfm,
    title={Real-Time Streamable Generative Speech Restoration with Flow Matching},
    author={Simon Welker and Bunlong Lay and Maris Hillemann and Tal Peer and Timo Gerkmann},
    year={2025},
    journal={Preprint},
}{% endraw %}">
<pre><code>{% raw %}@article{
    welker2025streamfm,
    title={Real-Time Streamable Generative Speech Restoration with Flow Matching},
    author={Simon Welker and Bunlong Lay and Maris Hillemann and Tal Peer and Timo Gerkmann},
    year={2025},
    journal={Preprint},
} {% endraw %}</code></pre>
    </div>
    <button id="copyButton" class="highlight">
        <svg xmlns="http://www.w3.org/2000/svg" height="16" viewBox="0 0 16 16" width="16" class="octicon octicon-clippy">
            <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path>
            <path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path>
        </svg>
    </button>
</div>

<script>
    document.getElementById('copyButton').addEventListener('click', function() {
        const codeContent = document.querySelector('div[data-snippet-clipboard-copy-content]').getAttribute('data-snippet-clipboard-copy-content');
        navigator.clipboard.writeText(codeContent).then(function() {
        }, function() {
            alert('Failed to copy!');
        });
    });
</script>

<br>

<h2>
    References
</h2>

<ol id="refList" style="list-style-type: none; padding: 0;">
    <!-- JavaScript will populate this list -->
</ol>

<script>
    document.addEventListener("DOMContentLoaded", function () {
        const references = {
            "streamfm": "S. Welker, B. Lay, M. Hillemann, T. Peer, and T. Gerkmann, “Real-Time Streamable Generative Speech Restoration with Flow Matching,“, preprint, 2025.",
            "flowdec": "S. Welker, M. Le, R. T. Q. Chen, W.-N. Hsu, and T. Gerkmann, A. Richard, Y.-C. Wu, “FlowDec: A flow-based full-band general audio codec with high perceptual quality,” in The Thirteenth International Conference on Learning Representations (ICLR), 2025.",
            "diffbuff-interspeech": "B. Lay, R. Makarov, and T. Gerkmann, “Diffusion buffer: Online diffusion-based speech enhancement with sub-second latency,” Interspeech, 2025.",
            "diffbuff-journal": "B. Lay, R. Makarov, S. Welker, M. Hillemann, and T. Gerkmann, “Diffusion buffer for online generative speech enhancement,” arXiv preprint arXiv:2510.18744, 2025.",
            "rtisi-ng": "T. Peer, S. Welker, J. Kolhoff, and T. Gerkmann, “A flexible online framework for projection-based STFT phase retrieval,” in IEEE Int. Conf. on Acoustics, Speech and Signal Proc. (ICASSP). IEEE, 2024.",
            "hifi-gan": "J. Kong, J. Kim, and J. Bae, “HiFi-GAN: Generative adversarial networks for efficient and high fidelity speech synthesis,” Advances in Neural Inf. Proc. Systems (NeurIPS), 2020.",
            "speechbrain": "M. Ravanelli, T. Parcollet, A. Moumen, S. de Langen, C. Subakan, P. Plantinga, Y. Wang, P. Mousavi, L. D. Libera, A. Ploujnikov et al., “Open-source conversational AI with SpeechBrain 1.0,” J. of Machine Learning Research, vol. 25, no. 333, 2024.",
            "demucs": "A. Défossez, G. Synnaeve, and Y. Adi, “Real time speech enhancement in the waveform domain,” in Interspeech, 2020.",
            "deepfilternet3": "H. Schröoter, T. Rosenkranz, A. N. Escalante-B., and A. Maier, “DeepFilterNet: Perceptually motivated real-time speech enhancement,” in Interspeech, 2023.",
            "hifistream": "E. Dmitrieva and M. Kaledin, “HiFi-Stream: Streaming speech enhancement with generative adversarial networks,” IEEE Signal Proc. Lett. (SPL), vol. 32, pp. 3595–3599, 2025.",
            "attenuate": "Y. R. Pei, R. Shrivastava, and F. Sidharth, “Optimized Real-time Speech Enhancement with Deep SSMs on Raw Audio,” in Interspeech, 2025.",
        };

        // Collect keys in order of their appearance, without duplication
        const referenceElements = document.querySelectorAll('.reference');
        const orderedKeys = [];
        referenceElements.forEach(element => {
            // Split the keys and iterate over them
            const keys = element.dataset.ref.split(' ');
            keys.forEach(key => {
                // Add key if it's not already in the list to maintain first appearance order
                if (!orderedKeys.includes(key) && references[key]) {
                    orderedKeys.push(key);
                }
            });
        });
        let sortedReferences = {};
        // Populate the sorted references object based on orderedKeys
        orderedKeys.forEach(key => {
            if (references[key]) {
                sortedReferences[key] = references[key];
            }
        });

        function changeId(element) {
            // Change the id of the clicked element to the next one
            key = element.id.split('-')[1];
            elem = document.getElementById(`link-${key}`);
            elem.href = `#${element.id}`;
        }

        const refList = document.getElementById('refList');
        const refTotal = Object.keys(sortedReferences).length;
        const maxWidth = `${Math.ceil(Math.log10(refTotal + 1)) * 10 + 5}px`;

        Object.entries(sortedReferences).forEach(([key, ref], index) => {
            const refNumber = index + 1;
            const li = document.createElement('li');
            li.id = `ref-${refNumber}`;
            li.style.display = 'flex';
            li.style.alignItems = 'baseline';
            li.style.marginBottom = '5px';

            const numberSpan = document.createElement('span');
            numberSpan.style.fontWeight = 'regular';
            numberSpan.style.minWidth = maxWidth;
            numberSpan.style.textAlign = 'right';
            numberSpan.style.marginRight = '10px';
            numberSpan.style.whiteSpace = 'nowrap';

            const numberLink = document.createElement('a');
            numberLink.href = `#cite-${key}-0`;
            numberLink.id = `link-${key}`;
            numberLink.textContent = `[${refNumber}]`;
            numberLink.style.textDecoration = 'none';
            numberSpan.appendChild(numberLink);

            const textSpan = document.createElement('span');
            textSpan.textContent = ref;

            li.appendChild(numberSpan);
            li.appendChild(textSpan);
            refList.appendChild(li);
        });

        referenceCounter = {};
        // Making In-text references linkable and combine multiple references
        document.querySelectorAll('.reference').forEach(span => {
            const keys = span.getAttribute('data-ref').split(' ');
            const refNumbers = keys.map(key => {
                const index = Object.keys(sortedReferences).indexOf(key);
                return index + 1;
            });
            keys.forEach((key, i) => {
                if (referenceCounter[key] >= 0) {
                    referenceCounter[key]++;
                } else {
                    referenceCounter[key] = 0;
                }

                // Set up string if there are multiple references
                if (keys.length > 1) {
                    if (i === 0) {
                        refText = `[${refNumbers[i]}, `;
                    } else if (i === keys.length - 1) {
                        refText = `${refNumbers[i]}]`;
                    } else {
                        refText = `${refNumbers[i]}, `;
                    }
                // Set up string if there is only one reference
                } else {
                    refText = `[${refNumbers[i]}]`;
                }

                const citeId = `cite-${key}-${referenceCounter[key]}`;
                const citeLink = document.createElement('a');
                citeLink.href = `#ref-${refNumbers[i]}`;
                citeLink.textContent = refText;
                citeLink.id = citeId;
                citeLink.style.textDecoration = 'none';
                citeLink.addEventListener('click', function () {
                    changeId(this);
                });

                span.appendChild(citeLink);
            });
        });

    });
</script>