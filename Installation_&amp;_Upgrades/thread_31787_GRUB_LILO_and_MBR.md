---
title: "GRUB LILO and MBR"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by kstells on 2005-05-04
I've just downloaded Ubunto 5.04

The installation is perfect except in one point. When I install GRUB or LILO on the MBR it doesn't appears to be something wrong. But there is. When I reboot, it auto logs into Windows without appearing the bootloader or a message. I don't know where could be the problem.

I tried to install grub to /dev/fdo, boot the disket, and then boot ubuntu. But when the disket boots it appears GURB and nothing to do, it "crashes" there and stop working. 

I thinked about if the iso of the CD is wrong on that track, and I made the check of the cd from the installation menu. It says it's okay.

someone with the same problem? or someone who can enlight me or turn on the light XD?

---

### Post by alastair on 2005-05-04
Hard to say. It is good you managed to install GRUB on a floppy - but bad it didn't work.

On the floppy - you mean "GRUB" appears - then nothing?

More information :

What disks -1, 2? (master, slave?)
ATA or SATA?
Where did you install GRUB originally (/dev/hda,hdb?)
Did UBUNTU's install see you disks for partitioning?

---

### Post by kstells on 2005-05-05
Yes, it appears GRUB and then nothing. I can't pass commands.

i've got 2 principal HD, (the 3rd is only for storage).

in the Master i've got the XP 4 all the family. and in the slave, i've got the Linux, and it is where I'm trying to install ubuntu. The disks are ATA, i've tried if there was an option in the installation menu to create a bootable disk, but there isn't that option..

what can I do?

---

