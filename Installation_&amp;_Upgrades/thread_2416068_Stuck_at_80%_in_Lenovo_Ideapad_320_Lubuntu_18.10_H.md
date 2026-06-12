---
title: "Stuck at 80% in Lenovo Ideapad 320 Lubuntu 18.10 HELP PLS"
date: 2019-04-04
forum: Installation &amp; Upgrades
---

### Post by s2art on 2019-04-04
Hi, so I'm new to this sort of stuff. I got this PC, but with W10 is incredible slow (CPU is 2 cores 1.10Ghz), so I decide to look for a more convenient OS
Lubuntu looks ideal, nice and fast.

I already disable secure boot, fast boot, and put it in legacy support, and I boot it from an USB, but in the installation it just got stucked at 80%, it just says (Starts procedure and passes 'fw_type' to other routine. I dont have a clue what´s wrong. Can please someone help me? Thanks

---

### Post by Dennis N on 2019-04-04
Windows 10 is most likely UEFI, so you should be installing Lubuntu 18.10 in UEFI mode as well. Mixing types of install on the same disk is not recommended. 

Lubuntu 18.10 uses a different installer than other Ubuntu types. I found the installer a bit buggy. When 18.10 first came out, in several attempts, I was never able to get the installer to finish a UEFI install without crashing or just stopping like yours did. I did a number of tries. But I was able to install in BIOS mode on an older BIOS machine. 

If you give up, I suggest you try Xubuntu 18.10 instead which uses the same installer as Ubuntu. 

But, since 18.10 support will be ending in a few months, a better choice could be Lubuntu 18.04, which uses the Ubuntu installer and has continuing support.

---

### Post by jtremblaymclellan on 2019-04-05
You could fix the problem by mounting your image via chroot and configuring the image to boot properly.

What did you do finally?

---

