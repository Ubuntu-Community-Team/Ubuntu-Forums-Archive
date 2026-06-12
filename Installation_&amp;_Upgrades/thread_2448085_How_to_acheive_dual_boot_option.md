---
title: "How to acheive dual boot option"
date: 2020-08-01
forum: Installation &amp; Upgrades
---

### Post by fen26boy on 2020-08-01
H i guys,
 Hope this wont sound too silly a question.
 A couple of years back I bought a reconditioned Dell laptop with a small (by today’s standards) HD with Windows 10 installed. I had not use for Win 10 at the time to swapped the the HD for a much bigger SSD on which I installed Xubuntu 18 LTS.
 I’ve since acquired a drive caddy which allows a second hard drive to be fitted in the slot normally occupied by the optical CD/DVD drive.
 
 
 Now for the question:
 If I put the original HD with Win 10 on into the caddy and run restore or reinstall GRUB would GRUB pick up the unused Windows on the second drive and offer it as a booting option in it’s start up menu?  If this is a way to give me a dual boot option can someone please tell me what commands to type in the terminal to achieve this?

---

### Post by crip720 on 2020-08-01
As long as everything goes good should only need to boot Xubuntu and do sudo update-grub(hopefully UEFI works same as Legacy for this).  Would wait a bit and see if better people have better ideas.

---

### Post by fen26boy on 2020-08-01
Thanks. Pretty much what I suspected. But,as you say, probably best to wait for further advice.

---

### Post by ubfan1 on 2020-08-01
Things to check: Was Windows shut down properly (vs the fast-start/hibernate option)? Was Windows installed in the same mode (UEFI vs legacy) as Ubuntu?  New machines have Windows in UEFI mode, but a machine which was updated from Win7,  may be in legacy mode.  Check the disk partitioning type (Windows requires gpt for UEFI) and the partitions (UEFI mode has a EFI partition).  Grub itself may have problems with the caddy -- on an old HP, grub would hang trying to access disk caddy, but would work fine if booted off another device, and then could boot a root in the caddy.

---

### Post by pbear42 on 2020-08-01
Further to ubfan1's point, there were many Win7 machines sold in its last year which were UEFI-in-CSM mode, so Windows was installed in legacy mode but the firmware preferentially boots in UEFI if supported by the boot medium.  So, it wouldn't have been obvious at installation of Xubuntu if you were using a different boot mode.  Which isn't to say it happened.  Only that you should check.

---

### Post by fen26boy on 2020-08-04
Thanks chaps. The big problem is: I don't know how to check for the things you warn I should look out for.

---

### Post by pbear42 on 2020-08-04
Easiest way to tell is to check for EFI partitions.  This is relatively small, usually 200 to 500 MB, usually first or second on the disk.  Most conspicuously, will be formatted fat32 (also called vfat in some Linux utilities) and have boot/esp flags.  Check both disks.  Doesn't matter which they are, but you want them to be the same.

---

