---
title: "External HDD Instalation Ubuntu 14.04"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by rickm1945 on 2014-05-06
I have a Toshiba 160GB External USB HD that has been formatted. I have Windows 7 on my Desktop and in My Computer it shows My Toshiba USB HDD as a Primary Drive. Can I install Ubuntu 14.04 on that drive and boot from it into Ubuntu? If I can how do I install? Thank you in advance for any help.

---

### Post by Bashing-om on 2014-05-06
rickm1945; Hi ! We can do this !

Sure you can install ubuntu onto that external hard drive.
Just be careful where the installer is going to install grub ( GRand Unified Bootloader ).

To be sure that we are all on the same page, show us the current hard disk situation(s), to preclude any errors.
From the liveUSB booted to the desktop; key combo ctl+alt+t yields a terminal interface to the operating system.
In this terminal execute the terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

```
and post that output - between code tags - back to us.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And precise guidance can be provided. It is but a matter of installing (Windows involved) in the proper mode and in the proper place,

[INDENT][INDENT]ain't nothing 
[INDENT][INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rickm1945 on 2014-05-06
I don't have Ubuntu Installed. I Have US  Ease Partition Master Pro. It showed drive C, and USB drives as both being primary drive.

---

### Post by Bashing-om on 2014-05-06
rickm1945; Wow

From this:
> 
Can I install Ubuntu 14.04 on that drive and boot from it into Ubuntu? 

I had "assumed" that you had an install medium.

Download the .iso file and burn to DVD. and in the liveDVD environment run the requested commands.

Me ->
[INDENT][INDENT]I be only linux literate
[/INDENT][/INDENT]

---

### Post by rickm1945 on 2014-05-07
This is what the commands returned.

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a427ea7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    24743935    12331008    7  HPFS/NTFS/exFAT
/dev/sda3        24743936  1953519615   964387840    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x307e65d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63   312576704   156288321    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD1001FAES-7 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  12.7GB  12.6GB  primary  ntfs         boot
 3      12.7GB  1000GB  988GB   primary  ntfs


Model: TOSHIBA MK1652GSX (scsi)
Disk /dev/sdf: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  160GB  160GB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD1001FAES-7 (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End          Size         Type     File system  Flags
 1      63s        80324s       80262s       primary  fat16        diag
 2      81920s     24743935s    24662016s    primary  ntfs         boot
 3      24743936s  1953519615s  1928775680s  primary  ntfs

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Error: Error opening /dev/sdb: No medium found                            
Retry/Cancel? retry                                                       
Error: Error opening /dev/sdb: No medium found                            
Retry/Cancel? 

---

### Post by Bashing-om on 2014-05-07
rickm1945; Top-a the morning to you;

OK, looking good.

Should be no problem to install to "sdf"  (!!). Why the drive is seen as 'sdf' I can not say, as I had expected it to be 'sdb'. Must be in relation to the usb port you have connected the external drive to.
The good thing is that it is recognized, -> partition table (msdos) is known, and file system is detected. There should exist no problem to install ubuntu onto that drive. There is now the decision as to how you want to install. As a standard default or "something else".
> 
Disk /dev/sdf: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
1 32.3kB 160GB 160GB primary ntfs boot


The easy thing to get ya installed, up and going is to do the standard install:
Boot the liveDVD play with the operating system to see if there "might" exist any difficulties or hardware problems, All is good ! Install !
I do endorse the standard install for the less knowledgeable. It is simple, straight forward, over and done.
In the liveDVD activate a terminal once more and MAKE sure the drive remains as recognized "sdf",, it could have mounted with a differing indentification.
check ! Terminal code:
```

sudo fdisk -lu

