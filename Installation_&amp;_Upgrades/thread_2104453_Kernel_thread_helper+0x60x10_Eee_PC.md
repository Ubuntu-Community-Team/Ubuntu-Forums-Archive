---
title: "Kernel_thread_helper+0x6/0x10 Eee PC"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by Shyme on 2013-01-13
Hello,

(1) I tried to upgrade to 12.04 and the upgrade bugged. Since then, I tried to reinstall with usb device. I change the Boot Device Priority (Removable Dev. is first) but even with this change, I receive this awful page:

error:no module specified.
error:no suitable mode found.
error:unknown command 'terminator'.
[ 0.925821] Kernel panic - not syncing:VFS:Unable to mount root fs on unknown-block(0,0)
[ 0.925900] Pid: 1, comm:swapper/0 Not tainted 3.2.0-33-generic #52-Ubuntu
[ 0.925964] Call trace:
[ 0.926030] [<c15601f1>] ? printk+0x2d/0x2f
[ 0.926094] [<c15600bf>] panic+0x5c/0x161
[ 0.926157] [<c1832b59>] mount_block_root+0xb9/0x14c
[ 0.926223] [<c1140ffc>] ? sys_mknod+0x2c/0x30
[ 0.926284] [<c1832d64>] mount_root+0x59/0x5f
[ 0.926346] [<c1832eb8>] prepare_namespace+0x14e/0x192
[ 0.926410] [<c1131c35>] ? sys_access0x25/0x30
[ 0.926472] [<c18328cd>] kernel_init+0x156/0x15b
[ 0.926533] [<c1832777>] ? start_kernel+0x353/0x353
[ 0.926597] [<c157ca3e>] kernel_thread_helper+0x6/0x10

I am not a Ubuntu or programmer. Could someone explain me step by step what should I do in order to fix this problem and have finally 12.04 installed on my Eee PC 1201HA (Netbook).

Thanks a lot,

I speak French, Spanish and English. So, anyone who speaks one of these languages is welcome ;-)

(2) I have just changed the "Hard Disk Drives". Now, first Drive is USB: and 2nd Drive [SATA:PM-WDC WD 2500]. And now, I do not recevie previous awful page (kernel panic and other strange line codes) but a black screen (NOTHING). 

(3) Now, I have changed again the Boot Device Priority to USB: as first one (before it was Removable Dev.). And, still this black screen.

---

