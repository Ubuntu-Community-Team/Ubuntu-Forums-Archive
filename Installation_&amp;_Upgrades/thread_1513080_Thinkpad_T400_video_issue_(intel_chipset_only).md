---
title: "Thinkpad T400 video issue (intel chipset only)"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by rafael_a on 2010-06-18
Hello. I have a TP T400 and wanted to use a bit of Linux. Installed Ubuntu 10.04 in my notebook using Virtualbox. The problem is that it doesn't recognizes the video chipset, which is a X4500 integrated graphics. After booting I receive an error msg saying that my video is not recognized and asks if I want to fix it. Dunno how to do that, so I cancel. After that I can only use 800x600, wanted widescreen (1440x900). Is there a simple way to fix it? Liked Ubuntu, wanted to use it.
Thanks in advance.

---

### Post by dino99 on 2010-06-19
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by rafael_a on 2010-06-19
Hello dino99. Thanks for the answer, but that has nothing to do with my problem. The problem is about the video resolution (Intel video chipset not being detected), and not about the instalation process.

---

### Post by rafael_a on 2010-06-24
well, gonna try Red Hat or Debian then...

---

### Post by dino99 on 2010-06-24
maybe a way with this, add into synaptic repo:

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by rafael_a on 2012-03-29
Hello,
forgot to post the solution I used.
I used xrandr app. You can add custom resolutions to the system using it. I followed the instructions in here:
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting%20an%20out-of-range%20resolution)

---