```
Click on the desktop's "install ubuntu" icon to start the installer.
Choose the option " erase disk and install ubuntu". The installer will do just that - wipe the disk - Save any data that may be on the hard drive at this time, any data is going to be history .The install wizard then takes care of everything, setting up the formatting and the partitioning; giving you the "root" partition, and an extended partition and in this extended partition the logical swap partition, easy peasy.
Point the installer to the drive that 'fdisk' shows as the 160 Gig drive (in this particular situation referred to as 'sdf').
I suggest NOT to check the boxes "install updates" or "install 3rd party software". The install will go much faster, and we have greater control if these actions are taken after the install is completed.
In the install process at the bottom of the install screen will be a popup of where grub is going to be installed -> make sure that 'sdf' and I do mean only the hard drive NOT a partition is selected. Installing grub to 'sdf' - as the drive 'fdisk' indicates - insures that the Windows' boot code on 'sda' remains untouched and permits you to boot Windows from your bios as a stand alone operating system. Installing grub to 'sdf' and setting bios priority to boot the external drive will give you the option to boot either ubuntu or windows - chainloading Windows onto grub's boot menu- ( by the time we are done with all the install).
Answer the few questions the install wizard asks -> identify keyboard, location, and account info and let the install complete, remove the disk -> reboot into the new install - bios set to boot the external drive.

Now booted into the install, let's complete the installation.
From the desktop key combo ctl+alt+t for a terminal:
Terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras ##if you want the non-free software ( codecs, flash, fonts and so on )
sudo update-grub ##will pick up Windows and add the entry to the boot menu.

```

Done ! You now have a true dual boot operating system.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-05-07
All the auto install options, install grub2's boot loader to sda. That is easily fixed with Boot-Repair as you want the Windows boot loader in the MBR of sda and grub in the MBR of the external.

The only way you can get the option on where to install grub2's boot loader is with Something Else or manual install. And then it is not as easy as you have to know and understand the partitions you need or want. Minimum is / (root) formatted ext4 of at least 10GB (20GB better) and swap of 2GB. A separate /home for your user settings and user data is suggested but not required. It should be larger than / but depends on how much data you may eventually want to save or if you are always saving data into your NTFS partition(s).

       Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by Bashing-om on 2014-05-07
@ oldfred, Thanks as always.

Not that I would dare disagree with you.
But,
I just recently did a (re-)install of release 12.04.1 standard desktop, erase disk and install. The option of where to install grub was indeed present as I did change the default from 'sda' to where I needed it, to 'sdc'.

Just for an update.

[INDENT][INDENT]my memory serves me right
[/INDENT][/INDENT]

---

### Post by rickm1945 on 2014-05-07
I tried to install like you said first and now the 160GB doesn't show in MY Computer. I can not access the USB drive at all. The install went through. I can't access the drive now, if I could I would format and start over.

---

### Post by oldfred on 2014-05-07
Windows will not show Linux partitions, so that is normal. 
Did you install to entire drive or shrink the NTFS partition?

May be best to see all the details.
Run the BootInfo report and post link.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

@bashing-om
Not sure I have ever done an auto-install as I always create partitions in advance with gparted. 
Where on install screen did the grub choice appear? A screen shot would be really good as then we could tell users exactly how to do it.

---

### Post by Bashing-om on 2014-05-07
@ oldfred; Yes.

As I have nothing to loose on that 12.04.1 .. at my earliest I will (re-)(re-)install and will at that time get us a screen shot.

As you have said
[INDENT][INDENT][INDENT]a picture is worth a thousand words
[/INDENT][/INDENT][/INDENT]

@ rickm1945; Umph.

Will await the results of the boot-repair text file. As a guess though I bet you did not pay attention to what 'fdisk' related for the device identification, and grub is not installed where you need it to be. - just a guess at this time -.

[INDENT][INDENT]ubuntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rickm1945 on 2014-05-08
I have never done a auto install either. I have allways created the partitions etc.

```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp8phfvmp1/secring.gpg' created
gpg: keyring `/tmp/tmp8phfvmp1/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp8phfvmp1/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty InRelease
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://archive.ubuntu.com trusty Release.gpg                               
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://archive.ubuntu.com trusty-updates Release.gpg
Ign http://ppa.launchpad.net trusty InRelease  
Hit http://archive.ubuntu.com trusty Release   
Hit http://archive.ubuntu.com trusty-updates Release                  
Hit http://security.ubuntu.com trusty-security Release.gpg            
Ign http://ppa.launchpad.net trusty Release.gpg                       
Hit http://archive.ubuntu.com trusty/main amd64 Packages             
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security Release
Ign http://ppa.launchpad.net trusty Release                           
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/main amd64 Packages   
Hit http://archive.ubuntu.com trusty/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US          
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US    
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
ubuntu@ubuntu:~$ 


```

---

### Post by rickm1945 on 2014-05-08
This is what is on the HDD:
```

/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/bin
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/boot
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/cdrom
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/dev
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/etc
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/home
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/lib
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/lib64
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/media
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/mnt
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/opt
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/proc
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/root
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/run
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/sbin
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/srv
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/sys
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/tmp
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/usr
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/var
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/initrd.img
/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/vmlinuz

