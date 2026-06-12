---
title: "Vista (32) won't boot after 12.04 dual boot install"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by mmcl26554 on 2013-09-17
I installed a second 80GB drive for Ubuntu, cleaned it with Gparted and partitioned it.  I used a live usb SD card to install it along side windows.  The install went well and Ubuntu boots fine from the Grub menu but Vista will not.  After I select it from the menu all I get is a flashing cursor.   I have tried the most recent boot repair both from a disk and from inside Ubuntu.  I have read a lot on the subject and tried a lot of things but none worked.  Some of the suggestions referred to grub file labeled "menu.1st" but it does not exist.  One suggestion was to put some data in it directing windows to do chainloading.  I created the file and did that but it didn't work.  I am at the end of my skills to get this to work so I really need some help.   My final option would to install each OS individually and select the one to boot from the bios boot menu. That would work but I want to make Grub work.
Michael

---

### Post by UltimateCat on 2013-09-17
Hi:

Before I could install Ubuntu I had to shrink my Windows XP partition. Than I was able to install Ubuntu.
This is called dual booting-

Did you shrink your Windows Vista partition before you install your Ubuntu Linux? (Or) Is your Windows Vista on another HDD?

If not; you should be able to use the partition manager that comes with the Linux Ubuntu installer to resize your Windows partition.
You can decrease your Vista to about 1/2 the size so Ubuntu will have enough room unless you have more than one drive-

> I installed a second 80GB drive for Ubuntu

Is Ubuntu the only OS on that 80 GB HDD?


