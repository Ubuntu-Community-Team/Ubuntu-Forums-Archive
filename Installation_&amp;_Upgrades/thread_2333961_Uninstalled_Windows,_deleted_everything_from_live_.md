---
title: "Uninstalled Windows, deleted everything from live CD - Installed Ubuntu - I/O Errors"
date: 2016-08-14
forum: Installation &amp; Upgrades
---

### Post by rurials2 on 2016-08-14
Hi all,

I hope this isn't a bore for you guys, but my Windows broke down while I had a dual boot with Kali and I just couldnt get it to work, sick of both systems I deleted them from a Ubuntu live cd - stupid I know. Now I cant get Ubuntu to work despite its supposedly being only system on my computer and Grub 2 working. 

Basically it get stuck loading after the first install. When I try to repair it via a live ubuntu cd nothing works as I get errors when I run the command below:

```
sudo fsck /dev/sda1
fsck from util-linux 2.27.1

e2fsck 1.42.13 (17-May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?


Here's more sepcific info on my situation:

ls -l /dev/sd*
brw-rw---- 1 root disk 8, 0 Aug 15 01:22 /dev/sda
brw------- 1 root root 8, 1 Aug 15 01:21 /dev/sda1
brw-rw---- 1 root disk 8, 2 Aug 15 01:37 /dev/sda2
brw------- 1 root root 8, 5 Aug 15 01:18 /dev/sda5
ubuntu@ubuntu:~$ dmesg | grep sda
[    8.477479] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    8.477481] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    8.477562] sd 1:0:0:0: [sda] Write Protect is off
[    8.477564] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.477589] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.927859]  sda: sda1 sda2 < sda5 >
[    8.928321] sd 1:0:0:0: [sda] Attached SCSI disk
[  157.339093] sd 1:0:0:0: [sda] tag#5 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[  157.339103] sd 1:0:0:0: [sda] tag#5 CDB: Read(10) 28 00 00 00 18 00 00 00 08 00
[  157.339107] blk_update_request: I/O error, dev sda, sector 6144
[  157.339170] sd 1:0:0:0: [sda] tag#4 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[  157.339171] sd 1:0:0:0: [sda] tag#4 CDB: Read(10) 28 00 73 73 90 00 00 00 08 00
[  157.339172] blk_update_request: I/O error, dev sda, sector 1936953344
[  157.557014] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  222.543746] Adding 8287228k swap on /dev/sda5.  Priority:-1 extents:1 across:8287228k FS
[  416.914746] sd 1:0:0:0: [sda] tag#29 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  416.914748] sd 1:0:0:0: [sda] tag#29 Sense Key : Medium Error [current] [descriptor] 
[  416.914750] sd 1:0:0:0: [sda] tag#29 Add. Sense: Unrecovered read error - auto reallocate failed
[  416.914752] sd 1:0:0:0: [sda] tag#29 CDB: Read(10) 28 00 73 73 88 00 00 00 08 00
[  416.914754] blk_update_request: I/O error, dev sda, sector 1936951296
[  505.779633] sd 1:0:0:0: [sda] tag#28 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  505.779635] sd 1:0:0:0: [sda] tag#28 Sense Key : Medium Error [current] [descriptor] 
[  505.779637] sd 1:0:0:0: [sda] tag#28 Add. Sense: Unrecovered read error - auto reallocate failed
[  505.779639] sd 1:0:0:0: [sda] tag#28 CDB: Read(10) 28 00 73 73 77 f0 00 00 08 00
[  505.779640] blk_update_request: I/O error, dev sda, sector 1936947184
[  584.299699] sd 1:0:0:0: [sda] tag#30 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  584.299702] sd 1:0:0:0: [sda] tag#30 Sense Key : Medium Error [current] [descriptor] 
[  584.299704] sd 1:0:0:0: [sda] tag#30 Add. Sense: Unrecovered read error - auto reallocate failed
[  584.299706] sd 1:0:0:0: [sda] tag#30 CDB: Read(10) 28 00 73 73 77 f0 00 00 08 00
[  584.299708] blk_update_request: I/O error, dev sda, sector 1936947184
[  772.307434] sd 1:0:0:0: [sda] tag#2 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  772.307436] sd 1:0:0:0: [sda] tag#2 Sense Key : Medium Error [current] [descriptor] 
[  772.307438] sd 1:0:0:0: [sda] tag#2 Add. Sense: Unrecovered read error - auto reallocate failed
[  772.307440] sd 1:0:0:0: [sda] tag#2 CDB: Read(10) 28 00 73 73 80 00 00 00 08 00
[  772.307442] blk_update_request: I/O error, dev sda, sector 1936949248
[  777.341996] sd 1:0:0:0: [sda] tag#13 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  777.341998] sd 1:0:0:0: [sda] tag#13 Sense Key : Medium Error [current] [descriptor] 
[  777.342000] sd 1:0:0:0: [sda] tag#13 Add. Sense: Unrecovered read error - auto reallocate failed
[  777.342002] sd 1:0:0:0: [sda] tag#13 CDB: Read(10) 28 00 73 73 80 08 00 00 08 00
[  777.342004] blk_update_request: I/O error, dev sda, sector 1936949256
[  779.372143] sd 1:0:0:0: [sda] tag#26 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  779.372146] sd 1:0:0:0: [sda] tag#26 Sense Key : Medium Error [current] [descriptor] 
[  779.372147] sd 1:0:0:0: [sda] tag#26 Add. Sense: Unrecovered read error - auto reallocate failed
[  779.372150] sd 1:0:0:0: [sda] tag#26 CDB: Read(10) 28 00 73 73 80 00 00 00 08 00
[  779.372151] blk_update_request: I/O error, dev sda, sector 1936949248
[  783.845494] sd 1:0:0:0: [sda] tag#13 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  783.845496] sd 1:0:0:0: [sda] tag#13 Sense Key : Medium Error [current] [descriptor] 
[  783.845499] sd 1:0:0:0: [sda] tag#13 Add. Sense: Unrecovered read error - auto reallocate failed
[  783.845501] sd 1:0:0:0: [sda] tag#13 CDB: Read(10) 28 00 73 73 7f fe 00 00 02 00
[  783.845503] blk_update_request: I/O error, dev sda, sector 1936949246
[  837.886478] sd 1:0:0:0: [sda] tag#20 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  837.886481] sd 1:0:0:0: [sda] tag#20 Sense Key : Medium Error [current] [descriptor] 
[  837.886483] sd 1:0:0:0: [sda] tag#20 Add. Sense: Unrecovered read error - auto reallocate failed
[  837.886485] sd 1:0:0:0: [sda] tag#20 CDB: Read(10) 28 00 73 73 77 80 00 00 08 00
[  837.886487] blk_update_request: I/O error, dev sda, sector 1936947072
[  906.023160] sd 1:0:0:0: [sda] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  906.023166] sd 1:0:0:0: [sda] tag#3 Sense Key : Medium Error [current] [descriptor] 
[  906.023171] sd 1:0:0:0: [sda] tag#3 Add. Sense: Unrecovered read error - auto reallocate failed
[  906.023177] sd 1:0:0:0: [sda] tag#3 CDB: Read(10) 28 00 73 73 81 10 00 00 f0 00
[  906.023180] blk_update_request: I/O error, dev sda, sector 1936949568
[  912.332729] sd 1:0:0:0: [sda] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  912.332791] sd 1:0:0:0: [sda] tag#12 Sense Key : Medium Error [current] [descriptor] 
[  912.332807] sd 1:0:0:0: [sda] tag#12 Add. Sense: Unrecovered read error - auto reallocate failed
[  912.332817] sd 1:0:0:0: [sda] tag#12 CDB: Read(10) 28 00 73 73 81 10 00 00 08 00
[  912.332823] blk_update_request: I/O error, dev sda, sector 1936949520
[  912.332831] Buffer I/O error on dev sda5, logical block 34, async page read
[  916.015933] sd 1:0:0:0: [sda] tag#22 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  916.015939] sd 1:0:0:0: [sda] tag#22 Sense Key : Medium Error [current] [descriptor] 
[  916.015944] sd 1:0:0:0: [sda] tag#22 Add. Sense: Unrecovered read error - auto reallocate failed
[  916.015949] sd 1:0:0:0: [sda] tag#22 CDB: Read(10) 28 00 73 73 77 f8 00 00 08 00
[  916.015953] blk_update_request: I/O error, dev sda, sector 1936947192
[  924.706334] sd 1:0:0:0: [sda] tag#6 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  924.706340] sd 1:0:0:0: [sda] tag#6 Sense Key : Medium Error [current] [descriptor] 
[  924.706345] sd 1:0:0:0: [sda] tag#6 Add. Sense: Unrecovered read error - auto reallocate failed
[  924.706350] sd 1:0:0:0: [sda] tag#6 CDB: Read(10) 28 00 73 73 81 18 00 00 08 00
[  924.706354] blk_update_request: I/O error, dev sda, sector 1936949528
[  924.706361] Buffer I/O error on dev sda5, logical block 35, async page read
[ 1173.816753] sd 1:0:0:0: [sda] tag#26 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1173.816758] sd 1:0:0:0: [sda] tag#26 Sense Key : Medium Error [current] [descriptor] 
[ 1173.816762] sd 1:0:0:0: [sda] tag#26 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1173.816766] sd 1:0:0:0: [sda] tag#26 CDB: Read(10) 28 00 73 73 7f fe 00 00 02 00
[ 1173.816769] blk_update_request: I/O error, dev sda, sector 1936949246
[ 1177.743152] sd 1:0:0:0: [sda] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1177.743154] sd 1:0:0:0: [sda] tag#3 Sense Key : Medium Error [current] [descriptor] 
[ 1177.743156] sd 1:0:0:0: [sda] tag#3 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1177.743158] sd 1:0:0:0: [sda] tag#3 CDB: Read(10) 28 00 73 73 81 18 00 00 08 00
[ 1177.743160] blk_update_request: I/O error, dev sda, sector 1936949528
[ 1177.743163] Buffer I/O error on dev sda5, logical block 35, async page read
[ 1185.797495] sd 1:0:0:0: [sda] tag#29 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1185.797501] sd 1:0:0:0: [sda] tag#29 Sense Key : Medium Error [current] [descriptor] 
[ 1185.797506] sd 1:0:0:0: [sda] tag#29 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1185.797512] sd 1:0:0:0: [sda] tag#29 CDB: Read(10) 28 00 73 73 81 38 00 00 08 00
[ 1185.797515] blk_update_request: I/O error, dev sda, sector 1936949560
[ 1185.797521] Buffer I/O error on dev sda5, logical block 39, async page read
[ 1300.919019] sd 1:0:0:0: [sda] tag#30 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1300.919025] sd 1:0:0:0: [sda] tag#30 Sense Key : Medium Error [current] [descriptor] 
[ 1300.919029] sd 1:0:0:0: [sda] tag#30 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1300.919035] sd 1:0:0:0: [sda] tag#30 CDB: Read(10) 28 00 73 73 77 80 00 00 08 00
[ 1300.919039] blk_update_request: I/O error, dev sda, sector 1936947072
[ 1302.796398] sd 1:0:0:0: [sda] tag#3 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1302.796404] sd 1:0:0:0: [sda] tag#3 Sense Key : Medium Error [current] [descriptor] 
[ 1302.796409] sd 1:0:0:0: [sda] tag#3 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1302.796414] sd 1:0:0:0: [sda] tag#3 CDB: Read(10) 28 00 73 73 77 80 00 00 08 00
[ 1302.796418] blk_update_request: I/O error, dev sda, sector 1936947072
[ 1302.796424] Buffer I/O error on dev sda1, logical block 242118128, async page read
[ 2519.862139] sd 1:0:0:0: [sda] tag#17 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2519.862146] sd 1:0:0:0: [sda] tag#17 Sense Key : Medium Error [current] [descriptor] 
[ 2519.862150] sd 1:0:0:0: [sda] tag#17 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2519.862156] sd 1:0:0:0: [sda] tag#17 CDB: Read(10) 28 00 73 73 81 38 00 00 08 00
[ 2519.862160] blk_update_request: I/O error, dev sda, sector 1936949560
[ 2519.862165] Buffer I/O error on dev sda5, logical block 39, async page read
[ 2527.825121] sd 1:0:0:0: [sda] tag#27 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2527.825127] sd 1:0:0:0: [sda] tag#27 Sense Key : Medium Error [current] [descriptor] 
[ 2527.825132] sd 1:0:0:0: [sda] tag#27 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2527.825138] sd 1:0:0:0: [sda] tag#27 CDB: Read(10) 28 00 73 73 81 38 00 00 08 00
[ 2527.825141] blk_update_request: I/O error, dev sda, sector 1936949560
[ 2527.825147] Buffer I/O error on dev sda5, logical block 39, async page read
[ 2545.153793] sd 1:0:0:0: [sda] tag#8 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2545.153800] sd 1:0:0:0: [sda] tag#8 Sense Key : Medium Error [current] [descriptor] 
[ 2545.153804] sd 1:0:0:0: [sda] tag#8 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2545.153810] sd 1:0:0:0: [sda] tag#8 CDB: Read(10) 28 00 73 73 74 00 00 01 00 00
[ 2545.153814] blk_update_request: I/O error, dev sda, sector 1936946232
[ 2548.794802] sd 1:0:0:0: [sda] tag#24 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2548.794809] sd 1:0:0:0: [sda] tag#24 Sense Key : Medium Error [current] [descriptor] 
[ 2548.794814] sd 1:0:0:0: [sda] tag#24 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2548.794820] sd 1:0:0:0: [sda] tag#24 CDB: Read(10) 28 00 73 73 74 20 00 00 08 00
[ 2548.794823] blk_update_request: I/O error, dev sda, sector 1936946208
[ 2548.794829] Buffer I/O error on dev sda1, logical block 242118020, async page read
[ 2556.125504] sd 1:0:0:0: [sda] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2556.125510] sd 1:0:0:0: [sda] tag#12 Sense Key : Medium Error [current] [descriptor] 
[ 2556.125515] sd 1:0:0:0: [sda] tag#12 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2556.125521] sd 1:0:0:0: [sda] tag#12 CDB: Read(10) 28 00 73 73 74 38 00 00 08 00
[ 2556.125525] blk_update_request: I/O error, dev sda, sector 1936946232
[ 2556.125531] Buffer I/O error on dev sda1, logical block 242118023, async page read
[ 2557.989404] sd 1:0:0:0: [sda] tag#25 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2557.989410] sd 1:0:0:0: [sda] tag#25 Sense Key : Medium Error [current] [descriptor] 
[ 2557.989415] sd 1:0:0:0: [sda] tag#25 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2557.989421] sd 1:0:0:0: [sda] tag#25 CDB: Read(10) 28 00 73 73 81 38 00 00 08 00
[ 2557.989424] blk_update_request: I/O error, dev sda, sector 1936949560
[ 2557.989430] Buffer I/O error on dev sda5, logical block 39, async page read
[ 2565.851825] sd 1:0:0:0: [sda] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2565.851831] sd 1:0:0:0: [sda] tag#7 Sense Key : Medium Error [current] [descriptor] 
[ 2565.851836] sd 1:0:0:0: [sda] tag#7 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2565.851842] sd 1:0:0:0: [sda] tag#7 CDB: Read(10) 28 00 73 73 81 40 00 00 08 00
[ 2565.851845] blk_update_request: I/O error, dev sda, sector 1936949568
[ 2565.851852] Buffer I/O error on dev sda5, logical block 40, async page read
[ 2790.364859] sd 1:0:0:0: [sda] tag#22 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2790.364879] sd 1:0:0:0: [sda] tag#22 Sense Key : Medium Error [current] [descriptor] 
[ 2790.364884] sd 1:0:0:0: [sda] tag#22 Add. Sense: Unrecovered read error - auto reallocate failed
[ 2790.364890] sd 1:0:0:0: [sda] tag#22 CDB: Read(10) 28 00 73 73 77 f0 00 00 08 00
[ 2790.364894] blk_update_request: I/O error, dev sda, sector 1936947184
[ 3277.375816] sd 1:0:0:0: [sda] tag#26 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3277.375822] sd 1:0:0:0: [sda] tag#26 Sense Key : Medium Error [current] [descriptor] 
[ 3277.375827] sd 1:0:0:0: [sda] tag#26 Add. Sense: Unrecovered read error - auto reallocate failed
[ 3277.375832] sd 1:0:0:0: [sda] tag#26 CDB: Read(10) 28 00 73 73 74 00 00 01 00 00
[ 3277.375836] blk_update_request: I/O error, dev sda, sector 1936946256
[ 3666.660528] sd 1:0:0:0: [sda] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3666.660534] sd 1:0:0:0: [sda] tag#1 Sense Key : Medium Error [current] [descriptor] 
[ 3666.660539] sd 1:0:0:0: [sda] tag#1 Add. Sense: Unrecovered read error - auto reallocate failed
[ 3666.660545] sd 1:0:0:0: [sda] tag#1 CDB: Read(10) 28 00 73 73 76 00 00 01 00 00
[ 3666.660549] blk_update_request: I/O error, dev sda, sector 1936946752
[ 3977.619135] sd 1:0:0:0: [sda] tag#5 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.619141] sd 1:0:0:0: [sda] tag#5 CDB: Read(10) 28 00 73 73 76 40 00 01 00 00
[ 3977.619145] blk_update_request: I/O error, dev sda, sector 1936946752
[ 3977.619169] blk_update_request: I/O error, dev sda, sector 0
[ 3977.619207] sd 1:0:0:0: [sda] tag#7 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.619214] sd 1:0:0:0: [sda] tag#7 CDB: Read(10) 28 00 73 73 76 40 00 00 08 00
[ 3977.619218] blk_update_request: I/O error, dev sda, sector 1936946752
[ 3977.619222] Buffer I/O error on dev sda1, logical block 242118088, async page read
[ 3977.619344] sd 1:0:0:0: [sda] tag#8 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.619351] sd 1:0:0:0: [sda] tag#8 CDB: Read(10) 28 00 00 00 18 00 00 00 08 00
[ 3977.619354] blk_update_request: I/O error, dev sda, sector 6144
[ 3977.619393] sd 1:0:0:0: [sda] tag#9 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.619399] sd 1:0:0:0: [sda] tag#9 CDB: Read(10) 28 00 00 00 18 00 00 00 08 00
[ 3977.619401] blk_update_request: I/O error, dev sda, sector 6144
[ 3977.619404] Buffer I/O error on dev sda1, logical block 512, async page read
[ 3977.622573] sd 1:0:0:0: [sda] tag#11 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.622580] sd 1:0:0:0: [sda] tag#11 CDB: Read(10) 28 00 00 00 08 00 00 00 20 00
[ 3977.622583] blk_update_request: I/O error, dev sda, sector 2048
[ 3977.622634] sd 1:0:0:0: [sda] tag#12 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.622640] sd 1:0:0:0: [sda] tag#12 CDB: Read(10) 28 00 00 00 08 00 00 00 08 00
[ 3977.622642] blk_update_request: I/O error, dev sda, sector 2048
[ 3977.622646] Buffer I/O error on dev sda1, logical block 0, async page read
[ 3977.622730] sd 1:0:0:0: [sda] tag#13 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3977.622738] sd 1:0:0:0: [sda] tag#13 CDB: Read(10) 28 00 00 00 08 00 00 00 08 00
[ 3977.622741] blk_update_request: I/O error, dev sda, sector 2048
[ 3977.622745] Buffer I/O error on dev sda1, logical block 0, async page read
[ 4738.362756] sd 1:0:0:0: [sda] tag#18 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 4738.362761] sd 1:0:0:0: [sda] tag#18 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4738.362763] blk_update_request: I/O error, dev sda, sector 0
[ 4738.362785] sd 1:0:0:0: [sda] tag#19 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 4738.362788] sd 1:0:0:0: [sda] tag#19 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 4738.362790] blk_update_request: I/O error, dev sda, sector 0
[ 4738.362791] Buffer I/O error on dev sda, logical block 0, async page read
[ 5252.878648] sd 1:0:0:0: [sda] tag#23 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 5252.878658] sd 1:0:0:0: [sda] tag#23 CDB: Read(10) 28 00 00 00 08 00 00 00 08 00
[ 5252.878662] blk_update_request: I/O error, dev sda, sector 2048
[ 5252.878759] sd 1:0:0:0: [sda] tag#24 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 5252.878768] sd 1:0:0:0: [sda] tag#24 CDB: Read(10) 28 00 00 00 08 00 00 00 08 00
[ 5252.878772] blk_update_request: I/O error, dev sda, sector 2048
[ 5252.878776] Buffer I/O error on dev sda1, logical block 0, async page read
[ 5495.447486] sd 1:0:0:0: [sda] tag#28 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 5495.447496] sd 1:0:0:0: [sda] tag#28 CDB: Read(10) 28 00 00 00 00 00 00 00 08 00
[ 5495.447499] blk_update_request: I/O error, dev sda, sector 0
[ 5495.447504] Buffer I/O error on dev sda, logical block 0, async page read
ubuntu@ubuntu:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST1000LM024 HN-M Rev: 0001
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GT50N     Rev: LC02
  Type:   CD-ROM                           ANSI  SCSI revision: 05
```

---

### Post by wildmanne39 on 2016-08-14
Is the I/O Errors meaning input and output errors if so that usually means what ever disk you are using is failing.

The computer is having trouble reading and writing to the drive.

---

### Post by rurials2 on 2016-08-14
Yes its input output. I understand but before I buy a new hard drive are there any software solutions to this, as it was working fine up until i muddled the instillation. One more thing I noticed the error for fsck repair was mentioning ext2 not ext4 where I believe the Ubuntu instilation on sda1 is. Does this have any significance?

---

### Post by wildmanne39 on 2016-08-14
I am a little rusty on disk issues but you might be able to reformat the drive and it should block out the bad sectors then you should be able to reinstall but it may still fail soon or you could use a livecd or usb version of ubuntu and get the files off of the drive if it is in good enough condition to allow the copying of files.

---

### Post by grahammechanical on 2016-08-14
The Ubuntu live session has the Disks utility. That will let you access the drive's SMART Data & Self Tests as well as formatting the drive.

Regards.

---

### Post by oldfred on 2016-08-14
fsck is for the ext2, ext3 & ext4 family of formats. That is says ext2 is not an issue.

---

