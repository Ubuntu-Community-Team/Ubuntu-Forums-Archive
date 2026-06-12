---
title: "Problem installing Nvidia drivers on 840m (14.04)"
date: 2014-09-29
forum: Installation &amp; Upgrades
---

### Post by robbiej2 on 2014-09-29
Hey folks. Just got an MSI GP70 2PE Laptop. The laptop has an Nvidia 840m and I need to utilize the GPU for my work. I've tried following the instructions posted [here]("http://ubuntuhandbook.org/index.php/2014/06/nvidia-driver-337-25/"), but when I get to the login screen there is a crash report prompt and I am unable to do anything else (I can CTRL+ALT+F1 and get a working terminal, but that's it). I've also tried skipping over the install of nvidia331-updates-dev and just using the .run file downloaded from Nvidia, but that causes the same issue. Any ideas on what could be happening?

Note that a fresh install of Ubuntu works fine. However, when I do boot into that, just before the login screen appears I see a two line message starting something about 'nouveau unknown chipset'.

Thanks in advance for any help!

---

### Post by ajgreeny on 2014-09-29
Have you tried installing one of the drivers that are available from "Additional drivers" in the dash?  I could not figure out from your post if you had or not.

That is always the first thing to try, not going straight to the nvidia website, which may have newer drivers, but they may not be as compatible with the rest of your OS.

---

### Post by robbiej2 on 2014-09-29
Forgot to mention that the "Additional Drivers" dialog doesn't show any options to select.

---

