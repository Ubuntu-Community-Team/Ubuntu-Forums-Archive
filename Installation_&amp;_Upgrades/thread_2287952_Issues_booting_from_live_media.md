---
title: "Issues booting from live media"
date: 2015-07-23
forum: Installation &amp; Upgrades
---

### Post by whitshade on 2015-07-23
I recently opted for a fresh install as my installation of Xubuntu 14.02 had gotten slow.  I have been unable to run or install from Live DVDs with Xubuntu 14.02.  I have been able to run some Live DVDs with other distros and versions of Xubuntu.  They boot to the menu, then a flashing cursor in the upper left corner  of a blank screen.  This eventually just becomes a small red block like a  cursor near the top of the screen. I am currently running 12.02 which booted and installed without issue.  I replaced the DVD drive (IDE) with a new one (SATA) thinking that this was the issue.  It was not.  I still have the same problem when loading Xubuntu from DVD.   I went to Ubuntu's [BootFromCD]("https://help.ubuntu.com/community/BootFromCD") Web site and realized that I could press F6 at the boot menu to access other options.  Here, I turned off the splash screen and rebooted so I could see what was going on. The attached screenshot shows how far loading got before the system crashed (note the ominous red block near the upper left-hand corner)..  Any input is appreciated.

---

### Post by howefield on 2015-07-23
> **whitshade said:**
> [IMG]/home/chris/Media/2015/0715/screenshot072215.JPG[/IMG]

No one here is likely to be able to see your home folder, so use the paperclip icon (in the posting window) to add an image to your post.

---

### Post by whitshade on 2015-07-23
Good point.

---

### Post by oldfred on 2015-07-24
Systems that start to boot, but then some fail often are driver issue and most often video card driver issue.
What video card/chip?

If video related:
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

