---
title: "Lubutu Lenovo ideapad 100s boot loader problems. Pastebin report included"
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by styrofoam-feet on 2018-05-30
Won't boot into Lubuntu, no dual partition. Been screwing around with bios and grub repair a bunch, and I just don't know what to make of it. Any help greatly appreciated.

 

[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
[/TD]
[TD="class: code"] Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 12152. According to the info in 
                       the boot sector, sda2 has 0 sectors.
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.
mount: /mnt/BootInfo/sda2: /dev/sda2 already mounted or mount point busy.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.9 GiB, 2063597568 bytes, 4030464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              0     2,111,199     2,111,200   0 Empty
/dev/sda2              12,152        16,823         4,672  ef EFI (FAT-12/16/32)

/dev/sda1 overlaps with /dev/sda2

GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1   +  R              0     2,111,143     2,111,144 Data partition (Windows/Linux)
/dev/sda2   +  R         12,152        16,823         4,672 Data partition (Windows/Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0                                                       
/dev/mmcblk0p1   84f096d7-31fc-4b3f-83c5-d5e26eca1226   ext4       
/dev/mmcblk0p5   9a942953-c298-40b0-8bb7-e90b5149921c   swap       
/dev/sda1        2018-04-26-18-40-24-00                 iso9660    Lubuntu 18.04 LTS amd64
/dev/sda2        044E-AC17                              vfat       
/dev/zram0       527b61cb-377d-4c46-a0be-9fc22d023532   swap       
/dev/zram1       a714c814-3796-4160-a550-a6d42226ffb9   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 13 May 30 14:40 mmc-DB4032_0x87256740 -> ../../mmcblk0
lrwxrwxrwx 1 root root 15 May 30 14:40 mmc-DB4032_0x87256740-part1 -> ../../mmcblk0p1
lrwxrwxrwx 1 root root 15 May 30 14:40 mmc-DB4032_0x87256740-part2 -> ../../mmcblk0p2
lrwxrwxrwx 1 root root 15 May 30 14:40 mmc-DB4032_0x87256740-part5 -> ../../mmcblk0p5
lrwxrwxrwx 1 root root  9 May 30 14:40 usb-_USB_DISK_2.0_07781C027FB8-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 May 30 14:40 usb-_USB_DISK_2.0_07781C027FB8-0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 May 30 14:40 usb-_USB_DISK_2.0_07781C027FB8-0:0-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mmcblk0p1   /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226 ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sda         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  9c 04 00 00 00 00 00 00  28 74 e9 67 00 00 80 00  |........(t.g....|
000001c0  01 00 00 40 e0 f6 00 00  00 00 e0 36 20 00 00 fe  |...@.......6 ...|
000001d0  ff ff ef fe ff ff 78 2f  00 00 40 12 00 00 00 00  |......x/..@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


/dev/sda1: unknown GPT attributes
1000000000000001

/dev/sda2: unknown GPT attributes
1000000000000001
Unknown BootLoader on sda1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f3 06 b4 42 eb 15 eb 02  |...t.f.....B....|
00000070  31 c9 5a 51 b4 08 cd 13  5b 0f b6 c6 40 50 83 e1  |1.ZQ....[...@P..|
00000080  3f 51 f7 e1 53 52 50 bb  00 7c b9 04 00 66 a1 b0  |?Q..SRP..|...f..|
00000090  07 e8 44 00 0f 82 80 00  66 40 80 c7 02 e2 f2 66  |..D.....f@.....f|
000000a0  81 3e 40 7c fb c0 78 70  75 09 fa bc ec 7b ea 44  |.>@|..xpu....{.D|
000000b0  7c 00 00 e8 83 00 69 73  6f 6c 69 6e 75 78 2e 62  ||.....isolinux.b|
000000c0  69 6e 20 6d 69 73 73 69  6e 67 20 6f 72 20 63 6f  |in missing or co|
000000d0  72 72 75 70 74 2e 0d 0a  66 60 66 31 d2 66 03 06  |rrupt...f`f1.f..|
000000e0  f8 7b 66 13 16 fc 7b 66  52 66 50 06 53 6a 01 6a  |.{f...{fRfP.Sj.j|
000000f0  10 89 e6 66 f7 36 e8 7b  c0 e4 06 88 e1 88 c5 92  |...f.6.{........|
00000100  f6 36 ee 7b 88 c6 08 e1  41 b8 01 02 8a 16 f2 7b  |.6.{....A......{|
00000110  cd 13 8d 64 10 66 61 c3  e8 1e 00 4f 70 65 72 61  |...d.fa....Opera|
00000120  74 69 6e 67 20 73 79 73  74 65 6d 20 6c 6f 61 64  |ting system load|
00000130  20 65 72 72 6f 72 2e 0d  0a 5e ac b4 0e 8a 3e 62  | error...^....>b|
00000140  04 b3 07 cd 10 3c 0a 75  f1 cd 18 f4 eb fd 00 00  |.....<.u........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  9c 04 00 00 00 00 00 00  28 74 e9 67 00 00 80 00  |........(t.g....|
000001c0  01 00 00 40 e0 f6 00 00  00 00 e0 36 20 00 00 fe  |...@.......6 ...|
000001d0  ff ff ef fe ff ff 78 2f  00 00 40 12 00 00 00 00  |......x/..@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/9848/mountinfo) leaked on lvs invocation. Parent PID 16992: bash
File descriptor 63 (pipe:[75236]) leaked on lvs invocation. Parent PID 16992: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20180530_1440 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Error: /dev/mmcblk0boot0: unrecognised disk label
Error: /dev/mmcblk0boot1: unrecognised disk label
boot-repair is executed in live-session (Ubuntu 18.04 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
mmcblk0 (sda) has unknown type. Please report this message to [email]boot.repair@gmail.com[/email]
cat: /sys/block/mmcblk0/mmcblk0boot0/start: No such file or directory
cat: /sys/block/mmcblk0/mmcblk0boot1/start: No such file or directory

=================== os-prober:
/dev/mmcblk0p1:Ubuntu 14.04.5 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/mmcblk0p1: UUID="84f096d7-31fc-4b3f-83c5-d5e26eca1226" TYPE="ext4" PARTUUID="000c2c87-01"
/dev/loop0: TYPE="squashfs"
/dev/mmcblk0p5: UUID="9a942953-c298-40b0-8bb7-e90b5149921c" TYPE="swap" PARTUUID="000c2c87-05"
/dev/sda1: UUID="2018-04-26-18-40-24-00" LABEL="Lubuntu 18.04 LTS amd64" TYPE="iso9660" PTUUID="67e97428" PTTYPE="dos" PARTUUID="67e97428-01"
/dev/sda2: SEC_TYPE="msdos" UUID="044E-AC17" TYPE="vfat" PARTUUID="67e97428-02"
/dev/zram0: UUID="527b61cb-377d-4c46-a0be-9fc22d023532" TYPE="swap"
/dev/zram1: UUID="a714c814-3796-4160-a550-a6d42226ffb9" TYPE="swap"
/dev/mmcblk0: PTUUID="000c2c87" PTTYPE="dos"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


=================== /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Aug  3  2016 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Aug  2  2016 00_header
-rwxr-xr-x 1 root root  6058 May 13  2015 05_debian_theme
-rwxr-xr-x 1 root root 11608 Aug  2  2016 10_linux
-rwxr-xr-x 1 root root 10412 Aug  2  2016 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Aug  2  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Aug  2  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Aug  2  2016 40_custom
-rwxr-xr-x 1 root root   216 Aug  2  2016 41_custom
-rw-r--r-- 1 root root   483 Aug  2  2016 README




=================== /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0014
Timeout: 0 seconds
BootOrder: 0000,0001,0012,0013,0014,0015,0016,0017
Boot0000* ubuntu	HD(1,GPT,ee001cd5-a031-442f-a1ab-c361f1f5ae7b,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot0001* Windows Boot Manager	HD(1,MBR,0x67e97428,0x2f78,0x1240)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0010  Setup	FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu	FvFile(86488440-41bb-42c7-93ac-450fbf7766bf)
Boot0012* ATA HDD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot0013* eMMC Disk:  SanDisk iNAND 32GB	PciRoot(0x0)/Pci(0x10,0x0)/Ctrl(0x0)..]3.K.L......2.
Boot0014* USB HDD: USB DISK 2.0	PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)3.!..3.G..A.....
Boot0015* PCI LAN:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0016* USB FDD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0017* USB CD:	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0018* Lenovo Recovery System	File(EFIMicrosoftBootlrsBootMgr.efi)..

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
mmcblk0p1	: mmcblk0,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	notbiosboot, /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226.

mmcblk0	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	mmc-disk, has-os,	1 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:2064MB:scsi:512:512:unknown: USB DISK 2.0:;

BYT;
/dev/zram1:483MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:483MB:483MB:linux-swap(v1)::;

BYT;
/dev/mmcblk0boot0:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;

BYT;
/dev/zram0:483MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:483MB:483MB:linux-swap(v1)::;

BYT;
/dev/mmcblk0boot1:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;

BYT;
/dev/mmcblk0:31.3GB:sd/mmc:512:512:msdos:MMC DB4032:;
1:1049kB:29.3GB:29.3GB:ext4::boot;
2:29.3GB:31.3GB:1984MB:::;
5:29.3GB:31.3GB:1984MB:linux-swap(v1)::;

=================== lsblk:
KNAME        TYPE FSTYPE     SIZE LABEL
loop0        loop squashfs 967.6M
sda          disk iso9660    1.9G Lubuntu 18.04 LTS amd64
sda1         part iso9660      1G Lubuntu 18.04 LTS amd64
sda2         part vfat       2.3M Lubuntu 18.04 LTS amd64
mmcblk0      disk           29.1G
mmcblk0p1    part ext4      27.3G
mmcblk0p2    part              1K
mmcblk0p5    part swap       1.9G
mmcblk0boot0 disk              4M
mmcblk0boot1 disk              4M
zram0        disk          460.5M
zram1        disk          460.5M

KNAME        ROTA RO RM STATE   MOUNTPOINT
loop0           1  1  0         /rofs
sda             1  0  1 running /cdrom
sda1            1  0  1
sda2            1  0  1
mmcblk0         0  0  0
mmcblk0p1       0  0  0         /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226
mmcblk0p2       0  0  0
mmcblk0p5       0  0  0
mmcblk0boot0    0  1  0
mmcblk0boot1    0  1  0
zram0           0  0  0         [SWAP]
zram1           0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=921928k,nr_inodes=230482,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=188632k,mode=755)
/dev/sda on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14151)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=188628k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/mmcblk0p1 on /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)


=================== ls:
/sys/block/mmcblk0 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro hidden holders inflight integrity mmcblk0boot0 mmcblk0boot1 mmcblk0p1 mmcblk0p2 mmcblk0p5 power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/mmcblk0boot0 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro hidden holders inflight integrity power queue range removable ro ro_lock_until_next_power_on size slaves stat subsystem trace uevent
/sys/block/mmcblk0boot1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro hidden holders inflight integrity power queue range removable ro ro_lock_until_next_power_on size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/dev (filtered):  acpi_thermal_rel autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse gpiochip0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 initctl input kmsg lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mmcblk0 mmcblk0boot0 mmcblk0boot1 mmcblk0p1 mmcblk0p2 mmcblk0p5 mmcblk0rpmb mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sg0 shm snapshot snd stderr stdin stdout tpm0 tpmrm0 uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  901M     0  901M   0% /dev
tmpfs          tmpfs     185M  1.3M  183M   1% /run
/dev/sda       iso9660   1.1G  1.1G     0 100% /cdrom
/dev/loop0     squashfs  968M  968M     0 100% /rofs
/cow           overlay   922M  285M  637M  31% /
tmpfs          tmpfs     922M   33M  889M   4% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     922M     0  922M   0% /sys/fs/cgroup
tmpfs          tmpfs     922M  588K  921M   1% /tmp
tmpfs          tmpfs     185M   16K  185M   1% /run/user/999
/dev/mmcblk0p1 ext4       27G  2.7G   23G  11% /media/lubuntu/84f096d7-31fc-4b3f-83c5-d5e26eca1226

=================== fdisk -l:
Disk /dev/loop0: 967.6 MiB, 1014571008 bytes, 1981584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 29.1 GiB, 31268536320 bytes, 61071360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000c2c87

Device         Boot    Start      End  Sectors  Size Id Type
/dev/mmcblk0p1 *        2048 57192447 57190400 27.3G 83 Linux
/dev/mmcblk0p2      57194494 61069311  3874818  1.9G  5 Extended
/dev/mmcblk0p5      57194496 61069311  3874816  1.9G 82 Linux swap / Solaris


Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.9 GiB, 2063597568 bytes, 4030464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x67e97428

Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *        0 2111199 2111200    1G  0 Empty
/dev/sda2       12152   16823    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/zram0: 460.5 MiB, 482893824 bytes, 117894 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/zram1: 460.5 MiB, 482893824 bytes, 117894 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of mmcblk0p1 into the MBR of mmcblk0.
Additional repair would be performed: unhide-bootmenu-10s


=================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?


=================== User settings
The settings chosen by the user will not act on the boot.

 [/TD]
[/TR]
[/TABLE]

---

