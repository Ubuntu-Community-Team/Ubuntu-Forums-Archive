---
title: "installation freezes"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by alemkra on 2010-07-18
Hi forum,

I used to run Ubuntu on my old IBM Thinkpad R50e without any problems. Since I needed it for some other taskes I got rid of Ubuntu a while ago and wanted to reinstall it today. Since it worked fine 6 months ago I was a bit astonished to find out that not even the live CD will boot up with the current version. It doesn't matter if I choose to install or try the live version, it just freezes after the Ubuntu screen with the dots. I have a black screen and the computer doesn't do anything until I switch it off. Any ideas?

Alemkra

---

### Post by davidmohammed on 2010-07-18
its probably a graphics issue - depending on what the graphics card - can I suggest you try pressing F6 from the live CD.  At the bottom of the screen is your boot string - add one of the following immediately before "quiet splash --"

nomodeset
i915.modeset=1
i915.modeset=0

then select the option "try without installing".

---

### Post by alemkra on 2010-07-19
Thank you! "i915.modeset=1" worked for me.
I guess I'll wait for a new bugfixed version of Ubuntu anyway because I read that there are several graphics issues, crashes etc when using this workaround.

---

### Post by davidmohammed on 2010-07-19
if you've got a i845 or i855GM graphics then there is already a fix - what card have you got?

lspci | grep VGA

---

### Post by alemkra on 2010-07-19
It's an Intel 82852/82855 Graphics Controller

---

### Post by davidmohammed on 2010-07-19
[this]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511") is the intel bug we are suffering from...

the fix is in the description of the bug.

---

### Post by alemkra on 2010-07-19
Thank you! I'll try the installation later on :D

---

