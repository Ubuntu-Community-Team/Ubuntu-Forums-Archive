---
title: "GRUB Stage1.5 Read error"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by Xanxer82 on 2007-12-12
I just installed Ubuntu 7.10 on an Emachines W2785. This previously had an XP installation. During Installastion of Ubuntu from the Live CD I chose to use the Entire Disk, as I wanted to completely get rid of windows and have a pure linux box. 
Installation went fine until it wanted to reboot ant remove the CD. I removed  the CD when promted and then it rebooted giving me a GRUB Stage1.5 Read error.
It will boot fine from the Live CD and sees the hard disk un the "Computer" menu. 
Now just to get it to boot up normally. 

Anyone have a solution?

---

### Post by torgrot on 2007-12-12
See this page for some help with that particular error.  Generally means you need to re-install grub.

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

torgrot

---

### Post by Xanxer82 on 2007-12-13
I took a look at that and ran supergrub. still get the same error. I'm unable to get to the grub menu at boot by hitting esc.

---

### Post by torgrot on 2007-12-13
Some people have had some luck going into the bios and checking that their hard drives are set to autodetect.  Since you can now boot off the Live CD why don't you follow this guide to reinstalling grub  [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

I have never had much luck with Super Grub.  You could also try GAG from a floppy which won't fix anything but may let you boot ubuntu.  You can get it from here [http://gag.sourceforge.net/](http://gag.sourceforge.net/)


torgrot

---

### Post by froy02 on 2007-12-13
Here's a very simple way to install grub with live CD.  Check this site:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Xanxer82 on 2007-12-23
I ended up removing the battery from the mobo and resetting the bios that way. Then I powered up and Ubuntu loaded correctly.

Thanks for the suggestions

---

