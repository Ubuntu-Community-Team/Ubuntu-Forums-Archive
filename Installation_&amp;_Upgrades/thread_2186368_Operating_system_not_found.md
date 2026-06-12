---
title: "Operating system not found"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by Abo El Nile on 2013-11-07
Hello ;

  I faced a problem while repair my laptop that can not find operating system after install ubuntu 12.4

       -i found on ubuntu forum that the problem can be fixed by Boot Repair and i try it and not fixed till now
       -and i tried to install ubuntu 10 & 11 and have the same problem 
       -i found that BOOTMGR is missing and cant fix it
       -and when i put CD windows XP in the CD room it works good    
       -if windows CD not in CD room not work 

so  i hope that you can help me to solve this problem 

Thanks;

---

### Post by TheFu on 2013-11-07
Please run boot-info and post the link with the results.  See my signature for a link.  I believe boot-repair can create that same output.

---

### Post by leclerc65 on 2013-11-07
My (un)educated guess is you have more than one HDD, the partition of the one you installed Ubuntu on has no boot tag. You can fix the tag with GParted.

---

### Post by Abo El Nile on 2013-11-07
Thanks for fast Replay 
here is the [COLOR=#000000]boot-info data

[/COLOR]**Ubuntu Pastebin**

**Paste from boot-repair at Thu, 7 Nov 2013 12:55:40 +0000**

[COLOR=#000000][FONT=Verdana]```
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
481[/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 6Nov2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 1 [COLOR=#AA22FF]**for**[/COLOR] /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048    78,125,055    78,123,008  83 Linux
/dev/sda2          78,127,102   234,440,703   156,313,602   5 Extended
/dev/sda5          85,940,224   234,440,703   148,500,480  83 Linux
/dev/sda6          78,127,104    85,940,223     7,813,120  82 Linux swap / Solaris


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        77b1fd26-632c-43ae-a63b-9aa237261fec   ext4       
/dev/sda5        822b820f-8152-435a-8e49-078c20cfb2d2   ext4       
/dev/sda6        1aa59a96-65d6-43ea-8001-30187b66d56d   [COLOR=#B8860B]swap[/COLOR]       

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/sda5        /home                    ext4       [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
[COLOR=#666666]}[/COLOR]

insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
[COLOR=#AA22FF]**if **[/COLOR]loadfont /usr/share/grub/unicode.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
  search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR]/boot/grub/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#AA22FF]**if **[/COLOR]background_color 44,0,30; [COLOR=#AA22FF]**then**[/COLOR]
clear
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"$1"[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"$1"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#AA22FF]**}**[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"$linux_gfx_mode"[/COLOR] ![COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"text"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]load_video; [COLOR=#AA22FF]**fi**[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic-pae'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
    linux    /boot/vmlinuz-3.2.0-55-generic-pae [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]77b1fd26-632c-43ae-a63b-9aa237261fec ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.2.0-55-generic-pae
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic-pae (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.2.0-55-generic-pae ...'[/COLOR]
    linux    /boot/vmlinuz-3.2.0-55-generic-pae [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]77b1fd26-632c-43ae-a63b-9aa237261fec ro recovery nomodeset 
    [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
    initrd    /boot/initrd.img-3.2.0-55-generic-pae
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_memtest86+ ###*[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+)"[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
    linux16    /boot/memtest86+.bin
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+, serial console 115200)"[/COLOR] [COLOR=#666666]{[/COLOR]
    insmod part_msdos
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
    search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
    linux16    /boot/memtest86+.bin [COLOR=#B8860B]console[/COLOR][COLOR=#666666]=[/COLOR]ttyS0,115200n8
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_memtest86+ ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sda1/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=#008800]*# / was on /dev/sda1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]77b1fd26-632c-43ae-a63b-9aa237261fec /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# /home was on /dev/sda5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]822b820f-8152-435a-8e49-078c20cfb2d2 /home           ext4    defaults        0       2
[COLOR=#008800]*# swap was on /dev/sda6 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]1aa59a96-65d6-43ea-8001-30187b66d56d none            swap    sw              0       0
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

  20.131668091 [COLOR=#666666]=[/COLOR] 21.616214016   boot/grub/grub.cfg                             1
  32.212451935 [COLOR=#666666]=[/COLOR] 34.587856896   boot/grub/core.img                             1
   1.146289825 [COLOR=#666666]=[/COLOR] 1.230819328    boot/vmlinuz-3.2.0-55-generic-pae              1
   1.146289825 [COLOR=#666666]=[/COLOR] 1.230819328    vmlinuz                                        1
   1.287635803 [COLOR=#666666]=[/COLOR] 1.382588416    boot/initrd.img-3.2.0-55-generic-pae           1
   1.287635803 [COLOR=#666666]=[/COLOR] 1.382588416    initrd.img                                     [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sda2

00000000  de 81 2a cc f8 47 33 74  1f 53 99 e6 3d cf c9 10  |..*..G3t.S..[COLOR=#666666]=[/COLOR]...|
00000010  e3 c9 2f ef d7 50 1a fd  0d e7 74 1b 84 a6 17 be  |../..P....t.....|
00000020  7e e1 30 7e 9f 8d 9b 8a  6e 01 92 67 48 2f 0a 98  |~.0~....n..gH/..|
00000030  04 4f 9e 8b 90 28 7c 3e  22 38 66 5e 3c 09 a8 27  |.O...[COLOR=#666666]([/COLOR]|>[COLOR=#BB4444]"8f^<..'|[/COLOR]
[COLOR=#BB4444]00000040  4d 1b 19 f1 b8 83 b0 74  40 af 57 f2 1d e9 a7 ec  |M......t@.W.....|[/COLOR]
[COLOR=#BB4444]00000050  3b 02 2f ae 82 f8 5a 83  ae 19 38 f6 61 73 e5 eb  |;./...Z...8.as..|[/COLOR]
[COLOR=#BB4444]00000060  b6 8d fb 5c b5 d0 cf 3a  ea d0 0c 73 cc 96 d6 b0  |...\...:...s....|[/COLOR]
[COLOR=#BB4444]00000070  6d a8 ae c4 c9 5c 43 db  ce 8f 87 82 fb 92 4e c3  |m....\C.......N.|[/COLOR]
[COLOR=#BB4444]00000080  63 a8 bc 88 cc a2 74 cd  8b 77 9c 37 44 88 da 08  |c.....t..w.7D...|[/COLOR]
[COLOR=#BB4444]00000090  63 65 41 f5 4b 6e fa 53  42 e2 47 02 6f f8 c2 c3  |ceA.Kn.SB.G.o...|[/COLOR]
[COLOR=#BB4444]000000a0  aa 05 79 fd f3 54 20 12  36 b1 b5 a0 8e 9d b0 f9  |..y..T .6.......|[/COLOR]
[COLOR=#BB4444]000000b0  83 de 33 2d ce ca f0 b3  ca 30 79 68 2b de eb a2  |..3-.....0yh+...|[/COLOR]
[COLOR=#BB4444]000000c0  94 2d 4b ab 0b 8d 40 6a  51 51 6c d2 83 69 ef 90  |.-K...@jQQl..i..|[/COLOR]
[COLOR=#BB4444]000000d0  b8 85 22 b7 38 4d 9e c7  85 a3 2c df 3b 08 08 86  |.."[/COLOR].8M....,.;...|
000000e0  31 8d 62 82 70 be 9f 91  b3 c7 7f f4 09 7b c4 13  |1.b.p........[COLOR=#666666]{[/COLOR]..|
000000f0  0d a0 70 a7 e9 dc 83 f8  04 ec ed 59 00 04 ca d4  |..p........Y....|
00000100  4a a3 93 b5 5e 9b 28 1d  ec 26 b2 3f fd 1c 8c 56  |J...^.[COLOR=#666666]([/COLOR]..&.?...V|
00000110  62 bc 14 82 9e b4 ca a0  65 b7 a5 b3 de cf 2a 60  |b.......e.....*[COLOR=#BB4444]`[/COLOR]|
00000120  cc ce 01 36 8c ca 56 21  17 76 6b ef a1 4c 4c 7c  |...6..V!.vk..LL||
00000130  9a 0c af 3b 90 be c8 27  51 8a a3 5e 3f bc db 4b  |...;...[COLOR=#BB4444]'Q..^?..K|[/COLOR]
[COLOR=#BB4444]00000140  24 71 ad 2d 2d d6 ef 79  32 27 26 74 47 8e 61 6e  |$q.--..y2'[/COLOR]&tG.an|
00000150  c1 97 87 af 9b d2 76 c8  77 a9 cc 03 67 a1 45 6f  |......v.w...g.Eo|
00000160  7c 45 6f 84 6b 4b 70 30  d8 f8 12 cf af f8 7e 1a  [COLOR=#666666]||[/COLOR]Eo.kKp0......~.|
00000170  96 b9 69 4c 9b 67 25 [COLOR=#AA22FF]cd  [/COLOR]98 d7 19 e4 69 86 95 50  |..iL.g%.....i..P|
00000180  35 68 ba 9d f4 26 e4 d2  67 af dd db dd cb 30 6b  |5h...&..g.....0k|
00000190  7d 6b 97 7b 55 dc 3d 71  19 a1 e8 0b 1a 76 e7 e6  |[COLOR=#666666]}[/COLOR]k.[COLOR=#666666]{[/COLOR]U.[COLOR=#666666]=[/COLOR]q.....v..|
000001a0  ee 00 3b a6 af 29 27 51  63 13 af 6d fd 9b ea 82  |..;..[COLOR=#666666])[/COLOR][COLOR=#BB4444]'Qc..m....|[/COLOR]
[COLOR=#BB4444]000001b0  f7 4e a0 d9 9c d5 90 95  f2 f8 69 0d 6c 0f 00 fe  |.N........i.l...|[/COLOR]
[COLOR=#BB4444]000001c0  ff ff 83 fe ff ff 02 38  77 00 00 f0 d9 08 00 fe  |.......8w.......|[/COLOR]
[COLOR=#BB4444]000001d0  ff ff 05 fe ff ff 01 00  00 00 01 38 77 00 00 00  |...........8w...|[/COLOR]
[COLOR=#BB4444]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]



[COLOR=#BB4444]ADDITIONAL INFORMATION :[/COLOR]
[COLOR=#BB4444]=================== log of boot-repair 2013-11-07__14h55 ===================[/COLOR]
[COLOR=#BB4444]boot-repair version : 3.199~ppa36~precise[/COLOR]
[COLOR=#BB4444]boot-sav version : 3.199~ppa36~precise[/COLOR]
[COLOR=#BB4444]glade2script version : 3.2.2~ppa45~precise[/COLOR]
[COLOR=#BB4444]boot-sav-extra version : 3.199~ppa36~precise[/COLOR]
[COLOR=#BB4444]boot-repair is executed in installed-session (Ubuntu 12.04 LTS, precise, Ubuntu, i686)[/COLOR]
[COLOR=#BB4444]CPU op-mode(s):        32-bit[/COLOR]
[COLOR=#BB4444]BOOT_IMAGE=/boot/vmlinuz-3.2.0-55-generic-pae root=UUID=77b1fd26-632c-43ae-a63b-9aa237261fec ro quiet splash vt.handoff=7[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda1:The OS now in use - Ubuntu 12.04 LTS CurrentSession:linux[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/sda1: UUID="77b1fd26-632c-43ae-a63b-9aa237261fec" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sda5: UUID="822b820f-8152-435a-8e49-078c20cfb2d2" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sda6: UUID="1aa59a96-65d6-43ea-8001-30187b66d56d" TYPE="swap"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Warning: extended partition does not start at a cylinder boundary.[/COLOR]
[COLOR=#BB4444]DOS and Linux will interpret the contents differently.[/COLOR]

[COLOR=#BB4444]=================== /etc/grub.d/ :[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root     4096 Apr 23  2012 grub.d[/COLOR]
[COLOR=#BB4444]total 56[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6715 Apr 17  2012 00_header[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 5522 Apr 17  2012 05_debian_theme[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7399 Apr 17  2012 10_linux[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6335 Apr 17  2012 20_linux_xen[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7603 Apr 17  2012 30_os-prober[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  214 Apr 17  2012 40_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   95 Apr 17  2012 41_custom[/COLOR]
[COLOR=#BB4444]-rw-r--r-- 1 root root  483 Apr 17  2012 README[/COLOR]




[COLOR=#BB4444]=================== /etc/default/grub :[/COLOR]

[COLOR=#BB4444]# If you change this file, run '[/COLOR]update-grub[COLOR=#BB4444]' afterwards to update[/COLOR]
[COLOR=#BB4444]# /boot/grub/grub.cfg.[/COLOR]
[COLOR=#BB4444]# For full documentation of the options in this file, see:[/COLOR]
[COLOR=#BB4444]#   info -f grub -n '[/COLOR]Simple configuration[COLOR=#BB4444]'[/COLOR]

[COLOR=#BB4444]GRUB_DEFAULT=0[/COLOR]
[COLOR=#BB4444]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT_QUIET=true[/COLOR]
[COLOR=#BB4444]GRUB_TIMEOUT=10[/COLOR]
[COLOR=#BB4444]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX=""[/COLOR]

[COLOR=#BB4444]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR]
[COLOR=#BB4444]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR]
[COLOR=#BB4444]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR]
[COLOR=#BB4444]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/COLOR]

[COLOR=#BB4444]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR]
[COLOR=#BB4444]#GRUB_TERMINAL=console[/COLOR]

[COLOR=#BB4444]# The resolution used on graphical terminal[/COLOR]
[COLOR=#BB4444]# note that you can use only modes which your graphic card supports via VBE[/COLOR]
[COLOR=#BB4444]# you can see them in real GRUB with the command `vbeinfo'[/COLOR]
[COLOR=#B8860B]GRUB_GFXMODE[/COLOR][COLOR=#666666]=[/COLOR]640x480

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This installed-session is not EFI-compatible.
SecureBoot disabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA FUJITSU MHV2120B [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 120GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  40.0GB  40.0GB  primary   ext4            boot
2      40.0GB  120GB   80.0GB  extended
6      40.0GB  44.0GB  4000MB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]
5      44.0GB  120GB   76.0GB  logical   [COLOR=#B8860B]ext4[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA FUJITSU MHV2120B;
1:1049kB:40.0GB:40.0GB:ext4::boot;
2:40.0GB:120GB:80.0GB:::;
6:40.0GB:44.0GB:4000MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
5:44.0GB:120GB:76.0GB:ext4::;


[COLOR=#666666]===================[/COLOR] mount:
/dev/sda1 on / [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
/dev/sda5 on /home [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
gvfs-fuse-daemon on /home/mahmoudahmed/.gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfs-fuse-daemon [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]mahmoudahmed[COLOR=#666666])[/COLOR]
gvfs-fuse-daemon on /root/.gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfs-fuse-daemon [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse fw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sg0 shm snapshot snd stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vboxusb vga_arbiter zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       37G  2.7G   33G   8% /
udev           devtmpfs  489M   12K  489M   1% /dev
tmpfs          tmpfs     199M  788K  198M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     497M  152K  496M   1% /run/shm
/dev/sda5      ext4       70G  2.8G   64G   5% /home

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x0005a21d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    78125055    39061504   83  Linux
/dev/sda2        78127102   234440703    78156801    5  Extended
/dev/sda5        85940224   234440703    74250240   83  Linux
/dev/sda6        78127104    85940223     3906560   82  Linux swap / Solaris

Partition table entries are not in disk [COLOR=#B8860B]order[/COLOR]



[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.
```



No change has been performed on your computer.
[/COLOR][/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]

---

### Post by TheFu on 2013-11-07
Please **edit the post** with the boot-info data ... and wrap the output in "code" tags ... "Adv Reply" has those. Much easier to read when things are aligned as intended.

---

### Post by Abo El Nile on 2013-11-07
```
[h=1]Ubuntu Pastebin[/h][h=1]Paste from boot-repair at Thu, 7 Nov 2013 12:55:40 +0000[/h][COLOR=#000000][FONT=Verdana][Download as text]("http://paste.ubuntu.com/6376187/plain/")[TABLE="class: pastetable"]
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
[/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 6Nov2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 1 [COLOR=#AA22FF]**for**[/COLOR] /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048    78,125,055    78,123,008  83 Linux
/dev/sda2          78,127,102   234,440,703   156,313,602   5 Extended
/dev/sda5          85,940,224   234,440,703   148,500,480  83 Linux
/dev/sda6          78,127,104    85,940,223     7,813,120  82 Linux swap / Solaris


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        77b1fd26-632c-43ae-a63b-9aa237261fec   ext4       
/dev/sda5        822b820f-8152-435a-8e49-078c20cfb2d2   ext4       
/dev/sda6        1aa59a96-65d6-43ea-8001-30187b66d56d   [COLOR=#B8860B]swap[/COLOR]       

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/sda5        /home                    ext4       [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]  [/COLOR]load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
[COLOR=#666666]}[/COLOR]

insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
[COLOR=#AA22FF]**if **[/COLOR]loadfont /usr/share/grub/unicode.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
  search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR]/boot/grub/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#AA22FF]**if **[/COLOR]background_color 44,0,30; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR]clear
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"$1"[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"$1"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#AA22FF]**}**[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**        **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**        **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]**      **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"$linux_gfx_mode"[/COLOR] ![COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"text"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]load_video; [COLOR=#AA22FF]**fi**[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic-pae'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
	linux	/boot/vmlinuz-3.2.0-55-generic-pae [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]77b1fd26-632c-43ae-a63b-9aa237261fec ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-55-generic-pae
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic-pae (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Loading Linux 3.2.0-55-generic-pae ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-55-generic-pae [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]77b1fd26-632c-43ae-a63b-9aa237261fec ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-55-generic-pae
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_memtest86+ ###*[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+)"[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
	linux16	/boot/memtest86+.bin
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+, serial console 115200)"[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 77b1fd26-632c-43ae-a63b-9aa237261fec
	linux16	/boot/memtest86+.bin [COLOR=#B8860B]console[/COLOR][COLOR=#666666]=[/COLOR]ttyS0,115200n8
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_memtest86+ ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sda1/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=#008800]*# / was on /dev/sda1 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]77b1fd26-632c-43ae-a63b-9aa237261fec /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# /home was on /dev/sda5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]822b820f-8152-435a-8e49-078c20cfb2d2 /home           ext4    defaults        0       2
[COLOR=#008800]*# swap was on /dev/sda6 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]1aa59a96-65d6-43ea-8001-30187b66d56d none            swap    sw              0       0
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

  20.131668091 [COLOR=#666666]=[/COLOR] 21.616214016   boot/grub/grub.cfg                             1
  32.212451935 [COLOR=#666666]=[/COLOR] 34.587856896   boot/grub/core.img                             1
   1.146289825 [COLOR=#666666]=[/COLOR] 1.230819328    boot/vmlinuz-3.2.0-55-generic-pae              1
   1.146289825 [COLOR=#666666]=[/COLOR] 1.230819328    vmlinuz                                        1
   1.287635803 [COLOR=#666666]=[/COLOR] 1.382588416    boot/initrd.img-3.2.0-55-generic-pae           1
   1.287635803 [COLOR=#666666]=[/COLOR] 1.382588416    initrd.img                                     [COLOR=#B8860B]1[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sda2

00000000  de 81 2a cc f8 47 33 74  1f 53 99 e6 3d cf c9 10  |..*..G3t.S..[COLOR=#666666]=[/COLOR]...|
00000010  e3 c9 2f ef d7 50 1a fd  0d e7 74 1b 84 a6 17 be  |../..P....t.....|
00000020  7e e1 30 7e 9f 8d 9b 8a  6e 01 92 67 48 2f 0a 98  |~.0~....n..gH/..|
00000030  04 4f 9e 8b 90 28 7c 3e  22 38 66 5e 3c 09 a8 27  |.O...[COLOR=#666666]([/COLOR]|>[COLOR=#BB4444]"8f^<..'|[/COLOR]
[COLOR=#BB4444]00000040  4d 1b 19 f1 b8 83 b0 74  40 af 57 f2 1d e9 a7 ec  |M......t@.W.....|[/COLOR]
[COLOR=#BB4444]00000050  3b 02 2f ae 82 f8 5a 83  ae 19 38 f6 61 73 e5 eb  |;./...Z...8.as..|[/COLOR]
[COLOR=#BB4444]00000060  b6 8d fb 5c b5 d0 cf 3a  ea d0 0c 73 cc 96 d6 b0  |...\...:...s....|[/COLOR]
[COLOR=#BB4444]00000070  6d a8 ae c4 c9 5c 43 db  ce 8f 87 82 fb 92 4e c3  |m....\C.......N.|[/COLOR]
[COLOR=#BB4444]00000080  63 a8 bc 88 cc a2 74 cd  8b 77 9c 37 44 88 da 08  |c.....t..w.7D...|[/COLOR]
[COLOR=#BB4444]00000090  63 65 41 f5 4b 6e fa 53  42 e2 47 02 6f f8 c2 c3  |ceA.Kn.SB.G.o...|[/COLOR]
[COLOR=#BB4444]000000a0  aa 05 79 fd f3 54 20 12  36 b1 b5 a0 8e 9d b0 f9  |..y..T .6.......|[/COLOR]
[COLOR=#BB4444]000000b0  83 de 33 2d ce ca f0 b3  ca 30 79 68 2b de eb a2  |..3-.....0yh+...|[/COLOR]
[COLOR=#BB4444]000000c0  94 2d 4b ab 0b 8d 40 6a  51 51 6c d2 83 69 ef 90  |.-K...@jQQl..i..|[/COLOR]
[COLOR=#BB4444]000000d0  b8 85 22 b7 38 4d 9e c7  85 a3 2c df 3b 08 08 86  |.."[/COLOR].8M....,.;...|
000000e0  31 8d 62 82 70 be 9f 91  b3 c7 7f f4 09 7b c4 13  |1.b.p........[COLOR=#666666]{[/COLOR]..|
000000f0  0d a0 70 a7 e9 dc 83 f8  04 ec ed 59 00 04 ca d4  |..p........Y....|
00000100  4a a3 93 b5 5e 9b 28 1d  ec 26 b2 3f fd 1c 8c 56  |J...^.[COLOR=#666666]([/COLOR]..&.?...V|
00000110  62 bc 14 82 9e b4 ca a0  65 b7 a5 b3 de cf 2a 60  |b.......e.....*[COLOR=#BB4444]`[/COLOR]|
00000120  cc ce 01 36 8c ca 56 21  17 76 6b ef a1 4c 4c 7c  |...6..V!.vk..LL||
00000130  9a 0c af 3b 90 be c8 27  51 8a a3 5e 3f bc db 4b  |...;...[COLOR=#BB4444]'Q..^?..K|[/COLOR]
[COLOR=#BB4444]00000140  24 71 ad 2d 2d d6 ef 79  32 27 26 74 47 8e 61 6e  |$q.--..y2'[/COLOR]&tG.an|
00000150  c1 97 87 af 9b d2 76 c8  77 a9 cc 03 67 a1 45 6f  |......v.w...g.Eo|
00000160  7c 45 6f 84 6b 4b 70 30  d8 f8 12 cf af f8 7e 1a  [COLOR=#666666]||[/COLOR]Eo.kKp0......~.|
00000170  96 b9 69 4c 9b 67 25 [COLOR=#AA22FF]cd  [/COLOR]98 d7 19 e4 69 86 95 50  |..iL.g%.....i..P|
00000180  35 68 ba 9d f4 26 e4 d2  67 af dd db dd cb 30 6b  |5h...&..g.....0k|
00000190  7d 6b 97 7b 55 dc 3d 71  19 a1 e8 0b 1a 76 e7 e6  |[COLOR=#666666]}[/COLOR]k.[COLOR=#666666]{[/COLOR]U.[COLOR=#666666]=[/COLOR]q.....v..|
000001a0  ee 00 3b a6 af 29 27 51  63 13 af 6d fd 9b ea 82  |..;..[COLOR=#666666])[/COLOR][COLOR=#BB4444]'Qc..m....|[/COLOR]
[COLOR=#BB4444]000001b0  f7 4e a0 d9 9c d5 90 95  f2 f8 69 0d 6c 0f 00 fe  |.N........i.l...|[/COLOR]
[COLOR=#BB4444]000001c0  ff ff 83 fe ff ff 02 38  77 00 00 f0 d9 08 00 fe  |.......8w.......|[/COLOR]
[COLOR=#BB4444]000001d0  ff ff 05 fe ff ff 01 00  00 00 01 38 77 00 00 00  |...........8w...|[/COLOR]
[COLOR=#BB4444]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]



[COLOR=#BB4444]ADDITIONAL INFORMATION :[/COLOR]
[COLOR=#BB4444]=================== log of boot-repair 2013-11-07__14h55 ===================[/COLOR]
[COLOR=#BB4444]boot-repair version : 3.199~ppa36~precise[/COLOR]
[COLOR=#BB4444]boot-sav version : 3.199~ppa36~precise[/COLOR]
[COLOR=#BB4444]glade2script version : 3.2.2~ppa45~precise[/COLOR]
[COLOR=#BB4444]boot-sav-extra version : 3.199~ppa36~precise[/COLOR]
[COLOR=#BB4444]boot-repair is executed in installed-session (Ubuntu 12.04 LTS, precise, Ubuntu, i686)[/COLOR]
[COLOR=#BB4444]CPU op-mode(s):        32-bit[/COLOR]
[COLOR=#BB4444]BOOT_IMAGE=/boot/vmlinuz-3.2.0-55-generic-pae root=UUID=77b1fd26-632c-43ae-a63b-9aa237261fec ro quiet splash vt.handoff=7[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda1:The OS now in use - Ubuntu 12.04 LTS CurrentSession:linux[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/sda1: UUID="77b1fd26-632c-43ae-a63b-9aa237261fec" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sda5: UUID="822b820f-8152-435a-8e49-078c20cfb2d2" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sda6: UUID="1aa59a96-65d6-43ea-8001-30187b66d56d" TYPE="swap"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Warning: extended partition does not start at a cylinder boundary.[/COLOR]
[COLOR=#BB4444]DOS and Linux will interpret the contents differently.[/COLOR]

[COLOR=#BB4444]=================== /etc/grub.d/ :[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root     4096 Apr 23  2012 grub.d[/COLOR]
[COLOR=#BB4444]total 56[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6715 Apr 17  2012 00_header[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 5522 Apr 17  2012 05_debian_theme[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7399 Apr 17  2012 10_linux[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6335 Apr 17  2012 20_linux_xen[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7603 Apr 17  2012 30_os-prober[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  214 Apr 17  2012 40_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   95 Apr 17  2012 41_custom[/COLOR]
[COLOR=#BB4444]-rw-r--r-- 1 root root  483 Apr 17  2012 README[/COLOR]




[COLOR=#BB4444]=================== /etc/default/grub :[/COLOR]

[COLOR=#BB4444]# If you change this file, run '[/COLOR]update-grub[COLOR=#BB4444]' afterwards to update[/COLOR]
[COLOR=#BB4444]# /boot/grub/grub.cfg.[/COLOR]
[COLOR=#BB4444]# For full documentation of the options in this file, see:[/COLOR]
[COLOR=#BB4444]#   info -f grub -n '[/COLOR]Simple configuration[COLOR=#BB4444]'[/COLOR]

[COLOR=#BB4444]GRUB_DEFAULT=0[/COLOR]
[COLOR=#BB4444]#GRUB_HIDDEN_TIMEOUT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT_QUIET=true[/COLOR]
[COLOR=#BB4444]GRUB_TIMEOUT=10[/COLOR]
[COLOR=#BB4444]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX=""[/COLOR]

[COLOR=#BB4444]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR]
[COLOR=#BB4444]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR]
[COLOR=#BB4444]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR]
[COLOR=#BB4444]#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"[/COLOR]

[COLOR=#BB4444]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR]
[COLOR=#BB4444]#GRUB_TERMINAL=console[/COLOR]

[COLOR=#BB4444]# The resolution used on graphical terminal[/COLOR]
[COLOR=#BB4444]# note that you can use only modes which your graphic card supports via VBE[/COLOR]
[COLOR=#BB4444]# you can see them in real GRUB with the command `vbeinfo'[/COLOR]
[COLOR=#B8860B]GRUB_GFXMODE[/COLOR][COLOR=#666666]=[/COLOR]640x480

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This installed-session is not EFI-compatible.
SecureBoot disabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	.
sda5	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/home.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA FUJITSU MHV2120B [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 120GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  40.0GB  40.0GB  primary   ext4            boot
2      40.0GB  120GB   80.0GB  extended
6      40.0GB  44.0GB  4000MB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]
5      44.0GB  120GB   76.0GB  logical   [COLOR=#B8860B]ext4[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA FUJITSU MHV2120B;
1:1049kB:40.0GB:40.0GB:ext4::boot;
2:40.0GB:120GB:80.0GB:::;
6:40.0GB:44.0GB:4000MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
5:44.0GB:120GB:76.0GB:ext4::;


[COLOR=#666666]===================[/COLOR] mount:
/dev/sda1 on / [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
/dev/sda5 on /home [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
gvfs-fuse-daemon on /home/mahmoudahmed/.gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfs-fuse-daemon [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]mahmoudahmed[COLOR=#666666])[/COLOR]
gvfs-fuse-daemon on /root/.gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfs-fuse-daemon [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse fw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sg0 shm snapshot snd stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vboxusb vga_arbiter zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       37G  2.7G   33G   8% /
udev           devtmpfs  489M   12K  489M   1% /dev
tmpfs          tmpfs     199M  788K  198M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     497M  152K  496M   1% /run/shm
/dev/sda5      ext4       70G  2.8G   64G   5% /home

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x0005a21d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    78125055    39061504   83  Linux
/dev/sda2        78127102   234440703    78156801    5  Extended
/dev/sda5        85940224   234440703    74250240   83  Linux
/dev/sda6        78127104    85940223     3906560   82  Linux swap / Solaris

Partition table entries are not in disk [COLOR=#B8860B]order[/COLOR]



[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
[/COLOR]
[/TD]
[/TR]
[/TABLE]

[/FONT][/COLOR]
[Download as text]("http://paste.ubuntu.com/6376187/plain/")
```

---