```

---

### Post by rickm1945 on 2014-05-08
I have never done a auto install either. I have allways created the partitions etc.

```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp8phfvmp1/secring.gpg' created
gpg: keyring `/tmp/tmp8phfvmp1/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp8phfvmp1/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty InRelease
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Hit http://archive.ubuntu.com trusty Release.gpg                               
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://archive.ubuntu.com trusty-updates Release.gpg
Ign http://ppa.launchpad.net trusty InRelease  
Hit http://archive.ubuntu.com trusty Release   
Hit http://archive.ubuntu.com trusty-updates Release                  
Hit http://security.ubuntu.com trusty-security Release.gpg            
Ign http://ppa.launchpad.net trusty Release.gpg                       
Hit http://archive.ubuntu.com trusty/main amd64 Packages             
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security Release
Ign http://ppa.launchpad.net trusty Release                           
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/main amd64 Packages   
Hit http://archive.ubuntu.com trusty/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-en_US          
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US    
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
ubuntu@ubuntu:~$ 


```

---

### Post by rickm1945 on 2014-05-08
Boot repair return:

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
612
613
614
615
616
617
618
619
620
621
622
623
624
625
626
627
628
629
630
631
632
633
634
635
636
637
638
639
640
641
642
643
644
645
646
647
648
649
650
651
652
653
654
655
656
657
658
659
660
661
662
663
664
665
666
667
668
669
670
671
672
673
674
675
676
677
678
679
680
681
682
683
684
685
686
687
688
689
690
691
692
693
694
695
696
697
698
699
700
701
702
703
704
705
706
707
708
709
710
711
712
713
714
715
716
717
718
719
720
721
722
723
724
725
726
727
728
729
730
731
732
733
734
735
736
737
738
739
740
741
742
743
744
745
746
747
748
749
750
751
752
753
754
755
756
757
758
759
760
761
762
763
764
765
766
767
768
769
770
771
772
[/TD]
[TD="class: code"] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdf and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdf2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdf5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    24,743,935    24,662,016   7 NTFS / exFAT / HPFS
/dev/sda3          24,743,936 1,953,519,615 1,928,775,680   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          2,048   295,952,383   295,950,336  83 Linux
/dev/sdf2         295,954,430   312,580,095    16,625,666   5 Extended
/dev/sdf5         295,954,432   312,580,095    16,625,664  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        5E28914828911FD7                       ntfs       RECOVERY
/dev/sda3        AA00AF6000AF31ED                       ntfs       OS
/dev/sdf1        c7732974-d9f4-45f9-bb47-dcf53bc15f51   ext4       
/dev/sdf5        b7ddbcb2-97f7-40ca-9f90-be8dc8a32486   swap       
/dev/sr0                                                iso9660    Ubuntu 14.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51 ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdf1/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

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
set root='hd5,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  c7732974-d9f4-45f9-bb47-dcf53bc15f51
else
  search --no-floppy --fs-uuid --set=root c7732974-d9f4-45f9-bb47-dcf53bc15f51
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
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-c7732974-d9f4-45f9-bb47-dcf53bc15f51' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd5,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  c7732974-d9f4-45f9-bb47-dcf53bc15f51
	else
	  search --no-floppy --fs-uuid --set=root c7732974-d9f4-45f9-bb47-dcf53bc15f51
	fi
	linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=c7732974-d9f4-45f9-bb47-dcf53bc15f51 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-c7732974-d9f4-45f9-bb47-dcf53bc15f51' {
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-c7732974-d9f4-45f9-bb47-dcf53bc15f51' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd5,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  c7732974-d9f4-45f9-bb47-dcf53bc15f51
		else
		  search --no-floppy --fs-uuid --set=root c7732974-d9f4-45f9-bb47-dcf53bc15f51
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=c7732974-d9f4-45f9-bb47-dcf53bc15f51 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-c7732974-d9f4-45f9-bb47-dcf53bc15f51' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd5,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  c7732974-d9f4-45f9-bb47-dcf53bc15f51
		else
		  search --no-floppy --fs-uuid --set=root c7732974-d9f4-45f9-bb47-dcf53bc15f51
		fi
		echo	'Loading Linux 3.13.0-24-generic ...'
		linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=c7732974-d9f4-45f9-bb47-dcf53bc15f51 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-24-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd5,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  c7732974-d9f4-45f9-bb47-dcf53bc15f51
	else
	  search --no-floppy --fs-uuid --set=root c7732974-d9f4-45f9-bb47-dcf53bc15f51
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd5,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd5,msdos1 --hint-efi=hd5,msdos1 --hint-baremetal=ahci5,msdos1  c7732974-d9f4-45f9-bb47-dcf53bc15f51
	else
	  search --no-floppy --fs-uuid --set=root c7732974-d9f4-45f9-bb47-dcf53bc15f51
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-5E28914828911FD7' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  5E28914828911FD7
	else
	  search --no-floppy --fs-uuid --set=root 5E28914828911FD7
	fi
	parttool ${root} hidden-
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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

