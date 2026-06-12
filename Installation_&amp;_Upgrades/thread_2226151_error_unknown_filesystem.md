---
title: "error: unknown filesystem"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by ceeholmes on 2014-05-25
Hello! I know this is a common problem because I've read many threads about this, but none of the things I've read have helped me so far. I tried installing Ubuntu 13.10 from a live usb but after the reboot I got the error: unknown filesystem message. I tried with Boot Repair but unfortunately it didn't solve the problem, either. I can still run Ubuntu from a live usb but I don't have any other OS installed. Here's the boot info

```
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
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
526
527
528
529
530
531
532
533
534
535
536
537
538
539
540
541
542
543
544
545
546
547
548
549
550
551
552
553
554
555
556
557
558
559
560
561
562
563
564
565
566
567
568
569
570
571
572
573
574
575
576
577
578
579
580
581
582
583
584
585
586
587
588
589
590
591
592
593
594
595
596
597
598
599
600
601
602
603
604
605
606
607
608
609
610
611
612[/TD]
[TD="class: code"] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 151356560 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 94 for .
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 211744 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   154,224,639   154,222,592  83 Linux
/dev/sda2         154,226,686   156,301,311     2,074,626   5 Extended
/dev/sda5         154,226,688   156,301,311     2,074,624  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064    15,240,575    15,232,512   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb   ext4       
/dev/sda5        1740dd77-2910-4225-94ee-1ff65fc56539   swap       
/dev/sdb1        39A3-5759                              vfat       UUI
/dev/zram0       08cc80f6-2831-49a9-a524-b61624313169   swap       
/dev/zram1       aa578c80-b566-4ccf-9985-329b3b1632ba   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
else
  search --no-floppy --fs-uuid --set=root 3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
    else
      search --no-floppy --fs-uuid --set=root 3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
    fi
    linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.11.0-12-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb' {
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
        else
          search --no-floppy --fs-uuid --set=root 3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
        else
          search --no-floppy --fs-uuid --set=root 3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
    else
      search --no-floppy --fs-uuid --set=root 3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
    else
      search --no-floppy --fs-uuid --set=root 3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1740dd77-2910-4225-94ee-1ff65fc56539 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  da 2e 00 00 db 2e 00 00  50 03 00 00 ff ff ff ff  |........P.......|
00000010  2a 0d 00 00 a1 08 00 00  dc 2e 00 00 ff ff ff ff  |*...............|
00000020  ff ff ff ff ff ff ff ff  dd 2e 00 00 de 2e 00 00  |................|
00000030  ff ff ff ff df 2e 00 00  b8 05 00 00 ff ff ff ff  |................|
00000040  e0 2e 00 00 5d 05 00 00  e1 2e 00 00 e2 2e 00 00  |....]...........|
00000050  aa 0c 00 00 e3 2e 00 00  ff ff ff ff ff ff ff ff  |................|
00000060  ff ff ff ff ff ff ff ff  6c 19 00 00 ff ff ff ff  |........l.......|
00000070  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000080  e4 2e 00 00 ff ff ff ff  6e 19 00 00 e5 2e 00 00  |........n.......|
00000090  e6 2e 00 00 6d 19 00 00  e4 03 00 00 ff ff ff ff  |....m...........|
000000a0  e7 2e 00 00 52 0b 00 00  6f 19 00 00 b1 0b 00 00  |....R...o.......|
000000b0  ff ff ff ff b1 0a 00 00  e8 2e 00 00 70 19 00 00  |............p...|
000000c0  e0 07 00 00 e9 2e 00 00  ff ff ff ff ff ff ff ff  |................|
000000d0  72 19 00 00 ea 2e 00 00  eb 2e 00 00 52 0d 00 00  |r...........R...|
000000e0  81 19 00 00 74 19 00 00  75 19 00 00 ec 2e 00 00  |....t...u.......|
000000f0  ff ff ff ff 69 0a 00 00  ed 2e 00 00 ff ff ff ff  |....i...........|
00000100  c7 08 00 00 a7 04 00 00  ff ff ff ff ff ff ff ff  |................|
00000110  a8 0d 00 00 f1 03 00 00  c6 07 00 00 13 06 00 00  |................|
00000120  ff ff ff ff 52 1a 00 00  eb 30 00 00 51 1a 00 00  |....R....0..Q...|
00000130  45 07 00 00 53 1a 00 00  50 1a 00 00 ff ff ff ff  |E...S...P.......|
00000140  ff ff ff ff fa 06 00 00  ec 30 00 00 ff ff ff ff  |.........0......|
00000150  ff ff ff ff 57 1a 00 00  16 18 00 00 ff ff ff ff  |....W...........|
00000160  ee 30 00 00 6f 0f 00 00  ef 30 00 00 c1 08 00 00  |.0..o....0......|
00000170  55 1a 00 00 f0 30 00 00  f1 30 00 00 f2 30 00 00  |U....0...0...0..|
00000180  ff ff ff ff ff ff ff ff  f1 0d 00 00 4d 0b 00 00  |............M...|
00000190  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
000001a0  51 03 00 00 f3 30 00 00  0b 09 00 00 66 07 00 00  |Q....0......f...|
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff f4 30 00 fe  |.............0..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 1f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: /tmp/BootInfo-fhctc4Fm/Tmp_Log: No such file or directory
File descriptor 9 (/proc/13944/mounts) leaked on lvscan invocation. Parent PID 22675: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-05-25__20h18 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 13.10, saucy, Ubuntu, i686)
ls: no se puede acceder a /home/usr/.config: No existe el archivo o el directorio
CPU op-mode(s):        32-bit
file=/cdrom/preseed/lubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash -- debian-installer/language=es keyboard-configuration/layoutcode?=es

=================== os-prober:
/dev/sda1:Ubuntu 13.10 (13.10):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="3d6d24a8-d951-4b0b-9d94-8ddfd479ffeb" TYPE="ext4"
/dev/sda5: UUID="1740dd77-2910-4225-94ee-1ff65fc56539" TYPE="swap"
/dev/sdb1: LABEL="UUI" UUID="39A3-5759" TYPE="vfat"
/dev/zram0: UUID="08cc80f6-2831-49a9-a524-b61624313169" TYPE="swap"
/dev/zram1: UUID="aa578c80-b566-4ccf-9985-329b3b1632ba" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Atención: la partición extendida no empieza en un límite de cilindro.
DOS y Linux interpretarán el contenido de forma diferente.

=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 oct 16  2013 grub.d
total 72
-rwxr-xr-x 1 root root  7850 oct 10  2013 00_header
-rwxr-xr-x 1 root root  5949 ago 15  2013 05_debian_theme
-rwxr-xr-x 1 root root 11479 oct 10  2013 10_linux
-rwxr-xr-x 1 root root 10258 oct 10  2013 20_linux_xen
-rwxr-xr-x 1 root root  1798 jun 17  2013 20_memtest86+
-rwxr-xr-x 1 root root 11531 oct 10  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 oct 10  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 oct 10  2013 40_custom
-rwxr-xr-x 1 root root   216 oct 10  2013 41_custom
-rw-r--r-- 1 root root   483 oct 10  2013 README




=================== sda1/etc/default/grub :

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



=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HTS54168 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  79.0GB  79.0GB  primary   ext4            boot
2      79.0GB  80.0GB  1062MB  extended
5      79.0GB  80.0GB  1062MB  logical   linux-swap(v1)


Model: Kingston DataTraveler SE6 (scsi)
Disk /dev/sdb: 7803MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  7803MB  7799MB  primary  fat32        boot, lba



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:80.0GB:scsi:512:512:msdos:ATA Hitachi HTS54168;
1:1049kB:79.0GB:79.0GB:ext4::boot;
2:79.0GB:80.0GB:1062MB:::;
5:79.0GB:80.0GB:1062MB:linux-swap(v1)::;

BYT;
/dev/sdb:7803MB:scsi:512:512:msdos:Kingston DataTraveler SE6;
1:4129kB:7803MB:7799MB:fat32::boot, lba;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  497M  217M  280M  44% /
udev           devtmpfs   488M   12K  488M   1% /dev
tmpfs          tmpfs      100M  1.1M   99M   2% /run
/dev/sdb1      vfat       7.3G  798M  6.5G  11% /cdrom
/dev/loop0     squashfs   638M  638M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      497M  720K  496M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      497M     0  497M   0% /run/shm
none           tmpfs      100M   20K  100M   1% /run/user
/dev/sda1      ext4        73G  2.2G   67G   4% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d8c9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   154224639    77111296   83  Linux
/dev/sda2       154226686   156301311     1037313    5  Extended
/dev/sda5       154226688   156301311     1037312   82  Linux swap / Solaris

Disk /dev/sdb: 7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    15240575     7616256    c  W95 FAT32 (LBA)



=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No se han hecho cambios en el equipo.
[/TD]
[/TR]
[/TABLE]


```

Any help would be appreciated, I'm out of my depth here. Thanks!

---

### Post by ubfan1 on 2014-05-25
You need to install grub to the MBR of sda, not to the partition where it is now.  You may do this from the live usb, or really, think about re-installing the 14.04 release.

---

