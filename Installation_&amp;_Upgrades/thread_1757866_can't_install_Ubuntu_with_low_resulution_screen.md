---
title: "can't install Ubuntu with low resulution screen"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by gdglenn on 2011-05-13
I have Ubuntu 8.10 running on an old Diamond Flower K6BV3+, but it was slower than I would like.  I tried to install 8.10 on a later H-P Pavilion 524w for more speed, but it won't install, because the screen resolution is too coarse.  I expect it is about 320x200.  I can not get at the necessary buttons to click for installation because they are off the bottom of the screen.

The download I used is "Ubuntu-8.10-desktop-i386.iso".  Should this work?

I tried loading other distros, including openSUSE 11.4 and Wary Puppy 5.1.1, but I get the same problem with off-the-screen buttons.

Can I do something to get the resolution up to 800x600 or better for installation.

Thank you,
D. Glenn

---

### Post by MAFoElffen on 2011-05-14
> **gdglenn said:**
> I have Ubuntu 8.10 running on an old Diamond Flower K6BV3+, but it was slower than I would like.  I tried to install 8.10 on a later H-P Pavilion 524w for more speed, but it won't install, because the screen resolution is too coarse.  I expect it is about 320x200.  I can not get at the necessary buttons to click for installation because they are off the bottom of the screen.

The download I used is "Ubuntu-8.10-desktop-i386.iso".  Should this work?

I tried loading other distros, including openSUSE 11.4 and Wary Puppy 5.1.1, but I get the same problem with off-the-screen buttons.

Can I do something to get the resolution up to 800x600 or better for installation.

Thank you,
D. Glenn
Is there any way you can boot in grub, drop down to the Grub Command line Interface and run 
```

vbeinfo
##  or  ##
vbeprobe

```I can't remeber what vsrsion it was that it switched from vbeprobe o vbeinfo...

Or boot into a linux text mode and run
```

hwinfo --framebuffer

```Either of those would return the Vesa modes that your card supports.  You might be able to use those to set a Vesa Graphics mode on boot.

One last question- What kernel and grub version it it installing?

---

### Post by wilee-nilee on 2011-05-14
> **gdglenn said:**
> I have Ubuntu 8.10 running on an old Diamond Flower K6BV3+, but it was slower than I would like.  I tried to install 8.10 on a later H-P Pavilion 524w for more speed, but it won't install, because the screen resolution is too coarse.  I expect it is about 320x200.  I can not get at the necessary buttons to click for installation because they are off the bottom of the screen.

The download I used is "Ubuntu-8.10-desktop-i386.iso".  Should this work?

I tried loading other distros, including openSUSE 11.4 and Wary Puppy 5.1.1, but I get the same problem with off-the-screen buttons.

Can I do something to get the resolution up to 800x600 or better for installation.

Thank you,
D. Glenn
8.10 is not supported any more end of life.

Download a alternative install of 10.04 the longterm release, the alternative is an no desktop during install of the regular OS.

---

