---
title: "windows 7 hibernate issues w/ multiboot ubuntu 10.04/grub2"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by ubnoobie on 2010-07-14
the remedies outlined in this post did not work.. [http://ubuntuforums.org/showthread.php?t=1341694](http://ubuntuforums.org/showthread.php?t=1341694)

*"makeactive" (grub) didn't work for me; and the windows bootloader partition is also (was already) the active boot partition on the win7 drive.*


my drive configuration, in bios boot priority order:

[LIST]
[*]**sdc** (pata, primary master): **ubuntu 10.04** w/ grub in mbr. three partitions (boot, swap, root). is first in bios boot order
[*]**sda** (first sata): **win7**, two ntfs partitions (boot and os). is second in bios boot order *(if pata drives are disconnected, automatically becomes first boot drive without any bios changes)*
[*]**sdd** (pata, primary slave): **winxp**, one ntfs partition and some unallocated space at the end. is third in bios boot order but likely never go that far at boot-up.
[*]**sdb** (second sata): two **data** partitions, one ntfs, one fat32. used for common data between the various operating systems.
[/LIST]

there is also an sata optical drive (second to hdd in bios boot order)

[B]
win7 hibernate does not work[/B] *(and shutdown /h reports it cannot find the hibernate file)* if the pata drives are connected and **system is booted via ubuntu 10.04's grub**.

** win7 DOES hibernate just fine on its own**, *when the two pata drives are completely disconnected* (win7's boot, no linux anywhere)


a little background:

each of the two windows versions was originally installed to its drive with ONLY that drive hooked up to the system, as i did not want a windows-based multiboot setup and i wanted each windows drive to be independent, able to boot on its own and by itself if it were ever needed (i.e. one of the other drives dies, etc)

ubuntu was installed with all four drives connected so grub could configure itself at install time with the extra operating systems and the extra partitions on the last drive.

the system was set up so that the pata drives would not necessarily need to be connected to run windows (primarily win 7), but if they are, grub would present its boot menu, saving last used boot option as default for next time (the advantage to grub vs just using the bios' boot drive menu).

motherboard is amd780g/sb700. win7 is x64, winxp and ubuntu are x86. hibernate status in winxp is unknown at present.


i do realize that this is most likely a windows issue.. but one the 'regular' windows crowd isn't going to know anything about (or even care).

---

### Post by oldfred on 2010-07-14
Normally I would say grub has nothing to do with it. And mixed PATA & SATA systems have more issues with drive order as some systems make PATA first in BIOS and some do not it seems.

Since you installed windows on its own it thinks it is sda and first in BIOS. Grub usually uses a map or drivemap command to make windows think it is first. perhaps after boot the hibernate does not recognize the system setting to make windows think it is sda and it sees sdb and then does not work. Do not know if that is the problem or if there is a fix.

---

