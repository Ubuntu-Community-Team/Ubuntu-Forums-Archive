---
title: "Fresh install error: The display server has been shut down about 6 times..."
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by crashMMVII on 2008-01-02
Hey all,

I have absolutely no previous experience with any form of Linux. After reading some guides about it, I decided to try and install Ubuntu 7.10 on my HDD so I can dual-boot it with Vista. I have the CD burned, created an unallocated space on my HDD, but after I boot from it and click on "start or install Ubuntu" (or something along those lines), it goes through what appears to be some loading screens, eventually giving me an error saying:

> The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.

It then goes to some kind of  basic input screen, and after 2 minutes, it does it all again. Various google searches, as well as one on these boards, have failed to return any kind of info to help me fix the problem. Does anyone have any ideas on what to try?

Thanks for your time!
crashMMVII

---

### Post by crashMMVII on 2008-01-03
Okay, I managed to get it "installed" via the Alternate CD, but when I choose to boot into Ubuntu through GRUB, I get the same problem.

I would really appreciate any help I can get. Thanks!

---

### Post by UnresponsiveBeeVictim on 2008-01-04
Do you have an ATi videocard?

---

### Post by ArmoredCavalry on 2008-01-08
I'm having the same problem.... 7.04 worked alright, but then I noticed that 7.10 was out, so I figured I would do a fresh install. Now I get the error mentioned above, with an ATI 3850 gpu.

---

### Post by Macyoshary on 2008-01-23
Same here on a Core 2 duo iMac with an ATI Radeon X1600 graphics card. If I try the Feisty cd in complains about x.

---

### Post by absoluteborg on 2008-02-08
I have this same problem. Tried to install the 'normal' ubuntu desktop CD. I'm trying to install on a Biostar P4M80-M4 Motherboard, which has an integrated VIA S3 UniChrome Graphics adapter. I tried both in normal and safe graphics mode, w/ the same result.

I also tried installing Fedora on the same machine, and I had the same issue. I installed Debian on the machine (using the text installer), and the thing worked w/ no problems.

After some searching, it looks like it's a video driver issue (duh?!). For whatever reason, the default video driver (in VESA mode?) doesn't seem to like some video chipsets. 

For install, I read somewhere to try the 'alternate CD', which includes a non-graphical installer. I'm downloading that, and trying that now.

For systems already installed, I would guess that you need to install AND/OR configure the video driver, to get one that works with your chipset. From what I've read ATI chipsets are the least Linux friendly, VIA is so so (depends on the chipset?), and NVidia is the best.

If I can't get this to work with the onboard graphics, I'm gonna buy a lower end Nvidia Graphics card, and try it with that. When/if I get this to work, I'll post what I did.

---

### Post by absoluteborg on 2008-02-12
Ok, so I fixed this problem on my computer. Here's my understanding of the problem:

The 'display server' is trying to use a video setting (resolution/color depth/refreshrate) that is not compatible with either your video card, or with the particular driver found for your video card. When the Installer attempts to auto-detect your video card, it apparently does not find the right one.

When installing: Use the Alternative CD. This gives you a text installer.

After installation: When the machine begins to load, the screen will start to flicker. Press Ctrl + Alt + F5, (in between monitor flickering), and login. You need to edit the file /etc/x11/xorg.conf. You can use VI to do this in the console. OR, what I did, is use the dpkg configure. At a command prompt, type: "sudo dpkg-reconfigure xserver-xorg" This will walk you through the xserver-xorg setup. Choose appropriate settings for your video card. When this process is done, the dpkg will change your xorg.conf file. Now, when X attempts to load, it should find compatible resolutions for the video driver, and it should load up fine.

---

