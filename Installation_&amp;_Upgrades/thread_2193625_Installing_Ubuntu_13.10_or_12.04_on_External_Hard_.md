---
title: "Installing Ubuntu 13.10 or 12.04 on External Hard Drive"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by ThatNewGuy on 2013-12-13
I have read many post about this, I know there is a lot of post on here so don't kill me for asking here haha. I have a WD 750gig laptop HDD that I installed into a WD passport external I had laying around. I wanted to put Ubuntu 13.10 on it but no luck so I went with a version I read that worked 12.04 and no dice. I went post hunting and found this thread [http://ubuntuforums.org/showthread.php?t=2084736](http://ubuntuforums.org/showthread.php?t=2084736) and yet again no dice. I tried making the /boot,swap and /(root) method and just by itself / for root and wont work. Ubuntu installs fine but went I hit ESC and boot from WD External it black screen every time. Does anyone have any thoughts about this?

Thanks

---

### Post by oldfred on 2013-12-14
If you hold shift key if BIOS booting or escape if UEFI booting, do you get grub menu?

Often black screen is a video issue.
What video card/chip do you have?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

   [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by ThatNewGuy on 2013-12-14
AMD Radeon card

ill check out your links

---

