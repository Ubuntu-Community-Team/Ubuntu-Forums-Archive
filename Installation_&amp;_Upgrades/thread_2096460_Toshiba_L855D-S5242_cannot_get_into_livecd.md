---
title: "Toshiba L855D-S5242 cannot get into livecd"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by mxdg406 on 2012-12-20
Hello Everyone,
I have tried to install 12.04 and 12.10 on my laptop which has an A8 4500m apu with 6 gigs of ram. Whenever I have tried to install it locks up during the Ubuntu loading screen. I just recently tried to install with wubi and none of the different launch options seems to help at all.  Any Help would be greatly appreciated!!!
Thank You,
Derek

---

### Post by slayt12 on 2012-12-20
Are you at the point where you've selected any options? Or is this the screen where the logo is starting to fill in?

Is your CD/DVD rom drive doing anything?
Is your hard drive light on or does it sound like its working?

Have you used the disk on a different computer? It could be a bad disk or the download could be corrupt.

---

### Post by mxdg406 on 2012-12-20
the most recent install was using wubi but yes on previous tries the disk was tested.  I'm at the purple screen with ubuntu and the dots filling in after a certain amount of time the dots just stop and its frozen.
Thank You,
Derek

---

### Post by mxdg406 on 2012-12-20
bump, anybody have any idea? I'd really love to get back onto ubuntu.

---

### Post by oldfred on 2012-12-21
Sounds like a video issue. I have nVidia so I so not know AMD/ATI. But it also could be other boot parameter is required. Sometimes removing quiet splash lets you see what is loading or what is not working.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by mxdg406 on 2013-01-08
Thank you, I'll give that a try tomorrow. Also just updated my bios to the latest version.

---

