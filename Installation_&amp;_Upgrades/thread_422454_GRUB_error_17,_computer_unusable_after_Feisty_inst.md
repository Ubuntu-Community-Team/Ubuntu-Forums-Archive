---
title: "GRUB error 17, computer unusable after Feisty installed"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Grrblt on 2007-04-25
Yesterday I figured I might have a go at Linux. I kept winxp at C: and installed the 7.04 Ubuntu on what used to be my E:
The installer said everything installed fine, but when I'm booting up my computer I'm greeted by the follow text:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

And then nothing more happens. I can still use the Live CD but can't access internet from there for some reason (might have written down wrong static IP infos). Reinstalling Ubuntu at the same drive didn't improve anything.

My motherboard is an A8N-SLI if that makes a difference.

:(

---

### Post by ssican on 2007-04-25
IF you have the Windows CD INSTALLATION you can repair the boot to windows XP. You can to use the method FIX MBR. See this Link: [http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)
Usually E is the UNIT of  CD-ROM/RW DRIVE 
For a Tutorial about INSTALL Ubuntu, see this link: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by corstar on 2007-04-25
I had a grub error a while ago. The solution was to change the jumper settings. I had it set to slave.

---

### Post by Grrblt on 2007-04-25
My D and E drives were both SATA hard drives, ie no CDROM and no master/slave jumpers. I will try the XP cd thing.

---

### Post by ssican on 2007-04-25
FOR TWO DRIVES, DUAL BOOT, see this forums:
Forum -Dual Boot Two Hard Drives- [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Forum -Dual Boot on Two Drives- [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

