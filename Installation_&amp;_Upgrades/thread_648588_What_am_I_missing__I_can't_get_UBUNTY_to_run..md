---
title: "What am I missing?  I can't get UBUNTY to run."
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by fredjara on 2007-12-23
I downloaded both the 7.0 and the 6.0 and tried both on my laptop.  Neither work.  Am I missing something here?  When I click on my CD drive I get an icon my computer doesn't recognize and the following under the icon:  ubuntu-6.06.1-desktop-i386.iso

Is there anything else I need to download?  If not, what do I need to do to get it up and running?

Thanks.
Fred

---

### Post by Stemp on 2007-12-23
Hi fredjara;

You have to «burn» a cd with this iso file.

See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Pumalite on 2007-12-23
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by fredjara on 2007-12-23
Thanks.  I did burn a cd with the iso file.  I am working off a cd.  I placed the cd in, and windows boots up normally...no ubuntu.

---

### Post by oldsoundguy on 2007-12-23
you have to burn the ISO as an "image" file and the burning program that comes with WinBLOWS is Roxio and really isn't that helpful.

---

### Post by oldos2er on 2007-12-23
I don't understand--you say you're "working off" a cd, then you say no ubuntu. As was said, you burn the iso file as an image to a cd, reboot, go into your BIOS and tell it to boot from cd, restart. Once the Ubuntu cd boots, choose to check the cd for defects just to be sure.

---

### Post by fredjara on 2007-12-24
I burned about three different cd's and none of them worked until I re-read the "burning cd" instructions.  I wasn't getting the "tree" but now that I downloaded all the proper burning and reading programs, and re-burned the CD, it worked fine on my laptop.  Next thing I want to do is actually replace XP with UBUNTU and boot directly from UBUNTU.  Is that do-able?

---

### Post by Pumalite on 2007-12-24
Is Grub installed to sda? Can you see Grub when you boot?

---

### Post by fredjara on 2007-12-24
Yes, I see GRUB when I boot.  All's good.  I just want to replace Windows XP with UBUNTU.  I'm working with my ancient laptop (about five years old) running amd athalon and maxed out at 368 RAM.

---

### Post by Pumalite on 2007-12-24
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, erase XP partition. Then reinstall Grub with this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You can then reboot Gparted and resize your Ubuntu partition.
Backup everything before you involve yourself with this operations.

---

