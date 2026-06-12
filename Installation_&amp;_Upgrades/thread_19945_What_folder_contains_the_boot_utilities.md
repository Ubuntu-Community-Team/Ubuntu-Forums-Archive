---
title: "What folder contains the boot utilities?"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by joplass on 2005-03-14
I want to put the boot utilities on floppy but I don’t seem to find it on the disk.  Warty please.  I am on a windows machine.  I am trying to start an installation from floppy on some old machine.
Thanks

---

### Post by sas on 2005-03-14
I don't think it's as simple as that, but I believe all boot stuff is in /boot

[http://sourceforge.net/projects/btmgr](http://sourceforge.net/projects/btmgr) may be a better solution for your problem though. It allows you to boot from floppy then cd.

---

### Post by joplass on 2005-03-14
Thanks man but it did not work.  I tried using the rawwrite command no can't do.  Anybody else please???

This is the message I get:
NTLDR is missing
Press any key to restart.

I have been using this for years but it does not work with Ubuntu:
C:\> d:
D:\> cd \dosutils
D:\dosutils> rawrite
Enter disk image source file name:..\images\bootdisk.img
Enter target diskette drive: a:
Please insert a formatted diskette into drive A: and 
press --ENTER-- :[Enter]
D:\dosutils>

---

### Post by sas on 2005-03-14
[QUOTE=joplass]Thanks man but it did not work.  I tried using the rawwrite command no can't do.  Anybody else please???

This is the message I get:
NTLDR is missing
Press any key to restart.

I have been using this for years but it does not work with Ubuntu:
C:\> d:
D:\> cd \dosutils
D:\dosutils> rawrite
Enter disk image source file name:..\images\bootdisk.img
Enter target diskette drive: a:
Please insert a formatted diskette into drive A: and 
press --ENTER-- :[Enter]
D:\dosutils>[/QUOTE]
 That means it's trying to load windows xp/nt for some reason and not the cd.

Dunno why though, sorry.

---

