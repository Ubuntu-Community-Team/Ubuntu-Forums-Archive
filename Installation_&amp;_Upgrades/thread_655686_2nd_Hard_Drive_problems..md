---
title: "2nd Hard Drive problems."
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by oompedoomp on 2008-01-01
Hi all and a happy new year to you!

I need some advice on an infuriating problem I have. I think it best to outline the basic problem to you all and let you ask for detailed info as required.

I was running Mepis Linux quite happily on a box with two internal hard drives. I had evaluated Ubuntu and decided I would prefer this platform. Using a live cd I installed ubuntu. It parted my drive ok, keeping Mepis bootable. However, I now cannot access my second hard drive at all (It's listed in Qparted as Sdb). No partition has been detected. fstab cannot detect the HD at all. I just need to get it to operate as an EXT3 for use as storage. I have lost hair over this! My wife is about to leave me! Please suggest or ask away.

Many thanks

Si

---

### Post by taurus on 2008-01-01
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /ec/fstab
df -h
```

---

### Post by oompedoomp on 2008-01-02
Hi

Thank you. Output is as follows but it's not showing Sdb.


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1ee3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         385     3092481   83  Linux
/dev/sda2            4536        4865     2650725    5  Extended
/dev/sda3             386         704     2562367+  83  Linux
/dev/sda4   *         705        4401    29696152+  83  Linux
/dev/sda5            4691        4865     1405656   82  Linux swap / Solaris
/dev/sda6            4589        4690      819252   82  Linux swap / Solaris
/dev/sda7            4536        4588      425659+  82  Linux swap / Solaris

Partition table entries are not in disk order

Look forward to your comments.

Thanks again.

Si

---

### Post by oompedoomp on 2008-01-04
Ok 

I tried this:

 dmesg | grep sdb
[   92.077343] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   92.077347] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   92.077367] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[   92.077372] end_request: I/O error, dev sdb, sector 0
[   92.080053] sd 0:0:1:0: [sdb] Write Protect is off
[   92.080057] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   92.753520] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   92.753524] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   92.753544] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[   92.753549] end_request: I/O error, dev sdb, sector 0
[   92.761288] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   93.263409] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   93.263413] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   93.263433] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[   93.263438] end_request: I/O error, dev sdb, sector 0
[   93.263445] Buffer I/O error on device sdb, logical block 0
[   93.828737] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   93.828742] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   93.828762] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[   93.828766] end_request: I/O error, dev sdb, sector 0
[   93.834397] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[   94.405108] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   94.405113] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   94.405133] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[   94.405139] end_request: I/O error, dev sdb, sector 0
[   94.419262] sd 0:0:1:0: [sdb] Write Protect is off
[   94.419266] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   94.970452] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   94.970457] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   94.970477] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[   94.970482] end_request: I/O error, dev sdb, sector 0
[   94.989848] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   95.008097] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[   95.012114] sd 0:0:1:0: [sdb] Write Protect is off
[   95.012120] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   95.020300] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  101.344181] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  101.344185] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  101.344206] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  101.344211] end_request: I/O error, dev sdb, sector 20010624
[  101.344219] Buffer I/O error on device sdb, logical block 2501328
[  101.931673] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  101.931678] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  101.931698] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  101.931703] end_request: I/O error, dev sdb, sector 20010624
[  101.939660] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  102.541333] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  102.541338] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  102.541359] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  102.541364] end_request: I/O error, dev sdb, sector 20010800
[  102.541601] sd 0:0:1:0: [sdb] Write Protect is off
[  102.541605] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  102.541825] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  102.542638] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  102.542834] sd 0:0:1:0: [sdb] Write Protect is off
[  102.542837] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  102.543067] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.217503] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  103.217508] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  103.217528] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  103.217533] end_request: I/O error, dev sdb, sector 20010800
[  103.217540] Buffer I/O error on device sdb, logical block 2501350
[  103.240614] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  103.240730] sd 0:0:1:0: [sdb] Write Protect is off
[  103.240734] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  103.241229] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  103.782825] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  103.782829] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  103.782849] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  103.782854] end_request: I/O error, dev sdb, sector 0
[  103.783217] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  103.783319] sd 0:0:1:0: [sdb] Write Protect is off
[  103.783323] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  104.436826] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  104.436830] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  104.436851] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  104.436855] end_request: I/O error, dev sdb, sector 0
[  104.458080] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  104.979980] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  104.979984] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  104.980004] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  104.980009] end_request: I/O error, dev sdb, sector 0
[  104.985099] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  104.985349] sd 0:0:1:0: [sdb] Write Protect is off
[  104.985354] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  104.985600] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  105.556386] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  105.556390] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  105.556410] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  105.556416] end_request: I/O error, dev sdb, sector 20010808
[  105.556969] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  105.557919] sd 0:0:1:0: [sdb] Write Protect is off
[  105.557926] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  105.559059] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  106.121706] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  106.121710] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  106.121730] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  106.121735] end_request: I/O error, dev sdb, sector 20010808
[  106.124171] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  106.124284] sd 0:0:1:0: [sdb] Write Protect is off
[  106.124288] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  106.139118] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  106.753539] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  106.753544] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  106.753565] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  106.753570] end_request: I/O error, dev sdb, sector 20010808
[  106.754134] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  106.754403] sd 0:0:1:0: [sdb] Write Protect is off
[  106.754406] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  106.779950] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  107.352110] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  107.352114] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  107.352135] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  107.352140] end_request: I/O error, dev sdb, sector 20010808
[  107.354235] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  107.355684] sd 0:0:1:0: [sdb] Write Protect is off
[  107.355692] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  107.371968] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  107.895267] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  107.895272] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  107.895292] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  107.895297] end_request: I/O error, dev sdb, sector 20010808
[  108.516002] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  108.516006] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  108.516026] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  108.516032] end_request: I/O error, dev sdb, sector 20010808
[  108.516038] Buffer I/O error on device sdb, logical block 2501351
[  108.516633] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  108.516749] sd 0:0:1:0: [sdb] Write Protect is off
[  108.516753] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  108.542224] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  109.092410] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  109.092414] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  109.092434] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  109.092439] end_request: I/O error, dev sdb, sector 20010752
[  109.702068] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  109.702072] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  109.702091] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  109.702096] end_request: I/O error, dev sdb, sector 20010800
[  109.709142] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  110.289562] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  110.289566] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  110.289586] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  110.289591] end_request: I/O error, dev sdb, sector 20010808
[  110.289905] sd 0:0:1:0: [sdb] Write Protect is off
[  110.289909] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  110.301715] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  110.877057] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  110.877062] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[  110.877082] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[  110.877087] end_request: I/O error, dev sdb, sector 20010808
[  110.898875] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  110.899149] sd 0:0:1:0: [sdb] Write Protect is off
[  110.899154] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  110.909916] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  110.930211] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[  110.930305] sd 0:0:1:0: [sdb] Write Protect is off
[  110.930309] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[  110.934204] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9409.566739] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 9409.566743] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[ 9409.566763] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[ 9409.566768] end_request: I/O error, dev sdb, sector 0
[ 9409.566775] Buffer I/O error on device sdb, logical block 0
[ 9409.566784] Buffer I/O error on device sdb, logical block 1
[ 9409.566787] Buffer I/O error on device sdb, logical block 2
[ 9409.566790] Buffer I/O error on device sdb, logical block 3
[ 9409.568378] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[ 9409.596981] sd 0:0:1:0: [sdb] Write Protect is off
[ 9409.596988] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 9410.143170] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 9410.143175] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[ 9410.143195] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[ 9410.143200] end_request: I/O error, dev sdb, sector 0
[ 9410.143205] Buffer I/O error on device sdb, logical block 0
[ 9410.145141] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9410.686315] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 9410.686320] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[ 9410.686340] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[ 9410.686345] end_request: I/O error, dev sdb, sector 20010808
[ 9410.686351] Buffer I/O error on device sdb, logical block 2501351
[ 9410.688473] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[ 9411.273794] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 9411.273798] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[ 9411.273818] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[ 9411.273823] end_request: I/O error, dev sdb, sector 20010808
[ 9411.273830] Buffer I/O error on device sdb, logical block 2501351
[ 9411.275994] sd 0:0:1:0: [sdb] Write Protect is off
[ 9411.276002] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 9411.805869] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 9411.805874] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[ 9411.805894] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[ 9411.805899] end_request: I/O error, dev sdb, sector 0
[ 9411.805904] Buffer I/O error on device sdb, logical block 0
[ 9411.805913] Buffer I/O error on device sdb, logical block 1
[ 9411.805917] Buffer I/O error on device sdb, logical block 2
[ 9412.282500] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 9412.282505] sd 0:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[ 9412.282525] sd 0:0:1:0: [sdb] Add. Sense: No additional sense information
[ 9412.282530] end_request: I/O error, dev sdb, sector 0
[ 9412.283057] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9412.304702] sd 0:0:1:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
[ 9412.305846] sd 0:0:1:0: [sdb] Write Protect is off
[ 9412.305852] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 9412.307548] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

Can anyone tell me from this output why I cannot use this drive?

Many thanks

Si

---