=============================== sdf1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdf1 during installation
UUID=c7732974-d9f4-45f9-bb47-dcf53bc15f51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
UUID=b7ddbcb2-97f7-40ca-9f90-be8dc8a32486 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdf5

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 00 08  00 00 00 a8 fd 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-Aox9tRP3/Tmp_Log: No such file or directory
File descriptor 9 (/proc/7049/mounts) leaked on lvscan invocation. Parent PID 16619: bash
File descriptor 63 (pipe:[269523]) leaked on lvscan invocation. Parent PID 16619: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-05-08__05h07 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

=================== os-prober:
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sdf1:Ubuntu 14.04 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda2: LABEL="RECOVERY" UUID="5E28914828911FD7" TYPE="ntfs"
/dev/sda3: LABEL="OS" UUID="AA00AF6000AF31ED" TYPE="ntfs"
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660"
/dev/sdf1: UUID="c7732974-d9f4-45f9-bb47-dcf53bc15f51" TYPE="ext4"
/dev/sdf5: UUID="b7ddbcb2-97f7-40ca-9f90-be8dc8a32486" TYPE="swap"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

XP not detected by os-prober on sda3. Please report this message to boot.repair@gmail.com
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 16 21:26 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11 06:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 11:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 06:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 06:51 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 08:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 06:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 06:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 06:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 06:51 41_custom
-rw-r--r-- 1 root root   483 Apr 11 06:51 README




=================== /media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51/etc/default/grub :

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
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda3.
sdf1	: sdf,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	63 sectors * 512 bytes
sdf	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD1001FAES-7 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
2      41.9MB  12.7GB  12.6GB  primary  ntfs         boot
3      12.7GB  1000GB  988GB   primary  ntfs


Model: TOSHIBA MK1652GSX (scsi)
Disk /dev/sdf: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  152GB  152GB   primary   ext4            boot
2      152GB   160GB  8512MB  extended
5      152GB   160GB  8512MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA WDC WD1001FAES-7;
1:32.3kB:41.1MB:41.1MB:fat16::diag;
2:41.9MB:12.7GB:12.6GB:ntfs::boot;
3:12.7GB:1000GB:988GB:ntfs::;