[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.bleepingcomputer.com/tutorials/shrink-and-extend-ntfs-volumes-in-windows/](http://www.bleepingcomputer.com/tutorials/shrink-and-extend-ntfs-volumes-in-windows/)

To view all partitions on your machine you can run this command:
As 'root"
```
fdisk -l

```
Post the output of that command when you have time.

---

### Post by Bubba_Jackson on 2013-09-17
Depending on the GRUB version installed, the configuration file is menu.lst (older GRUB) or grub.cfg (GRUB 2). I am guessing you have the grub.cfg file (located in /boot/grub) Please, post the contents of the file here and the output of the "fdisk" command.

---

### Post by Mark Phelps on 2013-09-17
If both drives were connected when you installed Ubuntu, you most likely installed GRUB to the Vista drive -- which has been known to corrupt Vista booting.  You should have come here first, and I would have told you to disconnect your Vista drive to prevent just this problem.

So now, you have TWO problems to fix -- getting Vista booting again and installing GRUB to the Ubuntu drive.

You should try using Boot-Repair, that might fix both:  [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by mmcl26554 on 2013-09-17
I'll post the outcome of```
fdisk -l
```
later but to answer the other questions
Ubuntu is the only OS on the 80GB drive Vista is on the other one
It is using Grub2 as it has a grub.cfg file  I did create the menu.1st just to insert what was suggested on another forum maybe I should have put it in the cfg file I can try that if it would help.   I'll try anything to get this to work.  
I used Boot repair to set Grub2 present on all disks but I can easily change that to sdb1 drive.  But the first time I did the install it was only on sdb1 and that didn't work either
Boot repair will fix windows so it will boot ok so that problem is easy to fix and if I have to reinstall Ubuntu it is also easy since I only began yesterday and have no data or programs.     Like I said if I cannot get it to work I'll just install ubuntu to the drive as if it was the only one so each OS thinks it is alone in the computer, But I want to be able to share files between the two OS's so would that still work?
Michael

---

### Post by Quackers on 2013-09-17
Are you getting a grub menu when you first start the computer - a choice of whether to boot Ubuntu or Windows?

---

### Post by mmcl26554 on 2013-09-17
Yes!  Then when I click on it I get a flashing (-) in the upper left of the screen and no hard drive activity.  I have waited as long as 15 minutes (on the possibility things are just slow) but nothing changes.
Michael

---

### Post by Quackers on 2013-09-17
Ok thanks. The output of Boot-Repair might help in finding out what's wrong.
Please suuply the pastebin info given at the end of running it.

---

### Post by mmcl26554 on 2013-09-17
I'll do that soon, I have to setup the web browser later today
Michael

---

### Post by mmcl26554 on 2013-09-17
here is the results of fdisk -l
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x652868aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08673c5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   105090774    52545356    7  HPFS/NTFS/exFAT
/dev/sdb2       105091070   117209087     6059009    5  Extended
/dev/sdb5   *   105091072   113037311     3973120   83  Linux
/dev/sdb6       113039360   117209087     2084864   82  Linux swap / Solaris
michael@GW-1:~$ 


```

---

### Post by mmcl26554 on 2013-09-17
Here is grub.cfg:

```
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
set default="Windows Vista (loader) (on /dev/sda1)"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=d6a1667f-6349-428c-bfa4-e2d9db952354 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
    echo    'Loading Linux 3.8.0-29-generic ...'
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=d6a1667f-6349-428c-bfa4-e2d9db952354 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4C303B4F303B3EF0
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by mmcl26554 on 2013-09-17
OK here is the output of boot repair

```
[COLOR=#000] 	       		       	    [h=1]Ubuntu Pastebin[/h] 	      [h=1]Paste from boot-repair at Tue, 17 Sep 2013 18:34:01 +0100[/h]  [Download as text]("http://paste.ubuntu.com/6120342/plain/")  [TABLE="class: pastetable"]
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
[/TD]
[TD="class: code"] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 5Sep2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   105,090,774   105,090,712   7 NTFS / exFAT / HPFS
/dev/sdb2         105,091,070   117,209,087    12,118,018   5 Extended
/dev/sdb5    *    105,091,072   113,037,311     7,946,240  83 Linux
/dev/sdb6         113,039,360   117,209,087     4,169,728  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4C303B4F303B3EF0                       ntfs       
/dev/sdb1        5BBEC93F78D5C006                       ntfs       
/dev/sdb5        d6a1667f-6349-428c-bfa4-e2d9db952354   ext4       
/dev/sdb6        5c412063-e907-4d54-83ad-4d060dbe340a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="Windows Vista (loader) (on /dev/sda1)"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
	linux	/boot/vmlinuz-3.8.0-29-generic root=UUID=d6a1667f-6349-428c-bfa4-e2d9db952354 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.8.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root d6a1667f-6349-428c-bfa4-e2d9db952354
	echo	'Loading Linux 3.8.0-29-generic ...'
	linux	/boot/vmlinuz-3.8.0-29-generic root=UUID=d6a1667f-6349-428c-bfa4-e2d9db952354 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.8.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 4C303B4F303B3EF0
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=d6a1667f-6349-428c-bfa4-e2d9db952354 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5c412063-e907-4d54-83ad-4d060dbe340a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  51.002082825 = 54.763069440   boot/grub/grub.cfg                             1
  53.258567810 = 57.185951744   boot/grub/core.img                             1
  51.108581543 = 54.877421568   boot/vmlinuz-3.8.0-29-generic                  1
  51.108581543 = 54.877421568   vmlinuz                                        1
  51.540164948 = 55.340830720   boot/initrd.img-3.8.0-29-generic               1
  51.540164948 = 55.340830720   initrd.img                                     1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  bb b1 ca 8d 1e 4f 52 91  c5 2a 28 42 a0 da 50 bb  |.....OR..*(B..P.|
00000010  15 0d 26 49 4b ca ea ee  02 31 b7 f0 6e a4 e6 93  |..&IK....1..n...|
00000020  91 df b7 47 d6 e5 24 c3  0d d1 53 46 7b 8c d4 75  |...G..$...SF{..u|
00000030  6a eb d0 c9 c2 49 de 26  21 e8 7a 09 4f 52 59 87  |j....I.&!.z.ORY.|
00000040  7b b9 0c b4 77 52 00 a7  cc 6e 99 44 22 0d 61 92  |{...wR...n.D".a.|
00000050  e0 a6 f6 fa 8b 93 59 87  bc 8f 4b 3e 7b 85 78 09  |......Y...K>{.x.|
00000060  31 34 4a 70 64 bc fe a9  e0 a8 27 6c a9 a1 23 95  |14Jpd.....'l..#.|
00000070  4b 85 d2 3f 93 33 c2 54  82 c9 d8 3d 69 c0 0a a4  |K..?.3.T...=i...|
00000080  75 fa 6f 9b cc 46 4f 9b  4a aa 01 f5 64 fc 24 9a  |u.o..FO.J...d.$.|
00000090  4f fd b4 09 28 b4 27 56  d2 0d c7 cb 9d 19 ee 3f  |O...(.'V.......?|
000000a0  7e ca f8 6d 8d a7 64 ef  b6 91 65 12 f9 a7 9e 21  |~..m..d...e....!|
000000b0  58 5c 2e c3 d3 62 b6 95  64 af b8 62 a2 e5 96 5b  |X\...b..d..b...[|
000000c0  7d 12 10 01 49 91 01 9b  34 57 a0 57 c8 be 04 9f  |}...I...4W.W....|
000000d0  79 9b 21 46 d2 81 53 9a  0b 46 fa 7d 54 ed 22 97  |y.!F..S..F.}T.".|
000000e0  65 b9 80 d1 87 99 90 81  25 7c 4b 1d 9d 62 4a c5  |e.......%|K..bJ.|
000000f0  95 0a 34 c9 71 17 67 ef  71 81 6d ba 18 c0 dc 19  |..4.q.g.q.m.....|
00000100  cf 7e 42 0a 30 55 a9 ac  e2 64 a5 bc 4a d7 91 e3  |.~B.0U...d..J...|
00000110  b1 4a 22 18 91 4c 21 92  dc bb 4a 4d a6 aa c6 06  |.J"..L!...JM....|
00000120  34 8e f4 9f e2 57 88 3d  a2 e6 e0 00 0f d4 c2 af  |4....W.=........|
00000130  20 04 6c 94 f1 93 2c 24  d5 15 ca 2b 99 57 5e 9a  | .l...,$...+.W^.|
00000140  68 a2 59 44 3a d6 c1 cd  b1 57 b2 33 d4 68 68 29  |h.YD:....W.3.hh)|
00000150  09 24 9b 2c 75 13 0a 46  c4 99 42 5b 8e 15 51 25  |.$.,u..F..B[..Q%|
00000160  7b 6e e6 ab 83 f0 5e 32  fc 2a 13 3c ac 62 01 5a  |{n....^2.*.<.b.Z|
00000170  2e d8 c0 a6 3b 57 49 35  9d 44 87 0f 9c 48 5b 99  |....;WI5.D...H[.|
00000180  85 70 0c 96 e8 71 d9 8c  cb 29 85 aa 3d d0 75 97  |.p...q...)..=.u.|
00000190  5a 22 9b c4 43 4d 27 1b  75 b8 3f 33 a4 18 4f ed  |Z"..CM'.u.?3..O.|
000001a0  a6 92 9a 0c 49 93 31 47  6d 79 01 ab 9b a5 1e 61  |....I.1Gmy.....a|
000001b0  40 d9 93 d3 c2 a8 32 ac  6d ff ff dc 4e 0e 80 fe  |@.....2.m...N...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 40 79 00 00 fe  |...........@y...|
000001d0  ff ff 05 fe ff ff 02 40  79 00 00 a8 3f 00 00 00  |.......@y...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-09-17__13h31 ===================
boot-repair version : 3.199~ppa27~precise
boot-sav version : 3.199~ppa27~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.199~ppa27~precise
boot-repair is executed in installed-session (Ubuntu 12.04.3 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=d6a1667f-6349-428c-bfa4-e2d9db952354 ro quiet splash vt.handoff=7

=================== os-prober:
/dev/sdb5:The OS now in use - Ubuntu 12.04.3 LTS CurrentSession:linux
/dev/sda1:Windows Vista (loader):Windows:chain

=================== blkid:
/dev/sda1: UUID="4C303B4F303B3EF0" TYPE="ntfs"
/dev/sdb1: UUID="5BBEC93F78D5C006" TYPE="ntfs"
/dev/sdb5: UUID="d6a1667f-6349-428c-bfa4-e2d9db952354" TYPE="ext4"
/dev/sdb6: UUID="5c412063-e907-4d54-83ad-4d060dbe340a" TYPE="swap"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Sep 17 13:04 grub.d
drwxr-xr-x  2 root root     4096 Aug 20 13:59 grub.d.bak
total 56
-rwxr-xr-x 1 root root 6743 Jul 19 19:32 00_header
-rwxr-xr-x 1 root root 5522 Jul 19 19:17 05_debian_theme
-rwxr-xr-x 1 root root 7780 Jul 19 19:32 10_linux
-rwxr-xr-x 1 root root 6335 Jul 19 19:32 20_linux_xen
-rwxr-xr-x 1 root root 7603 Jul 19 19:32 30_os-prober
-rwxr-xr-x 1 root root 1388 Jul 19 19:32 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Jul 19 19:32 40_custom
-rwxr-xr-x 1 root root   95 Jul 19 19:32 41_custom
-rw-r--r-- 1 root root  483 Jul 19 19:32 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Windows Vista (loader) (on /dev/sda1)"
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
This installed-session is not EFI-compatible.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sdb5	: sdb,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	.
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdb1.

sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	63 sectors * 512 bytes
sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	63 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD3200AAJS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  320GB  320GB  primary  ntfs         boot


Model: ATA ST96812AS (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  53.8GB  53.8GB  primary   ntfs
2      53.8GB  60.0GB  6204MB  extended
5      53.8GB  57.9GB  4068MB  logical   ext4            boot
6      57.9GB  60.0GB  2135MB  logical   linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA WDC WD3200AAJS-0;
1:32.3kB:320GB:320GB:ntfs::boot;

BYT;
/dev/sdb:60.0GB:scsi:512:512:msdos:ATA ST96812AS;
1:32.3kB:53.8GB:53.8GB:ntfs::;
2:53.8GB:60.0GB:6204MB:::;
5:53.8GB:57.9GB:4068MB:ext4::boot;
6:57.9GB:60.0GB:2135MB:linux-swap(v1)::;


=================== mount:
/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hpet input kmsg lirc0 log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb5 sdb6 sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  80 d6 42 25 00 00 00 00  |..........B%....|
00000030  5c 5e 0a 00 00 00 00 00  26 ad af 00 00 00 00 00  |^......&.......|
00000040  f6 00 00 00 01 00 00 00  f0 3e 3b 30 4f 3b 30 4c  |.........>;0O;0L|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  90 8e 43 06 00 00 00 00  |..........C.....|
00000030  04 00 00 00 00 00 00 00  c4 c7 6f 00 00 00 00 00  |..........o.....|
00000040  f6 00 00 00 01 00 00 00  06 c0 d5 78 3f c9 be 5b  |...........x?..[|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb5      ext4      3.7G  2.4G  1.2G  67% /
udev           devtmpfs  996M   12K  996M   1% /dev
tmpfs          tmpfs     402M  844K  401M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs    1004M   76K 1004M   1% /run/shm
/dev/sda1      fuseblk   299G  139G  160G  47% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk    51G   88M   51G   1% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x652868aa

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08673c5f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   105090774    52545356    7  HPFS/NTFS/exFAT
/dev/sdb2       105091070   117209087     6059009    5  Extended
/dev/sdb5   *   105091072   113037311     3973120   83  Linux
/dev/sdb6       113039360   117209087     2084864   82  Linux swap / Solaris


User choice: Is sdb (60.0GB) a removable disk? no
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdb (60.0GB) disk!

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS).
The boot flag would be placed on sdb5.
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

 [/TD]
[/TR]
[/TABLE]
 
 [Download as text]("http://paste.ubuntu.com/6120342/plain/") 
     		    
 	    
 	[/COLOR]

```

---

### Post by mmcl26554 on 2013-09-17
OK there is all the information requested, I sure you can come up with a solution.
Thanks everyone who responded and is trying to help!
Michael

---

### Post by Quackers on 2013-09-17
Sorry, please ignore (wrong info).
I'll have a look at your boot script output.

---

### Post by Quackers on 2013-09-17
I don't see anything wrong with the output of the boot script.
Can you state which hard drive is set to boot first in your bios please?
Also do you have a Windows Vista repair disc or installation disc?

---

### Post by mmcl26554 on 2013-09-17
yes to both and it is set to boot off sdb

---

### Post by Quackers on 2013-09-17
By all means see what others have to say but what I would recommend is that the bios be set to boot from the cd first then boot from the Windows repair cd and run the automatic repair utility. You may need to run this utility up to 3 times. 
Then set the bios to boot from the Windows drive and see if Windows will then boot.
Once Windows is booting normally you can then switch the bios back to booting from the Ubuntu drive and boot Ubuntu.
Once booted run sudo update-grub in the terminal and then reboot to see if Windows will boot from the grub menu.

---

### Post by mmcl26554 on 2013-09-17
I did pretty much what you said:
[SIZE=4]If I remove the Ubuntu drive and run boot repair then I can boot windows normally  (no grub), but of course I cannot boot Ubuntu if I put the drive  back in and set the bios to boot from it.   If I put the Ubuntu drive  back in and run boot repair I can then boot Ubuntu but not Vista.  This  is driving me NUTZ!!
Michael
[/SIZE]

---

### Post by mmcl26554 on 2013-09-17
I'm trying exactally what you said to do, see how that works

---

### Post by Quackers on 2013-09-17
Why would you need to run Boot-Repair once you've put the Ubuntu drive back in and set that drive to boot first in bios?
That drive should boot Ubuntu fine. It's likely that you'll just re-install grub to your Windows drive.

---

### Post by mmcl26554 on 2013-09-17
I ran the repair 4 times and it was unable to fix it so I used bootrec.exe from command prompt to to rebuild the Boot manager.  Vista is up but cannot boot ubuntu!  Now what?

---

### Post by Quackers on 2013-09-17
Ok so Windows boots normally from its own drive. That's good.
Now re-connect the Ubuntu drive and set the bios to boot from that drive.
Boot into Ubuntu and open up a terminal window and run ```
sudo update-grub
``` then enter your password.
In its output check that the Windows Vista loader is shown. It should be.
If it is reboot the computer leaving the bios alone and try to boot Windows from the grub menu.

---

### Post by mmcl26554 on 2013-09-17
I did set the bios to boot from the Ubuntu drive, however, it still boots vista.   Seems to make no attempt to boot Ubuntu?  I never removed the Ubuntu drive during this process but didn't make any changes to it also.

---

### Post by Quackers on 2013-09-17
It can't possibly boot Vista from the Ubuntu drive. There is no Vista on that drive.
Unless you ran the bootrec.exe instructions to the Ubuntu drive.
Did you run bootrec.exe whilst the bios was still set to boot the Windows drive?

---

### Post by mmcl26554 on 2013-09-17
No.  But the last time I ran boot repair without the ubuntu drive in and got Vista to boot again, then I reinstalled the Ubuntu drive and it still wouldn't boot from it, just went to windows even with the boot flag set to the second drive.

---

### Post by mmcl26554 on 2013-09-17
I have sent the data that boot repair generates to boot-repair and made a donation to them I assume they are the guru in all things Grub so it will be interesting what they come up with.

---

### Post by Quackers on 2013-09-17
When this all started wasn't Ubuntu the only OS you could get to?
Now it's only Vista? 
If that's true then changes have taken place to the Ubuntu drive somehow. Or your bios isn't changing drives as requested.

If you disconnect the Ubuntu drive and try to boot the system does Vista boot on its own once the bios is set to boot from that drive? Which I believe is where we were up to a couple of posts ago.

---

### Post by mmcl26554 on 2013-09-17
I'm sure if I remove the Ubuntu drive Vista will still boot, but Grub doesn't come up now or not that I can tell there is no grub menu now.  Just a screen asking me if I want to boot Vista or Vista home premium (the Os is actually Vista Ultimate)  Challenging?

---

### Post by Quackers on 2013-09-17
It wasn't really a challenge but it is now.
Grub won't come up on the Vista drive because it shouldn't be there now after you ran the bootrec commands to rebuild the BCD. Assuming your bios is set to boot that drive first (or second if the cd drive is first). You've written new code to the MBR of that drive over-writing grub, which is what was supposed to happen.

The only way now to boot Ubuntu (and see grub menu) is to set bios to boot from the Ubuntu drive before it boots the Windows drive.
As I understand it you have done that and it's still booting Vista which means that somehow grub is gone from that drive too.

---

### Post by mmcl26554 on 2013-09-17
I can remove the Vista drive and then run boot repair on the ubuntu drive to fix that?

---

### Post by Quackers on 2013-09-17
How? If you can't boot Ubuntu? 
Or do you mean run the bootrec commands on the Ubuntu drive?

---

### Post by mmcl26554 on 2013-09-17
I have another desktop computer (Older HP) Pentium 4 2.5GHz with the same OS and 2 drives that I want to install Ubuntu on but I am waiting to do that until I get this Gateway ONE working and I am also increasing the ram to 2GB and am waiting for it to arrive.  It will be interesting if I have the same problems with it.
Michael
OH, BTW my Wife wants to know if you have ever purchased cloths from "Quacker Factory"?

---

### Post by mmcl26554 on 2013-09-17
> **Quackers said:**
> How? If you can't boot Ubuntu? 
Or do you mean run the bootrec commands on the Ubuntu drive?
Run the boot repair disk to rebuild Grub on the ubuntu drive

---

### Post by Quackers on 2013-09-17
No, don't even know what Quacker factory is. I live in UK.

Sorry, what boot repair disc? Windows?
I think we're getting mixed up with terminology here.
Boot-Repair is a program written by a member of this forum to repair (usually) Ubuntu type systems.
Bootrec.exe is a Windows utility for repairing Windows systems' booting problems and is generally used by booting a Windows repair/installation disc. This will over-write grub.

As it's getting late here I can only suggest that you disconnect the Ubuntu drive completely and confirm that Vista boots from its own drive once bios is set to boot from that drive.
If that works ok we can then re-connect the Ubuntu drive and select that one in the bios boot order (after the cd drive) and see if it boots.
If it doesn't you can boot from the Ubuntu Live cd and we can speak again about repairing grub on that drive.

---

### Post by mmcl26554 on 2013-09-17
The boot repair disk I am referring to is from [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home).   And I did use the windows program Bootrec.exe to get Vist up and working again.   Quacker Factory is a maker of womens clothing sweaters and the like, high quality and also sold through the shopping channel QVC in USA.    We can talk tomorrow I'll make a post when I'm up.  Or we could use IM via Yahoo if you want.   I thank you for your kind assistance, and look forward to more chatts.
Michael McLeod
White Hall, WV

Sleep well

---

### Post by Quackers on 2013-09-17
Oh I see :-)
I'll be awake for a while yet if you want to make a start now. It's up to you.
Sadly I don't use IM any more.

---

### Post by mmcl26554 on 2013-09-17
OK, just tell me when you want to stop.   What would you like me to try now?

---

### Post by Quackers on 2013-09-17
I'd like to disconnect the Ubuntu drive then confirm that Vista will boot off its own disc when set as second boot device in the bios (ie after the cd drive or sd card)). If it does that's okay. If it doesn't run the bootrec commands to get it booting again. 

Once that's done I'd like you to re-connect the Ubuntu drive and make that the second boot device in the bios (after cd drive/sd card but before the Windows drive) and try to boot.
Does it boot or show anything?
If not boot from the Ubuntu live cd/usb/sd card (whichever you used to install Ubuntu) and select "try Ubuntu" then tell me when you're there please.

---

### Post by mmcl26554 on 2013-09-17
If I remove the Ubuntu drive then only the Vista drive will show up in the bios and Vista will boot ok.   The hard drives are set as the 4th boot device, CD->USB->SD-> hard drives.

---

### Post by Quackers on 2013-09-17
Ok that's great.
Now please re-connect the Ubuntu drive and set that as 4th boot device (one above the Windows drive) in the bios and try to boot. If it won't boot then boot from the Ubuntu live sd card and select try ubuntu.
Tell me when you're there please.
I'll get some commands ready to purge and re-install grub to the Ubuntu drive.

---

### Post by mmcl26554 on 2013-09-17
OK, just to verify things, I removed the vista drive with Ubuntu drine in place, tried to boot to network. Put vista in and removed Ubuntu, vista booted.  Out ubuntu in and now has booted with USB.

---

### Post by Quackers on 2013-09-17
so you are now in the "try ubuntu" desktop - correct?
Both drives are connected?

If so please open a terminal and run ```
sudo fdisk -l
``` - copy/paste it into terminal and hit enter.

Please post the output in code tags in your reply.

---

### Post by mmcl26554 on 2013-09-17
```
Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08673c5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   105090774    52545356    7  HPFS/NTFS/exFAT
/dev/sdb2       105091070   117209087     6059009    5  Extended
/dev/sdb5   *   105091072   113037311     3973120   83  Linux
/dev/sdb6       113039360   117209087     2084864   82  Linux swap / Solaris

Disk /dev/sdc: 3965 MB, 3965190144 bytes
255 heads, 63 sectors/track, 482 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004a82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        1985     7744510     3871263    c  W95 FAT32 (LBA)
this@this:~$ 


```

---

### Post by Quackers on 2013-09-17
Ok, I can see that the Windows drive is not connected. That's ok for the moment.
I presume the NTFS partition at /dev/sdb1 is a data partition of some kind? Not a Windows installation?

One thing puzzles me. Your terminal prompt is this@this when I would expect it to be ubuntu@ubuntu

---

### Post by mmcl26554 on 2013-09-17
it should be let me check

---

### Post by mmcl26554 on 2013-09-17
Well it is connected and I can boot windows from it

---

### Post by mmcl26554 on 2013-09-17
I don't know what the ntfs is on sdb1 because windows should be sda1   the this@this prompt is from the USB version of Ubuntu

---

### Post by Quackers on 2013-09-17
So you can now boot both operating systems from grub?
That sounds like you're booted into your Ubuntu system not the sd card "try ubuntu" desktop.

Whatever, if both systems are booting from grub your problem is over.

If that's the case leave the bios as it is.
It is preferable this way. If your Ubuntu drive goes faulty or anything you can set your bios to boot from the Windows drive and still get into Windows.

Please bear in mind that if you run Boot-Repair again and choose the recommended repair you will over-write the MBR on your Windows drive with grub. That could be a problem for booting Windows.

---

### Post by mmcl26554 on 2013-09-17
No Ubuntu does not boot from the hard drive but will boot from the live usb version.  Without the usb plugged in and the boot flag on ubuntu drive vista still boots, problem is not changed

---

### Post by mmcl26554 on 2013-09-17
The ultimate workaround or plan Z would to do a seperate install on the Ubuntu drive and choos the OS by selecting which drive to boot from by pressing the F10 key and select the drive.

---

### Post by Quackers on 2013-09-17
So are you now booted into your Ubuntu installation (hard drive) or in the USB Live desktop?

---

### Post by mmcl26554 on 2013-09-17
Usb

---

### Post by Quackers on 2013-09-17
So please run sudo fdisk -l again please and post the output. Thanks.

---

### Post by mmcl26554 on 2013-09-17
[SIZE=4]Ok now this is from the usb drive:
```
[/SIZE][SIZE=4]


[/SIZE]Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08673c5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   105090774    52545356    7  HPFS/NTFS/exFAT
/dev/sdb2       105091070   117209087     6059009    5  Extended
/dev/sdb5   *   105091072   113037311     3973120   83  Linux
/dev/sdb6       113039360   117209087     2084864   82  Linux swap / Solaris

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x652868aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 3965 MB, 3965190144 bytes
255 heads, 63 sectors/track, 482 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004a82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        1985     7744510     3871263    c  W95 FAT32 (LBA)
this@this:~$ 

[SIZE=4]
[/SIZE][SIZE=4]
```
[/SIZE]

---

### Post by Quackers on 2013-09-17
Hmm, again that terminal prompt is this@this

Is there an icon on the desktop that says install Ubuntu?

---

### Post by mmcl26554 on 2013-09-17
yes that is the way I know for sure it is the USB and also FF doesn't have the username and password for the form stored

---

### Post by Quackers on 2013-09-17
Ok, it seems the Windows drive is now connected and is 320GB.
Your Ubuntu drive is 60GB
Then there's a missing drive designation (/dev/sdc) - don't know why that's missing
then there's your 4GB sd card is it?

---

### Post by mmcl26554 on 2013-09-17
on the drive version also the prompt is michael@gw-1

---

### Post by Quackers on 2013-09-17
See post no 57 above.
If that is the case go and have a cup of coffee for a few minutes while I write some commands for you to enter into the terminal.

---

### Post by mmcl26554 on 2013-09-17
could sdc be the 
CD drive? as the USB is sdd

---

### Post by mmcl26554 on 2013-09-17
I'll go pet my Cats!

---

### Post by Quackers on 2013-09-17
Ok in the terminal please copy/paste these commands one line at a time pressing enter after each line 
```
sudo mkdir /mnt/temp 
sudo mount /dev/sdb5 /mnt/temp

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done

sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf

sudo chroot /mnt/temp
```
At this point your terminal prompt should become root@ubuntu, though yours may become root@this

Please report any errors.  before proceeding further.

In order to confirm an internet connection please run ```
apt-get update
``` A lot of lines of text should scroll by quickly. At the end your root prompt should return. If there are any error messages just before the end it is important to stop and say so.

More to follow

---

### Post by mmcl26554 on 2013-09-17
so far no problems

---

### Post by mmcl26554 on 2013-09-17
While waiting I installed a new cmos battery in my HP desktop, the old one was dead!  HaHa!  I wonder why we haven't moved on from battery backup?

---

### Post by Quackers on 2013-09-17
Ok same again please - now we're going to completely remove and re-install it
```
apt-get purge grub grub-pc grub-common
```
This will give you a warning that if you continue your system will become unbootable. That's why we tested the internet connection just now.
Tab to "OK" and press enter.

Now we'll re-install grub and its packages. ```
apt-get install grub-common grub-pc
```

This will happen:-

    You will be given the opportunity to add extra kernel options to the kernel line. If you don't know, you probably don't need them ; TAB to highlight "<OK>" and press ENTER.
    Read the installation notes. TAB to "<OK>" to continue.
    When presented with the device option, use the UP/DN keys to select the correct drive YOURS should be sdb.
        Make sure the installation drive [*] /dev/sdb has an asterisk next to it. If it doesn't, highlight sdb and press the SPACE bar to select it. No other drive should have one!
        Do not select a partition ( example: [ ] /dev/sda5 , etc).
    TAB to "<OK>" and press ENTER. When it has finishing the installation, you should have Grub 2 installed.

When it finishes (without errors) run ```
update-grub
```
when you should see your Windows Vista loader picked up - then
```
exit
```
your terminal prompt should now be back to this@this
run ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```

Then you can close the terminal and shutdown the computer.
Take out your sd card and turn on the computer again.
Go into bios or press F10 if that's how you choose the boot device and select the Ubuntu (60GB) drive to boot from.
You should get a grub menu with both systems listed. 
Try to boot Ubuntu first then reboot and try the Windows entry.

Good luck!

Edited second command

---

### Post by mmcl26554 on 2013-09-17
The second instruction is the same as the first and I got the following response:

```
root@this:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
Package grub-common is not installed, so not removed
Package grub-pc is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
root@this:/# 


```

---

### Post by Quackers on 2013-09-17
I edited realising I made a mistake. Sorry!

---

### Post by mmcl26554 on 2013-09-17
oops my errore now its ok

---

### Post by mmcl26554 on 2013-09-17
> **Quackers said:**
> Ok same again please - now we're going to completely remove and re-install it
```
apt-get purge grub grub-pc grub-common
```
This will give you a warning that if you continue your system will become unbootable. That's why we tested the internet connection just now.
Tab to "OK" and press enter.

Now we'll re-install grub and its packages. ```
apt-get install grub-common grub-pc
```

This will happen:-

    You will be given the opportunity to add extra kernel options to the kernel line. If you don't know, you probably don't need them ; TAB to highlight "<OK>" and press ENTER.
    Read the installation notes. TAB to "<OK>" to continue.
    When presented with the device option, use the UP/DN keys to select the correct drive YOURS should be sdb.
        Make sure the installation drive
[*] /dev/sdb has an asterisk next to it. If it doesn't, highlight sdb and press the SPACE bar to select it. No other drive should have one!
        Do not select a partition ( example: [ ] /dev/sda5 , etc).
    TAB to "<OK>" and press ENTER. When it has finishing the installation, you should have Grub 2 installed.

When it finishes (without errors) run ```
update-grub
```
when you should see your Windows Vista loader picked up - then
```
exit
```
your terminal prompt should now be back to this@this
run ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```

Then you can close the terminal and shutdown the computer.
Take out your sd card and turn on the computer again.
Go into bios or press F10 if that's how you choose the boot device and select the Ubuntu (60GB) drive to boot from.
You should get a grub menu with both systems listed. 
Try to boot Ubuntu first then reboot and try the Windows entry.

Good luck!

Edited second command


What is this?

[HTML]                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; You chose not to install GRUB to any devices. If you continue, the boot   &#9474;  
 &#9474; loader may not be properly configured, and when this computer next        &#9474;  
 &#9474; starts up it will use whatever was previously in the boot sector. If      &#9474;  
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474;  
 &#9474; unable to load modules or handle the current configuration file.          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you are already using a different boot loader and want to carry on     &#9474;  
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474;  
 &#9474; boot loader, then you should continue anyway. Otherwise, you should       &#9474;  
 &#9474; install GRUB somewhere.                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Continue without installing GRUB?                                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                            
[/HTML]

---

### Post by Quackers on 2013-09-17
Answer No

You missed this step it seems

When presented with the device option, use the UP/DN keys to select the correct drive YOURS should be sdb.
Make sure the installation drive[*] /dev/sdb has an asterisk next to it. If it doesn't, highlight sdb and press the SPACE bar to select it. No other drive should have one!
Do not select a partition ( example: [ ] /dev/sda5 , etc).

---

### Post by mmcl26554 on 2013-09-17
OK now the moment of truth, the re boot cross your fingers

---

### Post by Quackers on 2013-09-17
They're crossed!

---

### Post by mmcl26554 on 2013-09-17
sorry went to vista,  darn!

---

### Post by Quackers on 2013-09-17
F10 key?

---

### Post by mmcl26554 on 2013-09-17
yes and selected the 60 gb drive with ubuntu

---

### Post by Quackers on 2013-09-17
and?

---

### Post by mmcl26554 on 2013-09-17
here is the fdisk -l if you want

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x652868aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08673c5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   105090774    52545356    7  HPFS/NTFS/exFAT
/dev/sdb2       105091070   117209087     6059009    5  Extended
/dev/sdb5   *   105091072   113037311     3973120   83  Linux
/dev/sdb6       113039360   117209087     2084864   82  Linux swap / Solaris

Disk /dev/sdc: 3965 MB, 3965190144 bytes
255 heads, 63 sectors/track, 482 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00004a82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        1985     7744510     3871263    c  W95 FAT32 (LBA)
this@this:~$ 


```

---

### Post by Quackers on 2013-09-17
Ubuntu didn't boot? You're back in Live desktop?

---

### Post by mmcl26554 on 2013-09-17
it went to the windows boot where I select vista or vista home premium and I stopped it there because I knew there was no grub menue

---

### Post by mmcl26554 on 2013-09-17
Oh I rebooted with USB

---

### Post by Quackers on 2013-09-17
You seem to be booting the wrong hard drive
There is no Vista on the 60GB hard drive

---

### Post by mmcl26554 on 2013-09-17
correct but the bios is set to the ubuntu, I have an Idea, I'm going to switch physical positions and there fore connections and see what happens

---

### Post by Quackers on 2013-09-17
Ok, worth a try.

---

### Post by mmcl26554 on 2013-09-17
No joy!  What its doing apparently is looking for a windows boot and if it finds it switching to that drive

---

### Post by mmcl26554 on 2013-09-17
If I remove the vista drive should it boot on the Ubuntu drive alone?

---

### Post by Quackers on 2013-09-17
Yes if it's looking at the right drive.
Maybe your bios is a bit messed up and needs resetting to default values. They can do that.
Then you can go back in and change the boot order to your choice.

---

### Post by mmcl26554 on 2013-09-17
That didn't work either!

---

### Post by Quackers on 2013-09-17
What happens when you disconnect the Vista drive? Anything?

---

### Post by mmcl26554 on 2013-09-17
Well I'm going to try to run the boot repair disk with the Ubuntu drive in only and see if I can boot Ubuntu alone, then put the windows drive in and see if I can select either and boot , what do you think?

---

### Post by Quackers on 2013-09-17
Definitely worth a try, though that's pretty much what we've just done in the terminal.
Though it has to be said that the vista drive was connected then.

---

### Post by mmcl26554 on 2013-09-17
Well if you want to hit the sack, I'll take it from here and post the results.  I'll look for your response tomorrow, we get up about 10 AM, you know retired every day is vacation.
Michael

---

### Post by mmcl26554 on 2013-09-17
Maybe my only solution is WUBI here?

---

### Post by Quackers on 2013-09-17
I'll be around for a short time but I'll definitely look in tomorrow.
Best of luck to you!

---

### Post by mmcl26554 on 2013-09-17
good night!!

---

### Post by Quackers on 2013-09-17
No need for wubi.
It's sortable I'm sure :-)
Not sure how though.

---

### Post by Quackers on 2013-09-17
You've changed /etc/default/grub file to make Vista the default boot. Change it to 0 without "" round it. That's a zero not an o. That may help :D
```
================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Windows Vista (loader) (on /dev/sda1)"
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
This installed-session is not EFI-compatible.
SecureBoot disabled.
```

---

### Post by Quackers on 2013-09-17
Actually forget that as you've now got a new /etc/default/grub since we re-installed it.
It's late :-)

---

### Post by mmcl26554 on 2013-09-17
Well I reinstalled Ubuntu with only it's drive in the computer and it will boot albeit rather slowly, I did install the vista drive but didn't try the boot as te cats were wanted to be fed.   I'll try that tomorrow.

Michael

---

### Post by Quackers on 2013-09-18
Ok so you've got Ubuntu booting of its own drive and we had Windows booting off its own drive so if you now re-connect the Windows drive and boot into Ubuntu and run ```
sudo update-grub
``` and you should see the Windows loader recognised.
Then you can reboot and from the grub menu you should be able to boot Vista. :-)
In theory!

---

### Post by mmcl26554 on 2013-09-18
Ok I'll be back at the computer in about 1/2 hour and run the update Grub from inside Ubuntu and see what happens.   Or should I run Boot Repair or either?
Good, well afternoon to you!
Michael

---

### Post by Bucky Ball on 2013-09-18
*Thread moved to **Installation & Upgrades***

Not sure why this was posted in ***Absolute Beginners.*** It decreases your chances of help rather than enhances. ;)

---

### Post by Quackers on 2013-09-18
Just running sudo update-grub should do it. I'd leave Boot-Repair for the moment.
And good morning to you! ):P

---

### Post by mmcl26554 on 2013-09-18
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades***

Not sure why this was posted in ***Absolute Beginners.*** It decreases your chances of help rather than enhances. ;)


Hi Bucky,

Well maybe I underestimated my skills,  I regard myself as a beginner, however, I had help from a member of this forum in resolving a network drive issue and his tutelage must have been more effective than I thought.   I am certainly more confident in working with Ubuntu Linux.  About 7 years ago I had a go at RedHat Linux and never could quite catch on to it.   I purchased a lot of books on Linux but always seemed to get lost with the commands. Today however, I seem to understand them better. The forums didn't help either because the language was just something that would lose me.  Now, however, in addition to Ubuntu being easier to work with this forum speaks my language and the participants are not afraid to take you by the hand and lead.   So maybe I have advanced from "Absolute beginner" to just "Beginner" or "Advanced Beginner". I'll try other forums next issue and see what happens.  But thanks for the concern, this is really a community who looks out for each other.   Wouldn't it be nice is our country was like this!

Michael

---

### Post by mmcl26554 on 2013-09-18
Well Quacker:
I get the Grub menu with Ubuntu and Windows on it but Vista like before just flashes the (-) cursor right now I am waiting for the menu to come up again and see if Ubuntu will boot from it, I know Vista will boot if I select it's drive but not from the Grub menu.  Now Ubuntu does boot from it but I get a brief error message that the Swap file is either not ready or missing and then it boots.  I did not specify one way or the other for a swap file when i reinstalled Ubuntu but either it didn't make one or there is something wrong with the install because it takes maybe 5 minutes for the menu to come up and maybe 3 or more minutes for Ubuntu to get to the login screen.  I'll send you fdisk -l from the other computer as soon as I get logged in.

---

### Post by mmcl26554 on 2013-09-18
OK here is fdisk -l:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b296

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   113037311    56517632   83  Linux
/dev/sda2       113039358   117209087     2084865    5  Extended
/dev/sda5       113039360   117209087     2084864   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x652868aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT
michael@GW-1:~$ 


```

---

### Post by Quackers on 2013-09-18
I don't know why that should be I'm afraid. I can't think of anything else to try.
At least both systems are now bootable via the F10 device option. That's a start!
Be aware though that running Boot-Repair may over-write the MBR on your Windows drive with grub, which would stop Windows booting.

---

### Post by mmcl26554 on 2013-09-18
That doesn't bother me as I know how to get Vist up and running again.  If you think there is a chance it might help I'll run it.   I also did hear back from the boot repair people but their first instructions we have already done so I am waiting for the second round.
Michael

---

### Post by mmcl26554 on 2013-09-18
why does it take so long for Ubuntu to boot up with this installation as apposed to before?   Same drive Same computer?

---

### Post by Bucky Ball on 2013-09-18
> **mmcl26554 said:**
> ... participants are not afraid to take you by the hand and lead.

Especially if you have a go, have a try at solving it first (and provide what you've done so far in the first post), they will be gentle on you. You'll keep learning by branching out and you'll increase your chances of help by being here (as this is where the 'install gurus' hang, those you'll learn the most about it from).

If you let helpers know your level they'll take that in to account and if there's anything you don't understand, just ask. ;)


* What a marathon effort! 108 posts in 1 day!!!

---

### Post by Quackers on 2013-09-18
If you're happy about the possibility of repairing the Windows drive MBR then go for it. I really don't know whether it will help to be honest. It didn't before but I'm not sure there's anything to lose. 
As far as I can see there is no reason why Vista won't boot from grub (though a new output of the bootscript might shed some light since the re-install).

With regard to the boot time of the re-installed system I have no explanation other than the drive might be suspect (if it's an old one). That would be my only guess.

---

### Post by mmcl26554 on 2013-09-18
> **Bucky Ball said:**
> Especially if you have a go, have a try at solving it first (and provide what you've done so far in the first post), they will be gentle on you. You'll keep learning by branching out and you'll increase your chances of help by being here (as this is where the 'install gurus' hang, those you'll learn the most about it from).

If you let helpers know your level they'll take that in to account and if there's anything you don't understand, just ask. ;)


* What a marathon effort! 108 posts in 1 day!!!
BTW I know about "Bucky Balls"!

Do you think it would be better for me to start a new thread or move this one to the higher level formu?   I certainly don't want to insult Quacker as with 11 pages of posts she/he has certainly tried hard.   And I am most appreciative!
Michael

---

### Post by oldfred on 2013-09-18
Are both drives SATA or both PATA or mixed?

Sometimes that can cause BIOS to not recognize hd0 switch that grub does to make Windows think it booted from hd0. Boot drive is always hd0 and Windows usually needs to see that it is hd0 if installed that way. Grub does a map device to make Windows think it is hd0.

If BIOS does not work correct it can be just a BIOS setting like AHCI, not IDE unless drives are really old and IDE with jumpers not newer IDE cable select. Are settings on drives correct if older IDE?

---

### Post by mmcl26554 on 2013-09-18
Hi Old Fred!
Both are SATA and both are maybe 10 years old although the  one with Ubuntu is a bit newer.  Both pass testing and don't seem to  have any problems.

---

### Post by mmcl26554 on 2013-09-18
I am thinking of going back to square one and reinstalling 12.04 on the same hard drive. but first Gparted the drive and delete all partitions I don't know if I have to format it but I will try first to not and let Ubuntu install do it.  Should I select install along side Vista or something else and specifify the drive and swap files to make?  
Suggestions please.
Michael

---

### Post by UltimateCat on 2013-09-18
Ok, looking at your partitions

This is your Windows Vista partition-

> 
/dev/sdb1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT


And the other:
> /dev/sda1 is your Ubuntu Linux partition


Your /dev/sda1 (Ubuntu) is the 60 GB SSD
And your /dev/sdb is the 320 GB SSD according to the description from the output of "fdisk -l"

It looks like a partition is missing in your Windows 7 /dev/sdb1-
When my GNU GRUB menu boots I see 2 partitions for my Windows XP-
Mine looks something like this:

> Ubuntu with Linux 3.2.6-32 generic partition
"      " (recovery mode) portion
Memory   (memtest86+) portion
Than my HPFS/NTFS/exFAT Windows XP partition
The Windows XP Pro partition on dev/sda1 partition
And a Windows RECOVERY as well


I could be mistaken but it looks like your missing one or more of your Microsoft partitions:-

---

### Post by oldfred on 2013-09-18
If drives are SATA and 10 years old are they SATA2? I converted to SATA about 6 years ago and it was relatively new. 
One user had an old Dell with one IDE port that was only for booting and a SATA1 port for data. Could never configure SATA1 drive as boot.

I always prefer manual partitioning. And suggest using Vista to resize its own partition and reboot as Windows has to run chkdsk and make repairs to recognize its new size before starting Ubuntu install.

Did you try as an experiment installing grub2 onto the Vista drive so you boot Ubuntu from that. I would make sure Windows is seen as sda and Ubuntu as sdb. Port order as plugged in can make a difference.

It looks like Quackers led you thru just about every other repair alternative.

---

### Post by UltimateCat on 2013-09-18
> Should I select install along side Vista or something else and specifify the drive and swap files to make?  


If you want to install alongside Windows Vista you can: but you have to shrink the Windows parition first.
Than install Ubuntu to the portion of the drive that in shown as 'unallocated space'
Click on the unallocated space and create a 20 GB partion (/ EXT 4 journaling file system partition for Ubuntu)
(set the mount point at the beginning)
Than click on the rest of the free space and create a 1 to 2 GB "swap"

Otherwise you should disconnect the SSD that has your Vista on it and that way the Ubuntu Installer will only see the one drive to install to that is plugged in-

AFAIK you can not modify or change a parition of an Operating System while it is mounted,up and running--(at least that's been my experience)

If you want to use  to re-partition you should use a LIVE CD OF G-Parted-- Which is suggested here:
**Using Linux to Resize**
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by UltimateCat on 2013-09-18
I'm with you Oldfred; I prefer manual partitioning as well.

---

### Post by mmcl26554 on 2013-09-18
U Cat and OldFred
Remember I have 2 drives one for Vista (only partition on that drive full of Vista),  The other drive (60GB) Has 2 partitions one for Ubuntu and One for Swap.  I'm going to wipe the 60GB drive and let Ubuntu install install the partitions but manually.  If that doesn't give me a good booting system then I'll do one of the following:
Install with WUBI
OR
remove the Vista drive and install Ubuntu on the 60 GB drive and boot either from the F10 bios boot menu.   I'll keep you posted on what happens.
Michael

---

### Post by mmcl26554 on 2013-09-18
Here is the progress so far. Installation complete on the 60GB drive selecting "something else" and manually setting up the 2 partitions one for Ubunto and swap.  When I select the drive Ubuntu is on after maybe a 3 minute waite the grub menu comes up and it also contains Vista but Vista won't boot.  However Ubuntu will boot from this menu.  But why does it seem to take so long?   So right now I have Ubuntu and Vista on two separate drives. and they both will  boot. I don't have to select a drive for Vista it will come up if I do nothing, thats ok for me.  I may run boot repair and just get some data off it.  If I decide to tru WUBI can I install Ubuntu on the seperate drive instead of in Vista?
Michael

---

### Post by mmcl26554 on 2013-09-18
Well boot repair did nothing.  I did not let it write to the Vista drive.   So vista boots by default and if I select the sda drive then after the long wait the grub menu comes but it won't boot Vista.  However, ubuntu will boot from the menu.   So plan "Z" is to try WUBI and put Ubuntu on the drive it is on now, if I can.  I'd be happy with the current arrangement if Ubuntu wasn't so poky booting.  So that's for a different post.

Michael

---

### Post by oldfred on 2013-09-18
If you want to look at why boot is so long, you need to review log files and look at the entires with large differences in the timestamps.

gksu gedit /var/log/dmesg

This was 2 sec on my boot, so it was one of the longer with my SSD. You may see many seconds or minutes (over 60. deltas).
[    3.737030] usbhid: USB HID core driver
[    5.483186] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)

---

### Post by mmcl26554 on 2013-10-01
Oldfred,
I timed the boot and it took 56 seconds to get to the Grub boot menu, then 2:27 to get to the desktop.  I suppose that is not long unless you are waiting for something to happen.  You know the watched pot syndrom!
Anyway here is the output from the dmesg log  (FYI for some reason gksu is not installed on this 13.10 verson but sudo worked ok)
I'm still having the problem where Grub won't boot Vista.  Even with assistance from the "Boot Repair" people it still just hangs.   So I'm left with 2 options.   Use the Bios menu to select the drive to boot from or install WUBI.  Right now I have Ubuntu 13.10 installed in it's own drive and that works but boot up seems slow. 
Michael

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-8-generic (buildd@batsu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu3) ) #15-Ubuntu SMP Fri Sep 20 04:11:16 UTC 2013 (Ubuntu 3.11.0-8.15-generic 3.11.1)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007f5bcfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f5bd000-0x000000007f5c9fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007f5ca000-0x000000007f655fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f656000-0x000000007f6e7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007f6e8000-0x000000007f6ebfff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f6ec000-0x000000007f6f0fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f6f1000-0x000000007f6f1fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f6f2000-0x000000007f6fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000007f6ff000-0x000000007f6fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007f700000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gateway                          GZ7112                          /DGM965RA, BIOS RA96510J.15A.0092.2007.1214.1014 12/14/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7f700 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07F800000 mask FFF800000 uncachable
[    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000fe200-0x000fe20f] mapped at [c00fe200]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c008b000] 8b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b5f000, 0x01b5ffff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35fa4000-0x36fc9fff]
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 GATEWA)
[    0.000000] ACPI: RSDT 7f6fd038 00050 (v01 GATEWA SYSTEM   0000005C      01000013)
[    0.000000] ACPI: FACP 7f6fc000 000F4 (v02 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: DSDT 7f6f7000 044A4 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: FACS 7f6a2000 00040
[    0.000000] ACPI: APIC 7f6f6000 00078 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: WDDT 7f6f5000 00040 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: MCFG 7f6f4000 0003C (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: ASF! 7f6f3000 000A6 (v32 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: SLIC 7f6f2000 00176 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT 7f6f0000 001BC (v01 GATEWA    CpuPm 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT 7f6ef000 001B7 (v01 GATEWA  Cpu0Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT 7f6ee000 001B7 (v01 GATEWA  Cpu1Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT 7f6ed000 001B7 (v01 GATEWA  Cpu2Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT 7f6ec000 001B7 (v01 GATEWA  Cpu3Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1147MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b60000, 0x01b60fff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7f6fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0008efff]
[    0.000000]   node   0: [mem 0x00100000-0x7f5bcfff]
[    0.000000]   node   0: [mem 0x7f5ca000-0x7f655fff]
[    0.000000]   node   0: [mem 0x7f6e8000-0x7f6ebfff]
[    0.000000]   node   0: [mem 0x7f6f1000-0x7f6f1fff]
[    0.000000]   node   0: [mem 0x7f6ff000-0x7f6fffff]
[    0.000000] On node 0 totalpages: 521693
[    0.000000] free_area_init_node: node 0, pgdat c195d340, node_mem_map f4fb4020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3982 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2295 pages used for memmap
[    0.000000]   HighMem zone: 293457 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0008f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0x80000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bba000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519909
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-8-generic root=UUID=518066c3-0985-4c85-ae80-c5e3a276a090 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4175864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007f700)
[    0.000000] Memory: 2037040K/2086772K available (6399K kernel code, 615K rwdata, 2668K rodata, 880K init, 976K bss, 49732K reserved, 1173828K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1977000 - 0xc1a53000   ( 880 kB)
[    0.000000]       .data : 0xc1640024 - 0xc1976d80   (3291 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1640024   (6400 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f7008000 soft=f700a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1833.354 MHz processor
[    0.008002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3666.70 BogoMIPS (lpj=7333416)
[    0.008007] pid_max: default: 32768 minimum: 301
[    0.008048] Security Framework initialized
[    0.008072] AppArmor: AppArmor initialized
[    0.008074] Yama: becoming mindful.
[    0.008136] Mount-cache hash table entries: 512
[    0.008446] Initializing cgroup subsys memory
[    0.008461] Initializing cgroup subsys devices
[    0.008464] Initializing cgroup subsys freezer
[    0.008467] Initializing cgroup subsys blkio
[    0.008470] Initializing cgroup subsys perf_event
[    0.008473] Initializing cgroup subsys hugetlb
[    0.008508] CPU: Physical Processor ID: 0
[    0.008510] CPU: Processor Core ID: 0
[    0.008514] mce: CPU supports 6 MCE banks
[    0.008524] CPU0: Thermal monitoring enabled (TM2)
[    0.008540] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.008540] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.008540] tlb_flushall_shift: -1
[    0.008887] Freeing SMP alternatives memory: 28K (c1a53000 - c1a5a000)
[    0.013012] ACPI: Core revision 20130517
[    0.017582] ACPI: All ACPI Tables successfully acquired
[    0.019114] ftrace: allocating 27240 entries in 54 pages
[    0.028127] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032237] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071934] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz (fam: 06, model: 0f, stepping: 0d)
[    0.072000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.072000] perf_event_intel: PEBS disabled due to CPU errata
[    0.072000] ... version:                2
[    0.072000] ... bit width:              40
[    0.072000] ... generic registers:      2
[    0.072000] ... value mask:             000000ffffffffff
[    0.072000] ... max period:             000000007fffffff
[    0.072000] ... fixed-purpose events:   3
[    0.072000] ... event mask:             0000000700000003
[    0.072000] CPU 1 irqstacks, hard=f70e4000 soft=f70e6000
[    0.012000] Initializing CPU#1
[    0.072000] smpboot: Booting Node   0, Processors  #1
[    0.083388] Brought up 2 CPUs
[    0.083393] smpboot: Total of 2 processors activated (7333.41 BogoMIPS)
[    0.083513] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088120] devtmpfs: initialized
[    0.088336] EVM: security.selinux
[    0.088338] EVM: security.SMACK64
[    0.088340] EVM: security.capability
[    0.088361] PM: Registering ACPI NVS region [mem 0x7f656000-0x7f6e7fff] (598016 bytes)
[    0.089610] regulator-dummy: no parameters
[    0.089646] RTC time: 15:43:13, date: 10/01/13
[    0.089704] NET: Registered protocol family 16
[    0.089919] EISA bus registered
[    0.090024] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.090028] ACPI: bus type PCI registered
[    0.090032] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.090116] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.090120] PCI: not using MMCONFIG
[    0.090120] PCI: Using configuration type 1 for base access
[    0.090120] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.090120] mtrr: probably your BIOS does not setup all CPUs.
[    0.090120] mtrr: corrected configuration.
[    0.092085] bio: create slab <bio-0> at 0
[    0.092115] ACPI: Added _OSI(Module Device)
[    0.092119] ACPI: Added _OSI(Processor Device)
[    0.092122] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.092124] ACPI: Added _OSI(Processor Aggregator Device)
[    0.092225] ACPI: EC: Look up EC in DSDT
[    0.095826] ACPI: Interpreter enabled
[    0.095854] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.095861] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.095880] ACPI: (supports S0 S3 S4 S5)
[    0.095882] ACPI: Using IOAPIC for interrupt routing
[    0.095901] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.096099] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in ACPI motherboard resources
[    0.096101] PCI: Using MMCONFIG for extended config space
[    0.096121] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.096250] ACPI: No dock devices found.
[    0.099329] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.102100] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.102135] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.103414] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.105181] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.105185] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.105189] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.105192] acpi PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff] (ignored)
[    0.105196] acpi PNP0A03:00: host bridge window [mem 0xf8000000-0xfeafffff] (ignored)
[    0.105199] acpi PNP0A03:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
[    0.105202] PCI: root bus 00: using default resources
[    0.105206] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    0.105397] PCI host bridge to bus 0000:00
[    0.105402] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.105405] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.105409] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.105423] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.105576] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.105596] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x900fffff 64bit]
[    0.105609] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.105617] pci 0000:00:02.0: reg 0x20: [io  0x1130-0x1137]
[    0.105763] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.105780] pci 0000:00:02.1: reg 0x10: [mem 0x90100000-0x901fffff 64bit]
[    0.105966] pci 0000:00:19.0: [8086:104d] type 00 class 0x020000
[    0.105988] pci 0000:00:19.0: reg 0x10: [mem 0x90400000-0x9041ffff]
[    0.106000] pci 0000:00:19.0: reg 0x14: [mem 0x90424000-0x90424fff]
[    0.106011] pci 0000:00:19.0: reg 0x18: [io  0x10e0-0x10ff]
[    0.106086] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.106166] pci 0000:00:19.0: System wakeup disabled by ACPI
[    0.106214] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.106265] pci 0000:00:1a.0: reg 0x20: [io  0x10c0-0x10df]
[    0.106389] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.106438] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.106489] pci 0000:00:1a.1: reg 0x20: [io  0x10a0-0x10bf]
[    0.106611] pci 0000:00:1a.1: System wakeup disabled by ACPI
[    0.106671] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.106695] pci 0000:00:1a.7: reg 0x10: [mem 0x90425c00-0x90425fff]
[    0.106797] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.106904] pci 0000:00:1a.7: System wakeup disabled by ACPI
[    0.106962] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.106983] pci 0000:00:1b.0: reg 0x10: [mem 0x90420000-0x90423fff 64bit]
[    0.107071] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.107178] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.107231] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.107321] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.107407] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.107457] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.107548] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.107634] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.107685] pci 0000:00:1c.2: [8086:2843] type 01 class 0x060400
[    0.107776] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.107861] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.107913] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.108004] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.108089] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.108139] pci 0000:00:1c.4: [8086:2847] type 01 class 0x060400
[    0.108230] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.108315] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.108366] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.108417] pci 0000:00:1d.0: reg 0x20: [io  0x1080-0x109f]
[    0.108539] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.108588] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.108639] pci 0000:00:1d.1: reg 0x20: [io  0x1060-0x107f]
[    0.108761] pci 0000:00:1d.1: System wakeup disabled by ACPI
[    0.108810] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.108861] pci 0000:00:1d.2: reg 0x20: [io  0x1040-0x105f]
[    0.108982] pci 0000:00:1d.2: System wakeup disabled by ACPI
[    0.109043] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.109067] pci 0000:00:1d.7: reg 0x10: [mem 0x90425800-0x90425bff]
[    0.109169] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.109275] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.109328] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.109463] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.109515] pci 0000:00:1f.0: [8086:2811] type 00 class 0x060100
[    0.109612] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.109624] pci 0000:00:1f.0: address space collision: [io  0x0400-0x047f] conflicts with ACPI CPU throttle [??? 0x00000410-0x00000415 flags 0x80000000]
[    0.109631] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.109636] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.109640] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0810 (mask 007f)
[    0.109786] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.109802] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.109814] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.109826] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.109838] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.109850] pci 0000:00:1f.1: reg 0x20: [io  0x1100-0x110f]
[    0.109991] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
[    0.110014] pci 0000:00:1f.2: reg 0x10: [io  0x1118-0x111f]
[    0.110025] pci 0000:00:1f.2: reg 0x14: [io  0x113c-0x113f]
[    0.110035] pci 0000:00:1f.2: reg 0x18: [io  0x1110-0x1117]
[    0.110046] pci 0000:00:1f.2: reg 0x1c: [io  0x1138-0x113b]
[    0.110057] pci 0000:00:1f.2: reg 0x20: [io  0x1020-0x103f]
[    0.110068] pci 0000:00:1f.2: reg 0x24: [mem 0x90425000-0x904257ff]
[    0.110122] pci 0000:00:1f.2: PME# supported from D3hot
[    0.110243] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.110259] pci 0000:00:1f.3: reg 0x10: [mem 0x90426000-0x904260ff]
[    0.110294] pci 0000:00:1f.3: reg 0x20: [io  0x1000-0x101f]
[    0.110491] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.110499] pci 0000:00:1c.0:   bridge window [mem 0x90500000-0x905fffff]
[    0.110576] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.110584] pci 0000:00:1c.1:   bridge window [mem 0x90600000-0x906fffff]
[    0.110698] pci 0000:03:00.0: [8086:4229] type 00 class 0x028000
[    0.110736] pci 0000:03:00.0: reg 0x10: [mem 0x90300000-0x90301fff 64bit]
[    0.110916] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.120034] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.120047] pci 0000:00:1c.2:   bridge window [mem 0x90300000-0x903fffff]
[    0.120166] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.120178] pci 0000:00:1c.3:   bridge window [mem 0x90700000-0x907fffff]
[    0.120297] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.120305] pci 0000:00:1c.4:   bridge window [mem 0x90800000-0x908fffff]
[    0.120374] pci 0000:06:03.0: [104c:8023] type 00 class 0x0c0010
[    0.120397] pci 0000:06:03.0: reg 0x10: [mem 0x90204000-0x902047ff]
[    0.120411] pci 0000:06:03.0: reg 0x14: [mem 0x90200000-0x90203fff]
[    0.120497] pci 0000:06:03.0: supports D1 D2
[    0.120500] pci 0000:06:03.0: PME# supported from D0 D1 D2 D3hot
[    0.120592] pci 0000:00:1e.0: PCI bridge to [bus 06] (subtractive decode)
[    0.120600] pci 0000:00:1e.0:   bridge window [mem 0x90200000-0x902fffff]
[    0.120608] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.120611] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.120644] pci_bus 0000:00: on NUMA node 0
[    0.120648] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.120651] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.120769] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12)
[    0.120868] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.120966] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12)
[    0.121062] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[    0.121157] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
[    0.121253] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.121348] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.121443] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.122058] ACPI: Enabled 4 GPEs in block 00 to 1F
[    0.122068] ACPI: \_SB_.PCI0: notify handler is installed
[    0.122124] Found 1 acpi root devices
[    0.124018] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.124028] vgaarb: loaded
[    0.124030] vgaarb: bridge control possible 0000:00:02.0
[    0.124308] SCSI subsystem initialized
[    0.124312] ACPI: bus type ATA registered
[    0.124332] libata version 3.00 loaded.
[    0.124332] ACPI: bus type USB registered
[    0.124332] usbcore: registered new interface driver usbfs
[    0.124332] usbcore: registered new interface driver hub
[    0.124332] usbcore: registered new device driver usb
[    0.124332] PCI: Using ACPI for IRQ routing
[    0.129902] PCI: pci_cache_line_size set to 64 bytes
[    0.129979] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.129983] e820: reserve RAM buffer [mem 0x7f5bd000-0x7fffffff]
[    0.129986] e820: reserve RAM buffer [mem 0x7f656000-0x7fffffff]
[    0.129989] e820: reserve RAM buffer [mem 0x7f6ec000-0x7fffffff]
[    0.129992] e820: reserve RAM buffer [mem 0x7f6f2000-0x7fffffff]
[    0.129995] e820: reserve RAM buffer [mem 0x7f700000-0x7fffffff]
[    0.130122] NetLabel: Initializing
[    0.130125] NetLabel:  domain hash size = 128
[    0.130127] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.130141] NetLabel:  unlabeled traffic allowed by default
[    0.130157] hpet clockevent registered
[    0.130157] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.130157] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.130157] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.132023] Switched to clocksource hpet
[    0.142532] AppArmor: AppArmor Filesystem Enabled
[    0.142583] pnp: PnP ACPI init
[    0.142608] ACPI: bus type PNP registered
[    0.142736] system 00:00: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.142741] system 00:00: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.142745] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.142749] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.142753] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.142757] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.142760] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.142768] system 00:00: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.142772] system 00:00: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.142776] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.142782] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.142980] pnp 00:01: [dma 4]
[    0.143010] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.143065] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.143114] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.143156] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.143224] system 00:05: [io  0x0500-0x053f] has been reserved
[    0.143228] system 00:05: [io  0x0400-0x047f] could not be reserved
[    0.143231] system 00:05: [io  0x0680-0x06ff] has been reserved
[    0.143236] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.143344] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.143460] pnp 00:07: Plug and Play ACPI device, IDs WEC1022 (active)
[    0.143586] pnp 00:08: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.143681] pnp: PnP ACPI: found 9 devices
[    0.143684] ACPI: bus type PNP unregistered
[    0.143689] PnPBIOS: Disabled by ACPI PNP
[    0.180923] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.180930] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.180942] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.180946] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.180957] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.180961] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.180975] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.180979] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.180990] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.180994] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000
[    0.181010] pci 0000:00:1f.0: BAR 13: [io  0x0400-0x047f] has bogus alignment
[    0.181016] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.181020] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.181023] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.181027] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.181030] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.181034] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.181037] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.181040] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.181043] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.181047] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.181055] pci 0000:00:1c.0: BAR 15: assigned [mem 0x90900000-0x90afffff 64bit pref]
[    0.181060] pci 0000:00:1c.1: BAR 15: assigned [mem 0x90b00000-0x90cfffff 64bit pref]
[    0.181065] pci 0000:00:1c.2: BAR 15: assigned [mem 0x90d00000-0x90efffff 64bit pref]
[    0.181070] pci 0000:00:1c.3: BAR 15: assigned [mem 0x90f00000-0x910fffff 64bit pref]
[    0.181075] pci 0000:00:1c.4: BAR 15: assigned [mem 0x91100000-0x912fffff 64bit pref]
[    0.181079] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.181084] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.181088] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.181092] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.181097] pci 0000:00:1c.4: BAR 13: assigned [io  0x6000-0x6fff]
[    0.181102] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.181107] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.181113] pci 0000:00:1c.0:   bridge window [mem 0x90500000-0x905fffff]
[    0.181119] pci 0000:00:1c.0:   bridge window [mem 0x90900000-0x90afffff 64bit pref]
[    0.181126] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.181130] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.181137] pci 0000:00:1c.1:   bridge window [mem 0x90600000-0x906fffff]
[    0.181142] pci 0000:00:1c.1:   bridge window [mem 0x90b00000-0x90cfffff 64bit pref]
[    0.181150] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.181154] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.181160] pci 0000:00:1c.2:   bridge window [mem 0x90300000-0x903fffff]
[    0.181166] pci 0000:00:1c.2:   bridge window [mem 0x90d00000-0x90efffff 64bit pref]
[    0.181173] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.181177] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.181184] pci 0000:00:1c.3:   bridge window [mem 0x90700000-0x907fffff]
[    0.181189] pci 0000:00:1c.3:   bridge window [mem 0x90f00000-0x910fffff 64bit pref]
[    0.181197] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.181201] pci 0000:00:1c.4:   bridge window [io  0x6000-0x6fff]
[    0.181207] pci 0000:00:1c.4:   bridge window [mem 0x90800000-0x908fffff]
[    0.181213] pci 0000:00:1c.4:   bridge window [mem 0x91100000-0x912fffff 64bit pref]
[    0.181220] pci 0000:00:1e.0: PCI bridge to [bus 06]
[    0.181227] pci 0000:00:1e.0:   bridge window [mem 0x90200000-0x902fffff]
[    0.182220] pci 0000:00:1e.0: setting latency timer to 64
[    0.182226] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.182229] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.182233] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.182236] pci_bus 0000:01: resource 1 [mem 0x90500000-0x905fffff]
[    0.182239] pci_bus 0000:01: resource 2 [mem 0x90900000-0x90afffff 64bit pref]
[    0.182242] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.182245] pci_bus 0000:02: resource 1 [mem 0x90600000-0x906fffff]
[    0.182248] pci_bus 0000:02: resource 2 [mem 0x90b00000-0x90cfffff 64bit pref]
[    0.182252] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.182254] pci_bus 0000:03: resource 1 [mem 0x90300000-0x903fffff]
[    0.182258] pci_bus 0000:03: resource 2 [mem 0x90d00000-0x90efffff 64bit pref]
[    0.182261] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
[    0.182264] pci_bus 0000:04: resource 1 [mem 0x90700000-0x907fffff]
[    0.182267] pci_bus 0000:04: resource 2 [mem 0x90f00000-0x910fffff 64bit pref]
[    0.182270] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.182272] pci_bus 0000:05: resource 1 [mem 0x90800000-0x908fffff]
[    0.182276] pci_bus 0000:05: resource 2 [mem 0x91100000-0x912fffff 64bit pref]
[    0.182279] pci_bus 0000:06: resource 1 [mem 0x90200000-0x902fffff]
[    0.182282] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.182285] pci_bus 0000:06: resource 5 [mem 0x00000000-0xfffffffff]
[    0.182331] NET: Registered protocol family 2
[    0.182549] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.182594] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.182633] TCP: Hash tables configured (established 8192 bind 8192)
[    0.182673] TCP: reno registered
[    0.182676] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.182689] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.182777] NET: Registered protocol family 1
[    0.182794] pci 0000:00:02.0: Boot video device
[    0.185766] PCI: CLS 64 bytes, default 64
[    0.185816] Trying to unpack rootfs image as initramfs...
[    0.605089] Freeing initrd memory: 16536K (f5fa4000 - f6fca000)
[    0.605364] Scanning for low memory corruption every 60 seconds
[    0.607302] Initialise module verification
[    0.607367] audit: initializing netlink socket (disabled)
[    0.607387] type=2000 audit(1380642193.604:1): initialized
[    0.636267] bounce pool size: 64 pages
[    0.636283] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.638207] zbud: loaded
[    0.638270] VFS: Disk quotas dquot_6.5.2
[    0.638336] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.639062] fuse init (API version 7.22)
[    0.639177] msgmni has been set to 1718
[    0.639699] Key type asymmetric registered
[    0.639703] Asymmetric key parser 'x509' registered
[    0.639753] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.639795] io scheduler noop registered
[    0.639798] io scheduler deadline registered (default)
[    0.639835] io scheduler cfq registered
[    0.640019] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.640110] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.640197] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.640281] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.640365] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.640466] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.640487] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.640593] intel_idle: does not run on family 6 model 15
[    0.640678] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.640685] ACPI: Sleep Button [SLPB]
[    0.640749] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.640753] ACPI: Power Button [PWRF]
[    0.640854] ACPI: Requesting acpi_cpufreq
[    0.642475] GHES: HEST is not enabled!
[    0.642504] isapnp: Scanning for PnP cards...
[    0.642580] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.642707] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a CIR port
[    0.642818] serial 00:07: disabled
[    0.644376] Linux agpgart interface v0.103
[    0.644499] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    0.644597] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.645159] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.645287] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    0.647155] brd: module loaded
[    0.648120] loop: module loaded
[    0.648277] ata_piix 0000:00:1f.1: version 2.13
[    0.648505] ata_piix 0000:00:1f.1: can't derive routing for PCI INT D
[    0.648548] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.648904] scsi0 : ata_piix
[    0.649315] scsi1 : ata_piix
[    0.649381] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.649384] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.649784] libphy: Fixed MDIO Bus: probed
[    0.649919] tun: Universal TUN/TAP device driver, 1.6
[    0.649921] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.649969] PPP generic driver version 2.4.2
[    0.650020] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.650022] ehci-pci: EHCI PCI platform driver
[    0.650250] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    0.650267] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.650274] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.650291] ehci-pci 0000:00:1a.7: debug port 1
[    0.654184] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.654210] ehci-pci 0000:00:1a.7: irq 18, io mem 0x90425c00
[    0.654398] ata2: port disabled--ignoring
[    0.664016] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.664041] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.664045] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.664048] usb usb1: Product: EHCI Host Controller
[    0.664051] usb usb1: Manufacturer: Linux 3.11.0-8-generic ehci_hcd
[    0.664054] usb usb1: SerialNumber: 0000:00:1a.7
[    0.664186] hub 1-0:1.0: USB hub found
[    0.664192] hub 1-0:1.0: 4 ports detected
[    0.664529] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.664543] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.664549] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.664564] ehci-pci 0000:00:1d.7: debug port 1
[    0.668464] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.668489] ehci-pci 0000:00:1d.7: irq 23, io mem 0x90425800
[    0.680017] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.680035] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.680039] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.680042] usb usb2: Product: EHCI Host Controller
[    0.680045] usb usb2: Manufacturer: Linux 3.11.0-8-generic ehci_hcd
[    0.680048] usb usb2: SerialNumber: 0000:00:1d.7
[    0.680161] hub 2-0:1.0: USB hub found
[    0.680167] hub 2-0:1.0: 6 ports detected
[    0.680340] ehci-platform: EHCI generic platform driver
[    0.680351] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.680353] ohci-platform: OHCI generic platform driver
[    0.680362] uhci_hcd: USB Universal Host Controller Interface driver
[    0.680577] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.680582] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.680588] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.680625] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000010c0
[    0.680661] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.680665] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.680668] usb usb3: Product: UHCI Host Controller
[    0.680671] usb usb3: Manufacturer: Linux 3.11.0-8-generic uhci_hcd
[    0.680673] usb usb3: SerialNumber: 0000:00:1a.0
[    0.680782] hub 3-0:1.0: USB hub found
[    0.680788] hub 3-0:1.0: 2 ports detected
[    0.681082] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.681087] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.681093] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.681133] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000010a0
[    0.681169] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.681173] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.681176] usb usb4: Product: UHCI Host Controller
[    0.681179] usb usb4: Manufacturer: Linux 3.11.0-8-generic uhci_hcd
[    0.681182] usb usb4: SerialNumber: 0000:00:1a.1
[    0.681291] hub 4-0:1.0: USB hub found
[    0.681296] hub 4-0:1.0: 2 ports detected
[    0.681588] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.681592] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.681599] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.681623] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001080
[    0.681659] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.681662] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.681665] usb usb5: Product: UHCI Host Controller
[    0.681668] usb usb5: Manufacturer: Linux 3.11.0-8-generic uhci_hcd
[    0.681671] usb usb5: SerialNumber: 0000:00:1d.0
[    0.681778] hub 5-0:1.0: USB hub found
[    0.681783] hub 5-0:1.0: 2 ports detected
[    0.682075] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.682079] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.682086] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.682122] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001060
[    0.682156] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.682160] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.682163] usb usb6: Product: UHCI Host Controller
[    0.682166] usb usb6: Manufacturer: Linux 3.11.0-8-generic uhci_hcd
[    0.682168] usb usb6: SerialNumber: 0000:00:1d.1
[    0.682278] hub 6-0:1.0: USB hub found
[    0.682283] hub 6-0:1.0: 2 ports detected
[    0.682580] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.682584] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.682593] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.682617] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001040
[    0.682651] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.682654] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.682657] usb usb7: Product: UHCI Host Controller
[    0.682660] usb usb7: Manufacturer: Linux 3.11.0-8-generic uhci_hcd
[    0.682663] usb usb7: SerialNumber: 0000:00:1d.2
[    0.682772] hub 7-0:1.0: USB hub found
[    0.682777] hub 7-0:1.0: 2 ports detected
[    0.682955] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.995707] isapnp: No Plug & Play device found
[    1.224324] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-T632A, GA00, max UDMA/33
[    1.256198] ata1.00: configured for UDMA/33
[    1.280519] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-T632A GA00 PQ: 0 ANSI: 5
[    1.304382] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.304386] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.304507] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.304571] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.604018] tsc: Refined TSC clocksource calibration: 1833.333 MHz
[    1.709053] i8042: No controller found
[    1.709197] mousedev: PS/2 mouse device common for all mice
[    1.709378] rtc_cmos 00:02: RTC can wake from S4
[    1.709517] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.709548] rtc_cmos 00:02: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.709640] device-mapper: uevent: version 1.0.3
[    1.709729] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.709758] platform eisa.0: Probing EISA bus 0
[    1.709780] platform eisa.0: EISA: Detected 0 cards
[    1.709791] cpufreq-nforce2: No nForce2 chipset.
[    1.709794] cpuidle: using governor ladder
[    1.709796] cpuidle: using governor menu
[    1.709810] ledtrig-cpu: registered to indicate activity on CPUs
[    1.709952] ashmem: initialized
[    1.710143] TCP: cubic registered
[    1.710284] NET: Registered protocol family 10
[    1.710550] NET: Registered protocol family 17
[    1.710564] Key type dns_resolver registered
[    1.710780] Using IPI No-Shortcut mode
[    1.710900] PM: Hibernation image not present or could not be loaded.
[    1.710907] Loading module verification certificates
[    1.715793] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 078e2d2826e5de868f2f0b7369bf76e573ecfc2a'
[    1.715809] registered taskstats version 1
[    1.718751] Key type trusted registered
[    1.721377] Key type encrypted registered
[    1.723921] AppArmor: AppArmor sha1 policy hashing enabled
[    1.724361]   Magic number: 1:374:739
[    1.724462] rtc_cmos 00:02: setting system clock to 2013-10-01 15:43:15 UTC (1380642195)
[    1.726262] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.726265] EDD information not available.
[    1.726890] Freeing unused kernel memory: 880K (c1977000 - c1a53000)
[    1.726932] Write protecting the kernel text: 6404k
[    1.727040] Write protecting the kernel read-only data: 2672k
[    1.727042] NX-protecting the kernel data: 5884k
[    1.743414] systemd-udevd[98]: starting version 204
[    1.762399] pps_core: module verification failed: signature and/or required key missing - tainting kernel
[    1.762645] pps_core: LinuxPPS API ver. 1 registered
[    1.762648] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.762916] PTP clock support registered
[    1.771980] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.771985] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    1.772295] e1000e 0000:00:19.0: setting latency timer to 64
[    1.772383] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.772409] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[    1.864089] firewire_ohci 0000:06:03.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.920045] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    2.052388] usb 1-3: New USB device found, idVendor=0424, idProduct=2504
[    2.052396] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.052708] hub 1-3:1.0: USB hub found
[    2.052759] hub 1-3:1.0: 4 ports detected
[    2.102082] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1c:c0:18:2a:ec
[    2.102087] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.102114] e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: FFFFFF-0FF
[    2.102137] ahci 0000:00:1f.2: version 3.0
[    2.102432] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    2.102510] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl RAID mode
[    2.102515] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ccc ems 
[    2.102521] ahci 0000:00:1f.2: setting latency timer to 64
[    2.116574] scsi2 : ahci
[    2.116673] scsi3 : ahci
[    2.116762] scsi4 : ahci
[    2.116854] ata3: SATA max UDMA/133 abar m2048@0x90425000 port 0x90425100 irq 46
[    2.116858] ata4: SATA max UDMA/133 abar m2048@0x90425000 port 0x90425180 irq 46
[    2.116861] ata5: SATA max UDMA/133 abar m2048@0x90425000 port 0x90425200 irq 46
[    2.220045] usb 2-3: new high-speed USB device number 3 using ehci-pci
[    2.364210] firewire_core 0000:06:03.0: created device fw0: GUID 0090270001f2dcb1, S400
[    2.436047] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.436075] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.436099] ata5: SATA link down (SStatus 0 SControl 300)
[    2.438722] ata4.00: ATA-7: ST96812AS, 8.04, max UDMA/133
[    2.438729] ata4.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.440735] ata4.00: configured for UDMA/133
[    2.448654] ata3.00: ATA-8: WDC WD3200AAJS-00VWA0, 12.01B02, max UDMA/133
[    2.448660] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.449482] ata3.00: configured for UDMA/133
[    2.449654] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 12.0 PQ: 0 ANSI: 5
[    2.449868] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.449893] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.449949] sd 2:0:0:0: [sda] Write Protect is off
[    2.449953] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.449978] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.450077] scsi 3:0:0:0: Direct-Access     ATA      ST96812AS        8.04 PQ: 0 ANSI: 5
[    2.450251] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.450282] sd 3:0:0:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.450335] sd 3:0:0:0: [sdb] Write Protect is off
[    2.450339] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.450363] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.453069]  sda: sda1
[    2.453419] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.604137] Switched to clocksource tsc
[    2.701673]  sdb: sdb1 sdb2 < sdb5 >
[    2.702160] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.967792] usb 2-3: New USB device found, idVendor=0bda, idProduct=0151
[    2.967802] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.967809] usb 2-3: Product: USB 2.0 Reader
[    2.967814] usb 2-3: Manufacturer: Generic
[    2.967819] usb 2-3: SerialNumber: 070403013943000001
[    2.970875] usb-storage 2-3:1.0: USB Mass Storage device detected
[    2.970956] scsi5 : usb-storage 2-3:1.0
[    2.971051] usbcore: registered new interface driver usb-storage
[    3.208099] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    3.296407] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    3.296412] EXT4-fs (sdb1): write access will be enabled during recovery
[    3.390669] usb 5-1: New USB device found, idVendor=0443, idProduct=0021
[    3.390677] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.390684] usb 5-1: Product: Gateway USB Wireless HID Receiver
[    3.390689] usb 5-1: Manufacturer: Chicony
[    3.403955] hidraw: raw HID events driver (C) Jiri Kosina
[    3.452778] usbcore: registered new interface driver usbhid
[    3.452784] usbhid: USB HID core driver
[    3.458990] input: Chicony Gateway USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
[    3.459341] hid-generic 0003:0443:0021.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Gateway USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input0
[    3.461057] input: Chicony Gateway USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input3
[    3.462485] hid-generic 0003:0443:0021.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Chicony Gateway USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input1
[    4.000711] scsi 5:0:0:0: Direct-Access     Generic  2.0 Reader       1.00 PQ: 0 ANSI: 0 CCS
[    4.001011] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    4.003430] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    6.285257] EXT4-fs (sdb1): recovery complete
[    6.294013] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   16.060998] Adding 4882428k swap on /dev/sdb5.  Priority:-1 extents:1 across:4882428k FS
[   16.372815] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.502579] systemd-udevd[276]: starting version 204
[   16.621472] lp: driver loaded but no devices found
[   16.700188] wmi: Mapper loaded
[   16.707240] [drm] Initialized drm 1.1.0 20060810
[   16.782743] Winbond CIR 00:07: activated
[   16.825463] [drm] Memory usable by graphics device = 512M
[   16.825477] i915 0000:00:02.0: setting latency timer to 64
[   16.832813] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   16.832831] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.832833] [drm] Driver supports precise vblank timestamp query.
[   16.832905] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.847354] Registered IR keymap rc-rc6-mce
[   16.847993] cfg80211: Calling CRDA to update world regulatory domain
[   16.848333] input: Winbond CIR as /devices/pnp0/00:07/rc/rc0/input4
[   16.848395] rc0: Winbond CIR as /devices/pnp0/00:07/rc/rc0
[   16.855625] IR NEC protocol handler initialized
[   16.863209] IR RC5(x) protocol handler initialized
[   16.876302] IR RC6 protocol handler initialized
[   16.876868] IR JVC protocol handler initialized
[   16.884992] IR Sony protocol handler initialized
[   16.892040] IR SANYO protocol handler initialized
[   16.900094] IR MCE Keyboard/mouse protocol handler initialized
[   16.907244] lirc_dev: IR Remote Control driver registered, major 247 
[   16.912636] input: MCE IR Keyboard/Mouse (winbond-cir) as /devices/virtual/input/input5
[   16.913765] rc rc0: lirc_dev: driver ir-lirc-codec (winbond-cir) registered at minor = 0
[   16.913770] IR LIRC bridge handler initialized
[   16.936494] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   16.936503] Raw EDID:
[   16.936507]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   16.936510]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.936514]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.936518]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.936521]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.936524]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.936528]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.936531]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.944354] type=1400 audit(1380656610.716:2): apparmor="STATUS" operation="profile_load" parent=305 profile="unconfined" name="/sbin/dhclient" pid=317 comm="apparmor_parser"
[   16.944364] type=1400 audit(1380656610.716:3): apparmor="STATUS" operation="profile_load" parent=305 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=317 comm="apparmor_parser"
[   16.944371] type=1400 audit(1380656610.716:4): apparmor="STATUS" operation="profile_load" parent=305 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=317 comm="apparmor_parser"
[   16.945192] type=1400 audit(1380656610.716:5): apparmor="STATUS" operation="profile_replace" parent=305 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=317 comm="apparmor_parser"
[   16.945202] type=1400 audit(1380656610.716:6): apparmor="STATUS" operation="profile_replace" parent=305 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=317 comm="apparmor_parser"
[   16.945626] type=1400 audit(1380656610.716:7): apparmor="STATUS" operation="profile_replace" parent=305 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=317 comm="apparmor_parser"
[   16.961394] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   16.961399] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   16.961465] iwl4965 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   16.961619] iwl4965 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   16.994799] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[   17.004716] iwl4965 0000:03:00.0: device EEPROM VER=0x36, CALIB=0x5
[   17.005184] iwl4965 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.005233] iwl4965 0000:03:00.0: irq 48 for MSI/MSI-X
[   17.056024] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   17.056032] Raw EDID:
[   17.056036]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   17.056040]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.056043]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.056047]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.056050]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.056054]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.056057]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.056061]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.090974] iwl4965 0000:03:00.0: loaded firmware version 228.61.2.24
[   17.097470] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   17.128050] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   17.128063] Raw EDID:
[   17.128072]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   17.128080]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.128088]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.128096]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.128103]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.128111]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.128119]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.128126]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200041] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   17.200059] Raw EDID:
[   17.200068]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   17.200076]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200083]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200091]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200098]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200106]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200113]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200121]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   17.200135] i915 0000:00:02.0: LVDS-1: EDID block 0 invalid.
[   17.201747] [drm] initialized overlay support
[   17.227741] fbcon: inteldrmfb (fb0) is primary device
[   17.924109] Console: switching to colour frame buffer device 180x56
[   17.931130] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   17.931132] i915 0000:00:02.0: registered panic notifier
[   17.940245] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   17.964408] acpi device:24: registered as cooling_device2
[   17.964429] ACPI: Video Device [IGFX] (multi-head: yes  rom: no  post: no)
[   17.964489] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   17.964580] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.964922] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GPE0 1 (20130517/utaddress-251)
[   17.964930] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.964935] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \IGPO 1 (20130517/utaddress-251)
[   17.964941] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.964982] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.965432] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   18.007598] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   18.007603]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.007605]    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   18.007607]    mono: mono_out=0x0
[   18.007610]    dig-out=0x21/0x0
[   18.007611]    inputs:
[   18.007614]      Mic=0xb
[   18.021205] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[   18.045896] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   18.048230] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   18.262777] cfg80211: World regulatory domain updated:
[   18.262783] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.262787] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.262790] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.262793] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.262795] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.262798] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.288201] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   18.288348] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.647442] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   20.890903] init: failsafe main process (610) killed by TERM signal
[   21.251843] Bluetooth: Core ver 2.16
[   21.251876] NET: Registered protocol family 31
[   21.251879] Bluetooth: HCI device and connection manager initialized
[   21.253984] Bluetooth: HCI socket layer initialized
[   21.253991] Bluetooth: L2CAP socket layer initialized
[   21.254002] Bluetooth: SCO socket layer initialized
[   21.285150] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.285154] Bluetooth: BNEP filters: protocol multicast
[   21.285165] Bluetooth: BNEP socket layer initialized
[   21.303534] Bluetooth: RFCOMM TTY layer initialized
[   21.303551] Bluetooth: RFCOMM socket layer initialized
[   21.303554] Bluetooth: RFCOMM ver 1.11
[   21.551189] type=1400 audit(1380656615.320:8): apparmor="STATUS" operation="profile_load" parent=747 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=753 comm="apparmor_parser"
[   21.551203] type=1400 audit(1380656615.320:9): apparmor="STATUS" operation="profile_load" parent=747 profile="unconfined" name="chromium_browser" pid=753 comm="apparmor_parser"
[   21.551702] type=1400 audit(1380656615.320:10): apparmor="STATUS" operation="profile_load" parent=747 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=752 comm="apparmor_parser"
[   21.551711] type=1400 audit(1380656615.320:11): apparmor="STATUS" operation="profile_load" parent=747 profile="unconfined" name="chromium_browser" pid=752 comm="apparmor_parser"
[   21.715565] ppdev: user-space parallel port driver
[   21.767920] init: avahi-cups-reload main process (766) terminated with status 1
```

---

### Post by oldfred on 2013-10-01
Please use code tags, # in Advanced editor for long text output.

It looks like you only posted the first 20 seconds. But do not post entire thing, just those with long times like this:
 Longer entries - about 10 sec:
[    6.294013] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   16.060998] Adding 4882428k swap on /dev/sdb5.  Priority:-1 extents:1 across:4882428k FS

What I do not know for sure is if that is sdb1 mounting slow or swap mounting slow. Or timestamp is before or after entry?

I boot from SSD and this is one of my longer times.

 [    5.721439] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    7.705965] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across:3076412k 

But it is the same mount that is slower, boot file partition, then swap, just for my system it is two seconds, yours is 10.

I might try a full fsck on your ext4 partitions.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mmcl26554 on 2013-10-01
Oldfred,
Sorry I didn't use the correct tags around the log, I am an absolute beginner and there is a LOT I don't know, but I am learning.   So I don't know which to use to enclosed pasted data.  I thought I had posted the entire log but for some reason that didn't happen.   I don't understand very well what your instructions mean but I also haven't read the the thread you suggested.   I'll read that and then research the commands you suggest, maybe I can learn more.   If I need further explanation I'll ask for more clarification.   The computer I am trying to get Ubuntu to work as a dual boot "bricked" the motherboard after I manually set the memory setting to accommodate some RAM with greater capacity (2 to 4 GB).  I have installed another board and it is up and running again.  In any case when I resolve or give up on it I will mark this thread appropriately.
Michael

---

### Post by oldfred on 2013-10-01
Scroll thru your entries and just post the few that have a longer time stamp between them as I posted above. Those would be the ones that may need further research.

---

### Post by mmcl26554 on 2013-10-01
OK, Probably won't get to it until tomorrow, thanks for the info!
Michael

---

### Post by Bucky Ball on 2013-10-02
Just a note: Support questions for 13.10 don't belong here. They should be posted in Ubuntu +1 sub-forum. It is not released yet and yes, expect oddities, glitches, bugs, crashes and the need to tweak it.

---

### Post by mmcl26554 on 2013-10-02
> **Bucky Ball said:**
> Just a note: Support questions for 13.10 don't belong here. They should be posted in Ubuntu +1 sub-forum. It is not released yet and yes, expect oddities, glitches, bugs, crashes and the need to tweak it.

Actually this isn't a 13.10 issue as I only installed it over 12.04 at the suggestion of the people at "boot restore" since it had a newer version of Grub. 13.10 didn't help the problem anyway.   However, I can just as easily remove 13.10 and put 12.04 back as that is the version I want to run and I am much more used to it.  So I will reinstall 12.04 and run the suggested tests from it.
Michael

---

### Post by mmcl26554 on 2013-10-18
I have been doing some studying on the internet and am wondering if when I reinstall 12.04 on it's own drive with Vista on the first drive I should setup a separate /boot partition.  The computer I am using is a bios mbr boot but is it possible the separate /boot partition would improve the long boot time for Ubuntu and also allow Grub to boot Vista.
Michael

---

### Post by oldfred on 2013-10-18
Usually separate /boot is not required for a desktop. 

Some older BIOS have issues with boot files beyond 120GB. Only recent issues seem to be those booting from USB drives and then boot files beyond 100GB. And those systems do not boot, but give grub errors.

I normally suggest smaller / (root) of 10 to 25GB so all boot & system files are closer together on system and then separate /mnt/data or separate /home for rest of space you want for Ubuntu.

Vista not booting from grub is still a separate  issue. Grub can really only boot a Working Windows, so you have to fix Vista first. Always best to repair Vista from a Windows repairCD or flash drive and even install its boot loader to make sure it boots ok. After any resize of a NTFS partition chkdsk is required and that can only be run from Windows repair console or repairCD.
Then reinstall grub to MBR and run sudo update-grub to add Vista to grub menu.

---

### Post by mmcl26554 on 2013-10-23
I'm back after bricking and replacing the motherboard in this computer.  All I did was to specify parameters for some new ram and the MB died.   Oh well the replacement was only $35.   I have now reinstalled 12.04lts on the same 60GB hard drive and I still have the same problem of no boot of Vista from the Grub menu and a very long wait to get to the Grub menue where I can boot Ubuntu.  But that is a little long also.  Here is the output from /var/log/dmesg  hop I got it all this time!
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-32-generic (buildd@panlong) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #47~precise1-Ubuntu SMP Wed Oct 2 16:22:28 UTC 2013 (Ubuntu 3.8.0-32.47~precise1-generic 3.8.13.10)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf5bcfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf5bd000-0x00000000bf5c9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf5ca000-0x00000000bf655fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf656000-0x00000000bf6e7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf6e8000-0x00000000bf6ebfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf6ec000-0x00000000bf6f0fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bf6f1000-0x00000000bf6f1fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf6f2000-0x00000000bf6fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bf6ff000-0x00000000bf6fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf700000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Gateway                          ZX190                           /DGM965RA, BIOS RA96510J.15A.0092.2007.1214.1014 12/14/2007
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbf700 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   3 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   4 base 0FFF00000 mask FFFF00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000fe200-0x000fe20f] mapped at [c00fe200]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c008b000] 8b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x36160000-0x370a7fff]
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 GATEWA)
[    0.000000] ACPI: RSDT bf6fd038 00050 (v01 GATEWA SYSTEM   0000005C      01000013)
[    0.000000] ACPI: FACP bf6fc000 000F4 (v02 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: DSDT bf6f7000 044A4 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: FACS bf6a2000 00040
[    0.000000] ACPI: APIC bf6f6000 00078 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: WDDT bf6f5000 00040 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: MCFG bf6f4000 0003C (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: ASF! bf6f3000 000A6 (v32 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: SLIC bf6f2000 00176 (v01 GATEWA SYSTEM   0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT bf6f0000 001BC (v01 GATEWA    CpuPm 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT bf6ef000 001B7 (v01 GATEWA  Cpu0Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT bf6ee000 001B7 (v01 GATEWA  Cpu1Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT bf6ed000 001B7 (v01 GATEWA  Cpu2Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: SSDT bf6ec000 001B7 (v01 GATEWA  Cpu3Ist 0000005C MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2171MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0xbf6fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0008efff]
[    0.000000]   node   0: [mem 0x00100000-0xbf5bcfff]
[    0.000000]   node   0: [mem 0xbf5ca000-0xbf655fff]
[    0.000000]   node   0: [mem 0xbf6e8000-0xbf6ebfff]
[    0.000000]   node   0: [mem 0xbf6f1000-0xbf6f1fff]
[    0.000000]   node   0: [mem 0xbf6ff000-0xbf6fffff]
[    0.000000] On node 0 totalpages: 783822
[    0.000000] free_area_init_node: node 0, pgdat c1921f80, node_mem_map f4970200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3935 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4343 pages used for memmap
[    0.000000]   HighMem zone: 551258 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0xc0000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34880 r0 d22464 u57344
[    0.000000] pcpu-alloc: s34880 r0 d22464 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777695
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-32-generic root=UUID=74b46717-25d0-ce01-5034-671725d0ce01 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6272896 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:000bf700)
[    0.000000] Memory: 3076728k/3136512k available (6361k kernel code, 58560k reserved, 3039k data, 796k init, 2222404k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc192f000 - 0xc19f6000   ( 796 kB)
[    0.000000]       .data : 0xc16365ad - 0xc192e280   (3039 kB)
[    0.000000]       .text : 0xc1000000 - 0xc16365ad   (6361 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1833.444 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3666.88 BogoMIPS (lpj=7333776)
[    0.004006] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004052] AppArmor: AppArmor initialized
[    0.004054] Yama: becoming mindful.
[    0.004112] Mount-cache hash table entries: 512
[    0.004378] Initializing cgroup subsys cpuacct
[    0.004381] Initializing cgroup subsys memory
[    0.004390] Initializing cgroup subsys devices
[    0.004392] Initializing cgroup subsys freezer
[    0.004395] Initializing cgroup subsys blkio
[    0.004397] Initializing cgroup subsys perf_event
[    0.004401] Initializing cgroup subsys hugetlb
[    0.004435] CPU: Physical Processor ID: 0
[    0.004437] CPU: Processor Core ID: 0
[    0.004441] mce: CPU supports 6 MCE banks
[    0.004448] CPU0: Thermal monitoring enabled (TM2)
[    0.004452] process: using mwait in idle threads
[    0.004462] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.004462] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
[    0.004462] tlb_flushall_shift: -1
[    0.004765] Freeing SMP alternatives: 24k freed
[    0.008794] ACPI: Core revision 20121018
[    0.014772] ftrace: allocating 28850 entries in 57 pages
[    0.024122] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024513] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069203] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz (fam: 06, model: 0f, stepping: 0d)
[    0.072000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.072000] perf_event_intel: PEBS disabled due to CPU errata
[    0.072000] ... version:                2
[    0.072000] ... bit width:              40
[    0.072000] ... generic registers:      2
[    0.072000] ... value mask:             000000ffffffffff
[    0.072000] ... max period:             000000007fffffff
[    0.072000] ... fixed-purpose events:   3
[    0.072000] ... event mask:             0000000700000003
[    0.072000] CPU 1 irqstacks, hard=f44e8000 soft=f44ea000
[    0.008000] Initializing CPU#1
[    0.072000] smpboot: Booting Node   0, Processors  #1
[    0.082605] Brought up 2 CPUs
[    0.082611] smpboot: Total of 2 processors activated (7333.77 BogoMIPS)
[    0.082748] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.084114] devtmpfs: initialized
[    0.084280] EVM: security.selinux
[    0.084283] EVM: security.SMACK64
[    0.084285] EVM: security.capability
[    0.084299] PM: Registering ACPI NVS region [mem 0xbf656000-0xbf6e7fff] (598016 bytes)
[    0.085463] regulator-dummy: no parameters
[    0.085535] NET: Registered protocol family 16
[    0.085730] EISA bus registered
[    0.085850] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.085853] ACPI: bus type pci registered
[    0.085936] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.085940] PCI: not using MMCONFIG
[    0.088506] PCI: Using configuration type 1 for base access
[    0.089953] bio: create slab <bio-0> at 0
[    0.089953] ACPI: Added _OSI(Module Device)
[    0.089953] ACPI: Added _OSI(Processor Device)
[    0.089953] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.089953] ACPI: Added _OSI(Processor Aggregator Device)
[    0.089953] ACPI: EC: Look up EC in DSDT
[    0.095157] ACPI: Interpreter enabled
[    0.095181] ACPI: (supports S0 S3 S4 S5)
[    0.095203] ACPI: Using IOAPIC for interrupt routing
[    0.095222] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.095404] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in ACPI motherboard resources
[    0.095407] PCI: Using MMCONFIG for extended config space
[    0.099535] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.099931] ACPI: No dock devices found.
[    0.099942] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.100883] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.100887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.102905] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.102909] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.102912] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.102916] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff] (ignored)
[    0.102919] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfeafffff] (ignored)
[    0.102922] pci_root PNP0A03:00: host bridge window [mem 0xc0000000-0xefffffff] (ignored)
[    0.102925] PCI: root bus 00: using default resources
[    0.102930] pci_root PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-7f] only partially covers this bridge
[    0.102968] PCI host bridge to bus 0000:00
[    0.102972] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.102975] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.102978] pci_bus 0000:00: root bus resource [mem 0x00000000-0xfffffffff]
[    0.102992] pci 0000:00:00.0: [8086:2a00] type 00 class 0x060000
[    0.103056] pci 0000:00:02.0: [8086:2a02] type 00 class 0x030000
[    0.103075] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd00fffff 64bit]
[    0.103087] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.103095] pci 0000:00:02.0: reg 20: [io  0x1130-0x1137]
[    0.103147] pci 0000:00:02.1: [8086:2a03] type 00 class 0x038000
[    0.103163] pci 0000:00:02.1: reg 10: [mem 0xd0100000-0xd01fffff 64bit]
[    0.103262] pci 0000:00:19.0: [8086:104d] type 00 class 0x020000
[    0.103283] pci 0000:00:19.0: reg 10: [mem 0xd0400000-0xd041ffff]
[    0.103295] pci 0000:00:19.0: reg 14: [mem 0xd0424000-0xd0424fff]
[    0.103306] pci 0000:00:19.0: reg 18: [io  0x10e0-0x10ff]
[    0.103381] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.103401] pci 0000:00:1a.0: [8086:2834] type 00 class 0x0c0300
[    0.103452] pci 0000:00:1a.0: reg 20: [io  0x10c0-0x10df]
[    0.103491] pci 0000:00:1a.1: [8086:2835] type 00 class 0x0c0300
[    0.103542] pci 0000:00:1a.1: reg 20: [io  0x10a0-0x10bf]
[    0.103595] pci 0000:00:1a.7: [8086:283a] type 00 class 0x0c0320
[    0.103619] pci 0000:00:1a.7: reg 10: [mem 0xd0425c00-0xd0425fff]
[    0.103721] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.103751] pci 0000:00:1b.0: [8086:284b] type 00 class 0x040300
[    0.103771] pci 0000:00:1b.0: reg 10: [mem 0xd0420000-0xd0423fff 64bit]
[    0.103859] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.103888] pci 0000:00:1c.0: [8086:283f] type 01 class 0x060400
[    0.103978] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.104016] pci 0000:00:1c.1: [8086:2841] type 01 class 0x060400
[    0.104106] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.104136] pci 0000:00:1c.2: [8086:2843] type 01 class 0x060400
[    0.104226] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.104256] pci 0000:00:1c.3: [8086:2845] type 01 class 0x060400
[    0.104346] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.104376] pci 0000:00:1c.4: [8086:2847] type 01 class 0x060400
[    0.104466] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.104497] pci 0000:00:1d.0: [8086:2830] type 00 class 0x0c0300
[    0.104548] pci 0000:00:1d.0: reg 20: [io  0x1080-0x109f]
[    0.104588] pci 0000:00:1d.1: [8086:2831] type 00 class 0x0c0300
[    0.104639] pci 0000:00:1d.1: reg 20: [io  0x1060-0x107f]
[    0.104678] pci 0000:00:1d.2: [8086:2832] type 00 class 0x0c0300
[    0.104728] pci 0000:00:1d.2: reg 20: [io  0x1040-0x105f]
[    0.104781] pci 0000:00:1d.7: [8086:2836] type 00 class 0x0c0320
[    0.104804] pci 0000:00:1d.7: reg 10: [mem 0xd0425800-0xd0425bff]
[    0.104906] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.104931] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.105012] pci 0000:00:1f.0: [8086:2811] type 00 class 0x060100
[    0.105109] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.105123] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.105128] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0810 (mask 007f)
[    0.105180] pci 0000:00:1f.1: [8086:2850] type 00 class 0x01018a
[    0.105196] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.105208] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.105220] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.105232] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.105244] pci 0000:00:1f.1: reg 20: [io  0x1100-0x110f]
[    0.105293] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
[    0.105316] pci 0000:00:1f.2: reg 10: [io  0x1118-0x111f]
[    0.105327] pci 0000:00:1f.2: reg 14: [io  0x113c-0x113f]
[    0.105337] pci 0000:00:1f.2: reg 18: [io  0x1110-0x1117]
[    0.105348] pci 0000:00:1f.2: reg 1c: [io  0x1138-0x113b]
[    0.105359] pci 0000:00:1f.2: reg 20: [io  0x1020-0x103f]
[    0.105370] pci 0000:00:1f.2: reg 24: [mem 0xd0425000-0xd04257ff]
[    0.105424] pci 0000:00:1f.2: PME# supported from D3hot
[    0.105446] pci 0000:00:1f.3: [8086:283e] type 00 class 0x0c0500
[    0.105461] pci 0000:00:1f.3: reg 10: [mem 0xd0426000-0xd04260ff]
[    0.105497] pci 0000:00:1f.3: reg 20: [io  0x1000-0x101f]
[    0.105581] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.105589] pci 0000:00:1c.0:   bridge window [mem 0xd0500000-0xd05fffff]
[    0.105645] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.105652] pci 0000:00:1c.1:   bridge window [mem 0xd0600000-0xd06fffff]
[    0.105737] pci 0000:03:00.0: [8086:4229] type 00 class 0x028000
[    0.105776] pci 0000:03:00.0: reg 10: [mem 0xd0300000-0xd0301fff 64bit]
[    0.105955] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.112033] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.112046] pci 0000:00:1c.2:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.112125] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.112137] pci 0000:00:1c.3:   bridge window [mem 0xd0700000-0xd07fffff]
[    0.112215] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.112228] pci 0000:00:1c.4:   bridge window [mem 0xd0800000-0xd08fffff]
[    0.112294] pci 0000:06:03.0: [104c:8023] type 00 class 0x0c0010
[    0.112316] pci 0000:06:03.0: reg 10: [mem 0xd0204000-0xd02047ff]
[    0.112329] pci 0000:06:03.0: reg 14: [mem 0xd0200000-0xd0203fff]
[    0.112416] pci 0000:06:03.0: supports D1 D2
[    0.112419] pci 0000:06:03.0: PME# supported from D0 D1 D2 D3hot
[    0.112474] pci 0000:00:1e.0: PCI bridge to [bus 06] (subtractive decode)
[    0.112482] pci 0000:00:1e.0:   bridge window [mem 0xd0200000-0xd02fffff]
[    0.112490] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.112493] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xfffffffff] (subtractive decode)
[    0.112526] pci_bus 0000:00: on NUMA node 0
[    0.112537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.112776] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.112847] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.112917] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.112985] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.113054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.113180]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.113184]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.114917] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11 12)
[    0.114994] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.115069] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12)
[    0.115142] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[    0.115215] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12)
[    0.115288] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.115360] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
[    0.115432] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.115553] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.115553] vgaarb: loaded
[    0.115553] vgaarb: bridge control possible 0000:00:02.0
[    0.115553] SCSI subsystem initialized
[    0.115553] ACPI: bus type scsi registered
[    0.115553] libata version 3.00 loaded.
[    0.115553] ACPI: bus type usb registered
[    0.115553] usbcore: registered new interface driver usbfs
[    0.115553] usbcore: registered new interface driver hub
[    0.116014] usbcore: registered new device driver usb
[    0.116062] PCI: Using ACPI for IRQ routing
[    0.119725] PCI: pci_cache_line_size set to 64 bytes
[    0.119816] e820: reserve RAM buffer [mem 0x0008f000-0x0008ffff]
[    0.119819] e820: reserve RAM buffer [mem 0xbf5bd000-0xbfffffff]
[    0.119823] e820: reserve RAM buffer [mem 0xbf656000-0xbfffffff]
[    0.119826] e820: reserve RAM buffer [mem 0xbf6ec000-0xbfffffff]
[    0.119829] e820: reserve RAM buffer [mem 0xbf6f2000-0xbfffffff]
[    0.120003] e820: reserve RAM buffer [mem 0xbf700000-0xbfffffff]
[    0.120128] NetLabel: Initializing
[    0.120130] NetLabel:  domain hash size = 128
[    0.120132] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.120146] NetLabel:  unlabeled traffic allowed by default
[    0.120235] hpet clockevent registered
[    0.120239] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.120244] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.120251] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.122269] Switching to clocksource hpet
[    0.130279] AppArmor: AppArmor Filesystem Enabled
[    0.130329] pnp: PnP ACPI init
[    0.130353] ACPI: bus type pnp registered
[    0.130479] system 00:00: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.130483] system 00:00: [mem 0xfed13000-0xfed13fff] has been reserved
[    0.130487] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.130491] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.130495] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.130499] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.130502] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.130506] system 00:00: [mem 0xfed45000-0xfed99fff] has been reserved
[    0.130510] system 00:00: [mem 0x000c0000-0x000dffff] could not be reserved
[    0.130514] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.130519] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.130704] pnp 00:01: [dma 4]
[    0.130732] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.130783] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.130831] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.130872] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.130935] system 00:05: [io  0x0500-0x053f] has been reserved
[    0.130939] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.130943] system 00:05: [io  0x0680-0x06ff] has been reserved
[    0.130948] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.131049] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.131163] pnp 00:07: Plug and Play ACPI device, IDs WEC1022 (active)
[    0.131279] pnp 00:08: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.131373] pnp: PnP ACPI: found 9 devices
[    0.131375] ACPI: ACPI bus type pnp unregistered
[    0.131380] PnPBIOS: Disabled by ACPI PNP
[    0.168373] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.168380] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.168391] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.168395] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.168406] pci 0000:00:1c.2: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.168410] pci 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.168421] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 04] add_size 1000
[    0.168425] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 04] add_size 200000
[    0.168436] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 05] add_size 1000
[    0.168440] pci 0000:00:1c.4: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 05] add_size 200000
[    0.168459] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.168463] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.168467] pci 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.168470] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.168474] pci 0000:00:1c.4: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.168477] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.168481] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.168484] pci 0000:00:1c.2: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.168487] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.168491] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.168500] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd0900000-0xd0afffff 64bit pref]
[    0.168505] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd0b00000-0xd0cfffff 64bit pref]
[    0.168510] pci 0000:00:1c.2: BAR 15: assigned [mem 0xd0d00000-0xd0efffff 64bit pref]
[    0.168515] pci 0000:00:1c.3: BAR 15: assigned [mem 0xd0f00000-0xd10fffff 64bit pref]
[    0.168520] pci 0000:00:1c.4: BAR 15: assigned [mem 0xd1100000-0xd12fffff 64bit pref]
[    0.168525] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.168530] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.168534] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.168539] pci 0000:00:1c.3: BAR 13: assigned [io  0x5000-0x5fff]
[    0.168543] pci 0000:00:1c.4: BAR 13: assigned [io  0x6000-0x6fff]
[    0.168548] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.168553] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.168560] pci 0000:00:1c.0:   bridge window [mem 0xd0500000-0xd05fffff]
[    0.168565] pci 0000:00:1c.0:   bridge window [mem 0xd0900000-0xd0afffff 64bit pref]
[    0.168573] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.168577] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.168584] pci 0000:00:1c.1:   bridge window [mem 0xd0600000-0xd06fffff]
[    0.168589] pci 0000:00:1c.1:   bridge window [mem 0xd0b00000-0xd0cfffff 64bit pref]
[    0.168597] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.168601] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.168607] pci 0000:00:1c.2:   bridge window [mem 0xd0300000-0xd03fffff]
[    0.168613] pci 0000:00:1c.2:   bridge window [mem 0xd0d00000-0xd0efffff 64bit pref]
[    0.168620] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.168624] pci 0000:00:1c.3:   bridge window [io  0x5000-0x5fff]
[    0.168631] pci 0000:00:1c.3:   bridge window [mem 0xd0700000-0xd07fffff]
[    0.168636] pci 0000:00:1c.3:   bridge window [mem 0xd0f00000-0xd10fffff 64bit pref]
[    0.168644] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    0.168648] pci 0000:00:1c.4:   bridge window [io  0x6000-0x6fff]
[    0.168655] pci 0000:00:1c.4:   bridge window [mem 0xd0800000-0xd08fffff]
[    0.168660] pci 0000:00:1c.4:   bridge window [mem 0xd1100000-0xd12fffff 64bit pref]
[    0.168668] pci 0000:00:1e.0: PCI bridge to [bus 06]
[    0.168674] pci 0000:00:1e.0:   bridge window [mem 0xd0200000-0xd02fffff]
[    0.168735] pci 0000:00:1e.0: setting latency timer to 64
[    0.168741] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.168744] pci_bus 0000:00: resource 5 [mem 0x00000000-0xfffffffff]
[    0.168748] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.168751] pci_bus 0000:01: resource 1 [mem 0xd0500000-0xd05fffff]
[    0.168754] pci_bus 0000:01: resource 2 [mem 0xd0900000-0xd0afffff 64bit pref]
[    0.168757] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.168760] pci_bus 0000:02: resource 1 [mem 0xd0600000-0xd06fffff]
[    0.168764] pci_bus 0000:02: resource 2 [mem 0xd0b00000-0xd0cfffff 64bit pref]
[    0.168767] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.168770] pci_bus 0000:03: resource 1 [mem 0xd0300000-0xd03fffff]
[    0.168773] pci_bus 0000:03: resource 2 [mem 0xd0d00000-0xd0efffff 64bit pref]
[    0.168776] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
[    0.168780] pci_bus 0000:04: resource 1 [mem 0xd0700000-0xd07fffff]
[    0.168783] pci_bus 0000:04: resource 2 [mem 0xd0f00000-0xd10fffff 64bit pref]
[    0.168786] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.168789] pci_bus 0000:05: resource 1 [mem 0xd0800000-0xd08fffff]
[    0.168792] pci_bus 0000:05: resource 2 [mem 0xd1100000-0xd12fffff 64bit pref]
[    0.168796] pci_bus 0000:06: resource 1 [mem 0xd0200000-0xd02fffff]
[    0.168799] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.168802] pci_bus 0000:06: resource 5 [mem 0x00000000-0xfffffffff]
[    0.168852] NET: Registered protocol family 2
[    0.169063] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.169112] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.169158] TCP: Hash tables configured (established 8192 bind 8192)
[    0.169195] TCP: reno registered
[    0.169199] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.169212] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.169282] NET: Registered protocol family 1
[    0.169298] pci 0000:00:02.0: Boot video device
[    0.169710] PCI: CLS 64 bytes, default 64
[    0.169762] Trying to unpack rootfs image as initramfs...
[    0.565457] Freeing initrd memory: 15648k freed
[    0.575236] Initialise module verification
[    0.575304] audit: initializing netlink socket (disabled)
[    0.575334] type=2000 audit(1382545377.572:1): initialized
[    0.604674] bounce pool size: 64 pages
[    0.604689] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.606876] VFS: Disk quotas dquot_6.5.2
[    0.606942] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.607691] fuse init (API version 7.20)
[    0.607804] msgmni has been set to 1699
[    0.608294] Key type asymmetric registered
[    0.608297] Asymmetric key parser 'x509' registered
[    0.608345] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.608376] io scheduler noop registered
[    0.608379] io scheduler deadline registered (default)
[    0.608388] io scheduler cfq registered
[    0.608586] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.608702] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.608812] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.608925] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.609037] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.609134] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.609156] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609238] intel_idle: does not run on family 6 model 15
[    0.609324] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.609332] ACPI: Sleep Button [SLPB]
[    0.609395] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.609399] ACPI: Power Button [PWRF]
[    0.609509] ACPI: Requesting acpi_cpufreq
[    0.612729] GHES: HEST is not enabled!
[    0.612749] isapnp: Scanning for PnP cards...
[    0.612837] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.612973] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a CIR port
[    0.613066] serial 00:07: disabled
[    0.614590] Linux agpgart interface v0.103
[    0.614709] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    0.614813] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.615375] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.615508] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.617306] brd: module loaded
[    0.618167] loop: module loaded
[    0.618329] ata_piix 0000:00:1f.1: version 2.13
[    0.618344] ata_piix 0000:00:1f.1: can't derive routing for PCI INT D
[    0.618386] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.618699] scsi0 : ata_piix
[    0.620026] scsi1 : ata_piix
[    0.620089] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1100 irq 14
[    0.620092] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1108 irq 15
[    0.620476] libphy: Fixed MDIO Bus: probed
[    0.620570] tun: Universal TUN/TAP device driver, 1.6
[    0.620572] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.620637] PPP generic driver version 2.4.2
[    0.620690] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.620693] ehci-pci: EHCI PCI platform driver
[    0.620727] ehci-pci 0000:00:1a.7: setting latency timer to 64
[    0.620732] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.620740] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.620757] ehci-pci 0000:00:1a.7: debug port 1
[    0.624673] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.624693] ehci-pci 0000:00:1a.7: irq 18, io mem 0xd0425c00
[    0.628191] ata2: port disabled--ignoring
[    0.636021] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.636049] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.636053] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.636056] usb usb1: Product: EHCI Host Controller
[    0.636059] usb usb1: Manufacturer: Linux 3.8.0-32-generic ehci_hcd
[    0.636062] usb usb1: SerialNumber: 0000:00:1a.7
[    0.636182] hub 1-0:1.0: USB hub found
[    0.636190] hub 1-0:1.0: 4 ports detected
[    0.636327] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.636332] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.636338] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.636353] ehci-pci 0000:00:1d.7: debug port 1
[    0.640268] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.640291] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd0425800
[    0.652021] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.652043] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.652046] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.652049] usb usb2: Product: EHCI Host Controller
[    0.652052] usb usb2: Manufacturer: Linux 3.8.0-32-generic ehci_hcd
[    0.652055] usb usb2: SerialNumber: 0000:00:1d.7
[    0.652165] hub 2-0:1.0: USB hub found
[    0.652170] hub 2-0:1.0: 6 ports detected
[    0.652323] ehci-platform: EHCI generic platform driver
[    0.652335] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.652361] uhci_hcd: USB Universal Host Controller Interface driver
[    0.652384] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.652389] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.652395] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.652431] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000010c0
[    0.652472] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.652475] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.652478] usb usb3: Product: UHCI Host Controller
[    0.652482] usb usb3: Manufacturer: Linux 3.8.0-32-generic uhci_hcd
[    0.652484] usb usb3: SerialNumber: 0000:00:1a.0
[    0.652599] hub 3-0:1.0: USB hub found
[    0.652605] hub 3-0:1.0: 2 ports detected
[    0.652701] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.652705] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.652711] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.652747] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000010a0
[    0.652783] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.652786] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.652789] usb usb4: Product: UHCI Host Controller
[    0.652792] usb usb4: Manufacturer: Linux 3.8.0-32-generic uhci_hcd
[    0.652795] usb usb4: SerialNumber: 0000:00:1a.1
[    0.652901] hub 4-0:1.0: USB hub found
[    0.652906] hub 4-0:1.0: 2 ports detected
[    0.653003] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.653007] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.653013] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.653037] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001080
[    0.653074] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.653077] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.653080] usb usb5: Product: UHCI Host Controller
[    0.653083] usb usb5: Manufacturer: Linux 3.8.0-32-generic uhci_hcd
[    0.653086] usb usb5: SerialNumber: 0000:00:1d.0
[    0.653194] hub 5-0:1.0: USB hub found
[    0.653199] hub 5-0:1.0: 2 ports detected
[    0.653296] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.653300] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.653307] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.653342] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001060
[    0.653377] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.653381] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.653384] usb usb6: Product: UHCI Host Controller
[    0.653387] usb usb6: Manufacturer: Linux 3.8.0-32-generic uhci_hcd
[    0.653390] usb usb6: SerialNumber: 0000:00:1d.1
[    0.653507] hub 6-0:1.0: USB hub found
[    0.653512] hub 6-0:1.0: 2 ports detected
[    0.653605] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.653610] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.653616] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.653640] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001040
[    0.653675] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.653678] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.653681] usb usb7: Product: UHCI Host Controller
[    0.653684] usb usb7: Manufacturer: Linux 3.8.0-32-generic uhci_hcd
[    0.653687] usb usb7: SerialNumber: 0000:00:1d.2
[    0.653790] hub 7-0:1.0: USB hub found
[    0.653797] hub 7-0:1.0: 2 ports detected
[    0.653969] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.966038] isapnp: No Plug & Play device found
[    1.680343] tsc: Refined TSC clocksource calibration: 1833.333 MHz
[    1.680348] Switching to clocksource tsc
[    1.680986] i8042: No controller found
[    1.681013] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-T632A, GA00, max UDMA/33
[    1.681273] mousedev: PS/2 mouse device common for all mice
[    1.681457] rtc_cmos 00:02: RTC can wake from S4
[    1.681584] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.681612] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.681738] device-mapper: uevent: version 1.0.3
[    1.681816] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.681842] EISA: Probing bus 0 at eisa.0
[    1.681848] Cannot allocate resource for EISA slot 1
[    1.681851] Cannot allocate resource for EISA slot 2
[    1.681853] Cannot allocate resource for EISA slot 3
[    1.681856] Cannot allocate resource for EISA slot 4
[    1.681858] Cannot allocate resource for EISA slot 5
[    1.681860] Cannot allocate resource for EISA slot 6
[    1.681869] EISA: Detected 0 cards.
[    1.681881] cpufreq-nforce2: No nForce2 chipset.
[    1.681884] cpuidle: using governor ladder
[    1.681886] cpuidle: using governor menu
[    1.681891] ledtrig-cpu: registered to indicate activity on CPUs
[    1.681893] EFI Variables Facility v0.08 2004-May-17
[    1.682092] ashmem: initialized
[    1.682249] TCP: cubic registered
[    1.682392] NET: Registered protocol family 10
[    1.682640] NET: Registered protocol family 17
[    1.682653] Key type dns_resolver registered
[    1.682858] Using IPI No-Shortcut mode
[    1.682950] Loading module verification certificates
[    1.687940] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 3cb12b7e593ab85d86c12d43a7404fd39f0c861b'
[    1.687956] registered taskstats version 1
[    1.690719] Key type trusted registered
[    1.693036] Key type encrypted registered
[    1.695777] rtc_cmos 00:02: setting system clock to 2013-10-23 16:22:59 UTC (1382545379)
[    1.697653] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.697655] EDD information not available.
[    1.712237] ata1.00: configured for UDMA/33
[    1.721600] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-T632A GA00 PQ: 0 ANSI: 5
[    1.737710] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.737717] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.737929] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.738117] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.738254] Freeing unused kernel memory: 796k freed
[    1.738598] Write protecting the kernel text: 6364k
[    1.738687] Write protecting the kernel read-only data: 2496k
[    1.738688] NX-protecting the kernel data: 3876k
[    1.759246] udevd[99]: starting version 175
[    1.807933] Disabling lock debugging due to kernel taint
[    1.812214] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    1.812218] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    1.812283] e1000e 0000:00:19.0: setting latency timer to 64
[    1.812373] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.812417] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[    1.908112] firewire_ohci 0000:06:03.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.948043] usb 2-3: new high-speed USB device number 3 using ehci-pci
[    2.130083] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:1c:c0:17:1c:47
[    2.130087] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.130115] e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: FFFFFF-0FF
[    2.130142] ahci 0000:00:1f.2: version 3.0
[    2.130226] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    2.130307] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl RAID mode
[    2.130312] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ccc ems 
[    2.130318] ahci 0000:00:1f.2: setting latency timer to 64
[    2.144531] scsi2 : ahci
[    2.144628] scsi3 : ahci
[    2.144716] scsi4 : ahci
[    2.144808] ata3: SATA max UDMA/133 abar m2048@0xd0425000 port 0xd0425100 irq 46
[    2.144812] ata4: SATA max UDMA/133 abar m2048@0xd0425000 port 0xd0425180 irq 46
[    2.144816] ata5: SATA max UDMA/133 abar m2048@0xd0425000 port 0xd0425200 irq 46
[    2.408186] firewire_core 0000:06:03.0: created device fw0: GUID 0090270001f14b55, S400
[    2.464046] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.464074] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.464097] ata5: SATA link down (SStatus 0 SControl 300)
[    2.465355] ata4.00: ATA-7: ST96812AS, 8.04, max UDMA/133
[    2.465362] ata4.00: 117210240 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.466899] ata4.00: configured for UDMA/133
[    2.475053] ata3.00: ATA-8: WDC WD3200AAJS-00VWA0, 12.01B02, max UDMA/133
[    2.475059] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.475882] ata3.00: configured for UDMA/133
[    2.476111] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 12.0 PQ: 0 ANSI: 5
[    2.476396] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.476405] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.476455] sd 2:0:0:0: [sda] Write Protect is off
[    2.476459] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.476563] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.476565] scsi 3:0:0:0: Direct-Access     ATA      ST96812AS        8.04 PQ: 0 ANSI: 5
[    2.476740] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.476835] sd 3:0:0:0: [sdb] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.476907] sd 3:0:0:0: [sdb] Write Protect is off
[    2.476911] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.476940] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.479455]  sda: sda1
[    2.479803] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.519638]  sdb: sdb1 sdb2 < sdb5 >
[    2.520160] sd 3:0:0:0: [sdb] Attached SCSI disk
[    2.695974] usb 2-3: New USB device found, idVendor=0bda, idProduct=0151
[    2.695984] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.695990] usb 2-3: Product: USB 2.0 Reader
[    2.695996] usb 2-3: Manufacturer: Generic
[    2.696011] usb 2-3: SerialNumber: 070403013943000001
[    2.701099] Initializing USB Mass Storage driver...
[    2.701247] scsi5 : usb-storage 2-3:1.0
[    2.701354] usbcore: registered new interface driver usb-storage
[    2.701357] USB Mass Storage support registered.
[    2.936042] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    3.119084] usb 5-1: New USB device found, idVendor=0443, idProduct=0021
[    3.119092] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.119098] usb 5-1: Product: Gateway USB Wireless HID Receiver
[    3.119103] usb 5-1: Manufacturer: Chicony
[    3.167225] usbcore: registered new interface driver usbhid
[    3.167233] usbhid: USB HID core driver
[    3.170536] input: Chicony Gateway USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
[    3.170649] hid-generic 0003:0443:0021.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Gateway USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input0
[    3.171976] input: Chicony Gateway USB Wireless HID Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input3
[    3.172167] hid-generic 0003:0443:0021.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Chicony Gateway USB Wireless HID Receiver] on usb-0000:00:1d.0-1/input1
[    3.221320] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.732024] scsi 5:0:0:0: Direct-Access     Generic  2.0 Reader       1.00 PQ: 0 ANSI: 0 CCS
[    3.732759] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.734478] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    4.969190] init: ureadahead main process (261) terminated with status 5
[    6.777785] Adding 6143996k swap on /dev/sdb5.  Priority:-1 extents:1 across:6143996k 
[    7.846461] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.294690] udevd[337]: starting version 175
[    8.850889] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    9.980560] lp: driver loaded but no devices found
[   11.391277] wmi: Mapper loaded
[   11.395180] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GPE0 1 (20121018/utaddress-251)
[   11.395191] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.395196] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \IGPO 1 (20121018/utaddress-251)
[   11.395201] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.395235] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.548708] Winbond CIR 00:07: activated
[   11.554601] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   11.588529] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa1
[   11.604042] Registered IR keymap rc-rc6-mce
[   11.604176] input: Winbond CIR as /devices/pnp0/00:07/rc/rc0/input4
[   11.604287] rc0: Winbond CIR as /devices/pnp0/00:07/rc/rc0
[   11.715500] IR NEC protocol handler initialized
[   11.819063] [drm] Initialized drm 1.1.0 20060810
[   11.914225] cfg80211: Calling CRDA to update world regulatory domain
[   11.997446] IR RC5(x) protocol handler initialized
[   12.066660] IR RC6 protocol handler initialized
[   12.091515] IR JVC protocol handler initialized
[   12.167244] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[   12.173421] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.435368] i915 0000:00:02.0: setting latency timer to 64
[   12.435955] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   12.435967] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   12.435970] [drm] Driver supports precise vblank timestamp query.
[   12.436032] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.469919] IR Sony protocol handler initialized
[   12.588108] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   12.588123] Raw EDID:
[   12.588130]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   12.588138]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.588145]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.588152]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.588159]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.588166]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.588173]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.588181]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.637315] IR SANYO protocol handler initialized
[   12.717591] input: MCE IR Keyboard/Mouse (winbond-cir) as /devices/virtual/input/input5
[   12.717716] IR MCE Keyboard/mouse protocol handler initialized
[   12.724072] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   12.724086] Raw EDID:
[   12.724093]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   12.724101]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.724108]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.724116]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.724123]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.724130]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.724138]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.724145]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.777182] lirc_dev: IR Remote Control driver registered, major 249 
[   12.860049] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   12.860065] Raw EDID:
[   12.860075]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   12.860084]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.860092]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.860101]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.860110]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.860118]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.860127]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.860135]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.914224] rc rc0: lirc_dev: driver ir-lirc-codec (winbond-cir) registered at minor = 0
[   12.914229] IR LIRC bridge handler initialized
[   12.996051] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   12.996070] Raw EDID:
[   12.996079]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   12.996088]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996096]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996105]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996113]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996121]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996130]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996138]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.996153] i915 0000:00:02.0: LVDS-1: EDID block 0 invalid.
[   12.997760] [drm] initialized overlay support
[   13.027830] fbcon: inteldrmfb (fb0) is primary device
[   13.359217] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   13.359219] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   13.359305] iwl4965 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   13.402340] iwl4965 0000:03:00.0: device EEPROM VER=0x36, CALIB=0x5
[   13.402456] iwl4965 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.402533] iwl4965 0000:03:00.0: irq 48 for MSI/MSI-X
[   13.590427] iwl4965 0000:03:00.0: loaded firmware version 228.61.2.24
[   13.700173] Console: switching to colour frame buffer device 180x56
[   13.706363] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.706366] i915 0000:00:02.0: registered panic notifier
[   13.706550] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   13.707034] acpi device:23: registered as cooling_device2
[   13.707055] ACPI: Video Device [IGFX] (multi-head: yes  rom: no  post: no)
[   13.708000] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   13.708542] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.708682] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   13.972349] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   13.972532] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.034059] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'
[   14.265779] ppdev: user-space parallel port driver
[   14.848319] type=1400 audit(1382559792.652:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=657 comm="apparmor_parser"
[   14.848407] type=1400 audit(1382559792.652:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=671 comm="apparmor_parser"
[   14.848864] type=1400 audit(1382559792.652:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=657 comm="apparmor_parser"
[   14.848947] type=1400 audit(1382559792.652:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=671 comm="apparmor_parser"
[   14.849166] type=1400 audit(1382559792.652:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=657 comm="apparmor_parser"
[   14.849252] type=1400 audit(1382559792.652:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=671 comm="apparmor_parser"
[   14.849792] type=1400 audit(1382559792.652:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=756 comm="apparmor_parser"
[   14.850332] type=1400 audit(1382559792.652:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=756 comm="apparmor_parser"
[   14.850642] type=1400 audit(1382559792.652:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=756 comm="apparmor_parser"
[   15.633199] type=1400 audit(1382559793.436:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=780 comm="apparmor_parser"
[   15.796139] Bluetooth: Core ver 2.16
[   15.796173] NET: Registered protocol family 31
[   15.796176] Bluetooth: HCI device and connection manager initialized
[   15.796188] Bluetooth: HCI socket layer initialized
[   15.796192] Bluetooth: L2CAP socket layer initialized
[   15.796201] Bluetooth: SCO socket layer initialized
[   16.262358] Bluetooth: RFCOMM TTY layer initialized
[   16.262373] Bluetooth: RFCOMM socket layer initialized
[   16.262376] Bluetooth: RFCOMM ver 1.11
[   16.385664] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.385669] Bluetooth: BNEP filters: protocol multicast
[   16.385682] Bluetooth: BNEP socket layer initialized
[   17.543976] init: failsafe main process (814) killed by TERM signal
[   22.532648] audit_printk_skb: 3 callbacks suppressed
[   22.532653] type=1400 audit(1382559800.336:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=929 comm="apparmor_parser"
[   22.533218] type=1400 audit(1382559800.336:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=929 comm="apparmor_parser"
[   22.533530] type=1400 audit(1382559800.336:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=929 comm="apparmor_parser"
[   22.556537] type=1400 audit(1382559800.360:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=928 comm="apparmor_parser"
[   22.557010] type=1400 audit(1382559800.360:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=928 comm="apparmor_parser"
[   22.564598] type=1400 audit(1382559800.368:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=932 comm="apparmor_parser"
[   22.565255] type=1400 audit(1382559800.368:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=932 comm="apparmor_parser"
[   22.570252] type=1400 audit(1382559800.372:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=933 comm="apparmor_parser"
[   22.570927] type=1400 audit(1382559800.372:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=933 comm="apparmor_parser"
[   22.626698] type=1400 audit(1382559800.428:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=930 comm="apparmor_parser"
[   22.660360] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   22.764142] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
[   22.764309] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.764785] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.039540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.039925] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

---

### Post by oldfred on 2013-10-23
You are showing 23 sec and not much with longer times between tasks.
I am on my laptop now and it shows 38.5 sec as last entry.

Still better to have your own thread. And I asked in your other thread for Boot-Repair. It may give more details of your configuration. But Boot-Repair will not normally fix most Windows issues.

---

### Post by mmcl26554 on 2013-10-23
Well that's all there was in the log file, unless there is a page 2 that I didn't see.    I have been working with the "Boot Repair"  People and they are out of ideas.   I think it just won't work on the Gateway computer so I'm thinking of just giving up on it as a dual boot.   That would be ok by me but the 3 minute boot time to desktop gets kind of old.   If I can't fix that I'll just forget Ubuntu on that computer.   I'll think about it and probably start a new thread not in the beginner forum.    Thanks Fred!
Michael

---

### Post by oldfred on 2013-10-23
I so not see where you are getting a 3 minute boot time. Mine is 40 sec plus a little for grub & BIOS or under a minute total. Yours is showing 23 sec plus grub & BIOS??

Are you not able to boot liveDVD or flash drive and run Boot-Repair?

---

### Post by mmcl26554 on 2013-10-23
I can do all of the above!   In fact booting from a USB may be faster than from the internal drive.   The majority of the time is spent waiting for the Grub menu then maybe a minute or less to get to the desktop.  Strange indeed.  I have just done a fresh install today and the mbr is on the drive with Ubuntu, not on the Vista drive, but I don't think that should be involved in this problem.
Michael

---

### Post by oldfred on 2013-10-24
If you have multiple drives I always suggest keeping Windows boot loader on Windows drive and grub on Ubuntu drive.
The only time it takes a long time booting is when it runs fsck. And with ext4 fsck is also faster. But that is only every 40 or 60 reboots unless you have file system issues?
Or it can be that you have your Vista partition in fstab and it has issues mounting it? A chkdsk on NTFS partition may resolve that type of issue.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mmcl26554 on 2013-10-24
> **oldfred said:**
> If you have multiple drives I always suggest keeping Windows boot loader on Windows drive and grub on Ubuntu drive.
[HTML]I believe this is what I have done as grub is on the Ubuntu drive.   
The first time I did this I let it put the MBR on the windows drive and when
 Vista wouldn't boot I didn't know about the MBR repair program Vista has.   
 Now I know better and it wouldn't be a big problem to fix it.  But since you don't have to put it there I don't[/HTML]

The only time it takes a long time booting is when it runs fsck. And with ext4 fsck is also faster. But that is only every 40 or 60 reboots unless you have file system issues?
Or it can be that you have your Vista partition in fstab and it has issues mounting it? A chkdsk on NTFS partition may resolve that type of issue.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

[HTML]I'll try this.   Just to verify, you want me to boot from the USB thumb drive and run the commands 

sudo e2fsck -C0 -p -f -v /dev/sdb1
sudo e2fsck -f -y -v /dev/sdb1  

from a terminal,   correct?[/HTML]

Michael

---

### Post by oldfred on 2013-10-24
The example is sdb1, but you have to use the actual drive and partition(s) your install is on. If you have separate /home or data partitions that also are extX formatted you need to run on all partitions.

You can only run chkdsk from Windows with either its repair console when booting, if you can get to it or from a separate Windows repairCD or flash drive.

---

### Post by mmcl26554 on 2013-10-24
I have 2 drives, the Ubuntu has 2 partitions one for Ubuntu and one 5GB swap.   The Windows Vista drive just has that so running check disk is no problem at all.  And running the commands on the Ubuntu drive should be no problem either.  
Michael

---

### Post by mmcl26554 on 2013-11-02
I have reinstalled 12.04 lt as the only OS.  Then with both hard drives installed (Vista & Ubuntu) I select the OS with the F10 boot selection key.    I am giving up on trying to have Grub boot Vista, but Ubuntu still takes a full 3 minutes boot to the desktop.   I will start a new thread on this subject only and see if I can find some help.
Thank you to all of you who tried to assist me.   Even though we were not successful I did learn a lot.
Michael

---

### Post by mmcl26554 on 2013-11-02
I have reinstalled 12.04 lt as the only OS. Then with both hard drives installed (Vista & Ubuntu) I select the OS with the F10 boot selection key. I am giving up on trying to have Grub boot Vista, but Ubuntu still takes a full 3 minutes boot to the desktop. I will start a new thread on this subject only and see if I can find some help.
Thank you to all of you who tried to assist me. Even though we were not successful I did learn a lot.
Michael

---

