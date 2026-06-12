---
title: "instanll xp on ide drive, ubuntu on sata drive"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by mcfly2309 on 2007-06-07
Hi, (first of all, excuse my bad english) i want to know if i can install xp on an old 20 gb ide drive and ubuntu on a partitioned 250gb sata drive. What does the grub do in that situation? does it detect both drives or only the one i have first in my bios? this is what i have tried:

i plugged the ide drive on the ide 1 port, a dvd writer on the ide 2 port, and the sata drive on the sata 1 port. then i configured the bios, it boots the dvd first, then the sata drive (there isn't a third option available and i can't boot one drive first then the other, i don't know why) then i installed ubuntu 7.04 on the second partition of the sata drive (the first was the swap partition) with the live cd, restarted and got the error 22 from grub 1.5. then i erased everything and installed in the first sata partition ubuntu 7.04 and left the second sata partition for swap, restarted and got error 15 from grub.

then i erased everything again, and configured the bios to boot first the dvd, then the ide drive, then i installed xp and everything is working fine now. now how should i proceed with the ubuntu installation?¿ should i leave the bios configuration like it is and install ubuntu on the sata drive? where does the grub program install, on the ide or on the sata drive? ¿can i use another boot loader than doesn't have conflicts with using 2 physical drives? i've read a lot that the ubuntu installation destroys the master boot record, what does this actually mean? please don't give me solutions by using floppy drive because i haven't got one.

---

### Post by logos34 on 2007-06-07
Grub merely overwrites whatever bootloader(windows ntldr here) was on the mbr...it doesn't 'destroy' it (that's pretty severe!).   You can repeatedly overwrite it without risk (as far as I know). 

Grub went by default to the ide drive because it basically has to guess druing install which disk is the master/main one.  Why it assumes IDE is and not the sata even though the latter is set first in the hard disk boot boot priority (and after the dvd) is due to the fact that it's programmed to scan to the ide channels first for whatever reason.  (Grub clearly needs to be revised because a lot of people now have sata drives as their primary bootable disk vs. just addon storage).  But in any case you can overide the default location and specify that it go to '/dev/sda' (the sata) instead of '/dev/hda'--this avoids messing up guessing which drive is '(hd0)' and which '(hda1)'.

You'll be fine with that setup, and you don't need to remap your menu.lst entry for windows (as you would have to if you were booting to windows via grub on the sata, in which case windows disk would be second in boot order--it's all down to windows refusing to startup unless it's satisfied it's FIRST!).

---

### Post by logos34 on 2007-06-07
To clarify:

Install ubuntu again to the sata like the first time, and let grub overwrite the windows bootloader on the ide disk.  Leave the boot order in the BIOS as you have it now (1. IDE, 2.Sata).  You will boot to IDE disk, grub menu will appear and then you choose which OS to start--windows on the same disk, or ubuntu on the sata.

---

### Post by mcfly2309 on 2007-07-30
thanks man, got it solved here is a helpful link in case someone hasnt seen it yet

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

---