BYT;
/dev/sdf:160GB:scsi:512:512:msdos:TOSHIBA MK1652GSX;
1:1049kB:152GB:152GB:ext4::boot;
2:152GB:160GB:8512MB:::;
5:152GB:160GB:8512MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
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
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdf1 on /media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdf1 sdf2 sdf5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdc sdd sde sdf sdf1 sdf2 sdf5 sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vga_arbiter vhost-net watchdog watchdog0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  83 39 01 00 80 01 29 30  30 30 30 44 65 6c 6c 55  |.9....)0000DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 40 01 00  |........?....@..|
00000020  00 00 00 00 80 00 80 00  ff 4f 78 01 00 00 00 00  |.........Ox.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d7 1f 91 28 48 91 28 5e  |...........(H.(^|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 90 79 01  |........?.....y.|
00000020  00 00 00 00 80 00 80 00  ff c7 f6 72 00 00 00 00  |...........r....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ed 31 af 00 60 af 00 aa  |.........1..`...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  126M  3.8G   4% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      792M  1.3M  791M   1% /run
/dev/sr0       iso9660    964M  964M     0 100% /cdrom
/dev/loop0     squashfs   923M  923M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G  1.2M  3.9G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      3.9G   80K  3.9G   1% /run/shm
none           tmpfs      100M   52K  100M   1% /run/user
/dev/sdf1      ext4       139G  3.3G  129G   3% /media/ubuntu/c7732974-d9f4-45f9-bb47-dcf53bc15f51
/dev/sda1      vfat        40M  8.9M   31M  23% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     12G  6.6G  5.3G  56% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    920G   95G  825G  11% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a427ea7

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    24743935    12331008    7  HPFS/NTFS/exFAT
/dev/sda3        24743936  1953519615   964387840    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009663e

Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048   295952383   147975168   83  Linux
/dev/sdf2       295954430   312580095     8312833    5  Extended
/dev/sdf5       295954432   312580095     8312832   82  Linux swap / Solaris


User choice: Is sdf (160GB) a removable disk? yes
Partition outside the disk detected.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on the removable disk!

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdf1 into the MBR of sdf.
It would also fix access to other systems (other MBRs) for the situations when the removable media is disconnected.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

 [/TD]
[/TR]
[/TABLE]
  [Download as text]("http://paste.ubuntu.com/7414934/plain/")
```

---

### Post by rickm1945 on 2014-05-08
Yes, I used the entire drive. I showed 2 partitions and I adjusted them to what I thought they should be. I then proceeded with the install.

---

### Post by oldfred on 2014-05-08
I do not see anything wrong.

If you in BIOS choose to boot from external does it boot?
If you want to be able to write files from Windows, you need to shrink / (root) sda1 and create a new NTFS partition for shared data.

Your sda3 is not showing the Windows execute able. I assume Windows works, so it is just BootInfo report did not see it?

---

### Post by monkeybrain20122 on 2014-05-08
BTW, you can boot that drive off any computer with compatible hardware (set to boot from usb drive of course ), not just your desktop with which you did the installation. so it is a portable installation.

---

### Post by rickm1945 on 2014-05-08
I guess I was hoping for a dual boot situation. I had dual boot with 12.04. I just didn't want to take up the space on the c: drive. I want to use Ubuntu to edit photos with GIMP and UFRaw the raw photo editor. I really don't like the idea of having to go into Boot Sequence just to be able o run Ubuntu 14.04. Any way around that. I can Boot into the USB drive but it is a pain in the kisster.I am late today I have Chemo on Thursdays.

---

### Post by Bashing-om on 2014-05-08
rickm1945; Eating crow,

I Have gone back at looked at the procedure I directed you to use, and I am in error -- I do apologize that due to my mis-direction you are in this situation. The "erase  disk and install ubuntu" as oldfred did so say, does not provide the means to install grub to a place of choice in that initial install screen ! In my case I had pre-partitioned the hard drive and had used the "something else" choice in that install ( such that th choice of grub's install is available). sheeshh, sorry to mis-direct you.

@ oldfred, I do so stand corrected in my thinking - and my poor confused memory -, next time I try and tell grampaw how to suck eggs, I will take much greater care in what I think. I do appreciate your continued efforts to educate me.


@ rickm1945,

see oldfred's suggestion to create a shared data partition.
In respect to your last:
> 
Any way around that.

 As is now, you can boot either operating system by resetting the boot priority in bios. If it is your desire to have the ability to boot either Windows or ubuntu from the Windows' hard drive, well, we can install ubuntu's boot manager to the sda drive. But that does mean that in the future if that boot code is damaged, one will have to resort to Windows repair disk to (re-)install Windows boot code . May not ever be a problem, and may not be a big deal to you in that event, but the possibility is there.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-05-08
You should be able to set BIOS to boot USB first, internal hard drive second.
And in grub menu have the option to boot either system.
But if external is unplugged then BIOS will skip that and just boot internal hard drive.

@Bashing-om
No need to apologize. My 2 yr old grandson has yet to figure that grandpa does not know it all. Things are changing very rapidly with these new systems and every vendor seems to have implemented the UEFI 'standard' differently. And there are so many versions & flavors of Ubuntu I cannot keep the straight myself. I only have Ubuntu with fallback/flashback and try to pick up from other threads/posts other useful info myself.

---

### Post by rickm1945 on 2014-05-09
@oldfed My old feeble mind is not sure I' following you. I understand booting from the F12 on my computer. (Boot setting), but I'm not sure about what or how to use "Grub options menu. If I edit Grub, are you saying that when I boot that I will have option on screen to boot into either of them? If that is what you mean how do I accomplish that feat?:)

I changed boot sequence and iss in theory acting like a dual boot sysem. This is wha I was wanting and I appreciateYou and Bashing-om's help. I had 12.04 on a laptop with I no longer have install choose was "something else" and install was flawless. This istall was flawless as well and I am satisified with the results thanks to you guys. Your help is greatly appreciated and thanks for your patience.
[SOLVED]

---

