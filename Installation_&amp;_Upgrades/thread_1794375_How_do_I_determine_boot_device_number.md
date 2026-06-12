---
title: "How do I determine boot device number?"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by Yumil1988 on 2011-06-30
I'm currently running Ubuntu (w/ GRUB) and Windows XP. I'd like to remove Ubuntu and run the recovery on Windows XP because it has started not running correctly. The computer is about 5 years old and I figured I'd just wipe it clean and start over (read: remove Ubuntu and reinstall windows via the recovery console). 

I intend to follow the tutorial here: [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

However, I'm confused about determining the boot device number for Windows. I've run "sudo fdisk -l" and I can identify the windows drive in the list it says:

Device: /dev/sda1
Boot: *
Start: 1
End: 19352
Blocks: 155444908+
Id: 7
System: HPFS/NTFS

Am I looking for the 7, the 1, or something completely different? This is also the first partition on the list. 

sda2 (id: c) is a FAT32 drive. I think this is the recovery partition included on the HP desktop. 

sda3 (id:83) is Linux
sda4 (id: 82) is swap

Help is appreciated. I just need to run fixmbr. (I hope this is the right category)

---

### Post by nzjethro on 2011-06-30
The Windows device number is sda1. However, it is named differently to Grub. You can convert "sda1" to "hd0,0" (i.e. sda is the first drive, so is hd0; "1" is the first partition, so is ",0").

[This link]("http://www.gnu.org/software/grub/manual/grub.html#Naming-convention") has more info on the Grub naming convention, so you can properly determine your device numbers and names.

---

### Post by YesWeCan on 2011-07-01
BTW the Grubites changed it in Grub2. sda1 used to be hd0,0 but is now hd0,1. In Grub2 the second number is the same as the sd number.

---

