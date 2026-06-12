---
title: "hal.dll missing - no WinXP login"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by Gerrit Overweg on 2007-06-20
I have worked through all the posted items on hal.dll problems
I can now edit my boot.ini but am unsure if hda 5 were windows is on should be given inn as partition 5 or 6 
And if I have give other inputs after this changings.
I just worked a few days with ubuntu and have still little idea how to handel the commands.
here is  what fdisk -l gives:
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        2551    20482875    f  W95 Ext'd (LBA)
/dev/hda2   *        2552        2740     1518142+   e  W95 FAT16 (LBA)
/dev/hda3            2741        5804    24611580    c  W95 FAT32 (LBA)
/dev/hda4            5805        7227    11430247+  83  Linux
/dev/hda5               2        2263    18169483+   7  HPFS/NTFS
/dev/hda6            2406        2551     1172713+  82  Linux swap / Solaris
](*,)

---

### Post by Gerrit Overweg on 2007-06-21
I want to add, that my boot.ini is on hda 2 and windows on hda 5
The quetion is how to correct my boot.ini
And if I have to mount this file again or not. How one does that?

I tried to go through windowsconsole with bootcfg /rebuild, but the console didn't wan t to do that

---

