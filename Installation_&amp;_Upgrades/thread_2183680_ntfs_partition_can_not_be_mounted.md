---
title: "ntfs partition can not be mounted"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by housam-59 on 2013-10-25
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).

the above statement appears when trying to mount the ntfs partition. 
how can I solve it 
thanks
housam

---

### Post by oldfred on 2013-10-26
It may just need chkdsk from a Windows repairCD or recovery console if dual booting Windows. You may have to run multiple times as chkdsk does not always fix everything on one pass.

If chkdsk does not work, some advanced things to try. 
 If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition 
small 'system reserved' NTFS partition instead of the partition where windows was installed. 

   Major MFT errors after NTFS partition move. - meierfra.
[http://ubuntuforums.org/showthread.php?t=1368432&highlight=grldr](http://ubuntuforums.org/showthread.php?t=1368432&highlight=grldr)

---

### Post by housam-59 on 2013-10-29
Thanks, solved. I've installed win.7 instead of XP and it works.

---

