---
title: "Firefox + flash = high CPU usage"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SnowPunk98 on 2008-09-17
Running the most up to date Ibex and whenever I use Firefox and Adobe flash my CPU (Intel Core 2 Duo E7200) spikes to 50+% and when I close the page or firefox it drops to ~10%. I have tried multiple flash enabled sites and the same thing happens.

---

### Post by Nullack on 2008-09-18
Theres no GPU acceleration on flash if your running compiz

Also the flash revision in the repos is old

---

### Post by dizzogg on 2008-09-18
Yea, try removing flashplugin-nonfree and manually install the flash plugin from adobe's site.  Works for me.

---

### Post by dustman on 2008-09-18
> **dizzogg said:**
> Yea, try removing flashplugin-nonfree and manually install the flash plugin from adobe's site.  Works for me.

true, true.

too bad flash is not open-source...the community might get it working in no time!

---

### Post by yelo3 on 2008-09-18
Do you mean that using the flash version from adobe website, the cpu usage is finally low??????

---

### Post by dizzogg on 2008-09-18
Yes, installing the new RC from Adobe's site seems to bring down cpu usage and also seems to feel a little faster.

---

### Post by psyke83 on 2008-09-18
Just keep in mind that any manual installation of the flash plugin *will* cause problems later on (due to multiple version of the plugin in different folders). It's always better to use a packaged version.

There have been some prerequisite updates to Intrepid (ia32-libs, libflashsupport completely removed). Flash is next on the list, and should be updated soon.

P.S. Discussion of Flash is too fragmented, try to keep it in one place. The [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=866965") thread is the best place to keep updated, as Flash will be impacted.

---

### Post by SnowPunk98 on 2008-09-18
Yes, I am using Compiz and the one from the repo, not from Adobe, I hope this can be resolved before Ibex is released.

---

### Post by bogusx on 2008-09-24
> **dizzogg said:**
> Yes, installing the new RC from Adobe's site seems to bring down cpu usage and also seems to feel a little faster.

I have downloaded and manually installed the new Shockwave Flash plugin (10.0.r12) and nothing happens, i.e. cpu usage is extremly high still.
Which exactly version of the web browser and the plugin are you using?

PS: I even tried the pre-build Firefox 3.1.0 (because I read somewhere it's the browser's bug not the plugin itself), still with the same results so I am about to give up...

---

### Post by phenest on 2008-09-24
Personally, I'm using the swfdec-mozilla package. I'm on 64 bit and it works fine. I'm not using Compiz, but it might be worth trying.

---

