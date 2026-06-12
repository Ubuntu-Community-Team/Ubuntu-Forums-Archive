---
title: "Grub Windows 7 Error"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by 6ejrpksjgj on 2013-11-16
Short Question:

Trying to dual boot Ubuntu 12.04 and Windows 7 Pro on a brand new Acer Travelmate. If I fiddle with the boot order in the BIOS to put the Windows Boot Loader above Ubuntu, Windows loads fine. If I put Ubuntu above the WBL, Ubuntu boots fine. GRUB2 does not appear to see Windows 7 at all. I've even tried holding shift during boot, and didn't getany options. I have tried a few things I have found in the forums like updating grub, mounting the windows partition and updating grub, but nothing has worked. How do I get GRUB to give me an option between booting Ubuntu and Windows 7?

Long Explanation:

I purchased a new Acer Travelmate laptop. I shrank the Windows partition using the Windows Disk Management tool. (Trying to use this guide: [lifehacker.com]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")) After the partition was shrunk, I loaded up the Ubuntu LIVE CD, and hit install. I created a new partition in the un-allocated space, formatted it as ext2. I installed Ubuntu there, and it works fine. I think I see an error early in boot that says something like "efdisk read error", but I'm not sure because it's only on the screen for a split second. I have tried booting to the Windows repair disc and doing "bootrec /FixMbr", and it said it completed the operation successfully, but nothing changed. Suggestions?

Any help would be greatly appreciated!

Thanks,
   aero2600

---

### Post by oldfred on 2013-11-16
Why ext2? ext4 has been the standard for years.

I think I did see someone else try ext2 and have issues.
That lifehacker link is pretty old, so not everything is up to date, epecially for a new system.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 6ejrpksjgj on 2013-11-16
I went with ext2 over ext4 because I read something about Windows having issues accessing ext3 and ext4. Probably also bad/dated information. I'll boot from the Live disc and post that info here shortly.

UPDATE: here is the pastebin of the boot-info: [http://paste.ubuntu.com/6429253/]("http://paste.ubuntu.com/6429260/")

Second Udpate: Boot-Repair was able to fix Grub, and now I have a boot menu. Thank you for the advice, oldfred. I wouldn't have had to bother you if my searching had turned up boot-repair.

~aero2600

---

### Post by oldfred on 2013-11-16
Do not plan on letting Windows access Linux partitions. Better to create a shared NTFS data partition as then data can be read/write from both systems. At best Windows ext drivers are read only as Windows does not support Linux ownership & permissions. 

I really do not see anything wrong. It looks like at some point you booted Boot-Repair in BIOS mode as it installed a Windows boot loader to the MBR for BIOS boot. You want UEFI boot.

---

### Post by 6ejrpksjgj on 2013-11-16
So, looking at that boot-info I posted the link to, do I need to fix anything else, or am I good to go?

(thanks again, sir.)

~aero2600

---

### Post by oldfred on 2013-11-16
If it is working then it should be good.
It just is ext4 has a lot of improvements over the very old ext2. 
Journaling helps prevent or let you repair issues that may occur on a power failure or other abnormal shutdown.

---

