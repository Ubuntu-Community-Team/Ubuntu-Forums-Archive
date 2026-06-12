---
title: "No GRUB menu after install"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by trevorrr.rice on 2013-11-03
I know this question has been asked a lot, but none of the suggestions in other threads have solved my problem.

I finally installed Ubuntu after weeks of trying, but when I went to re-boot my computer, it booted straight to Windows 7.  I then went back into Ubuntu using my LiveUSB and ran boot-repair.

Here are my results: ```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
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
773
774
775
776
777
778
779
780
781
782
783
784
785
786
787
788
789
790
791
792
793
794
795
796
797
798
799
800
801
802
803
804
805
806
807
808
809
810
811
812
813
814
815
816
817
818
819
820
821
822
823
824
825
826
827
828
829
830
831
832
833
834
835
836
837
838
839
840
841
842
843
844
845
846
847
848
849
850
851
852
853
854
855
856
857
858
859
860
861
862
863
864
865
866
867
868
869
870
871
872
873
874
875
876
877
878
879
880
881
882
883
884
885
886
887
888
889
890
891
892
893
894
895
896
897
898
899
900
901
902
903
904
905
906
907
908
909
910
911
912
913
914
915
916
917
918
919
920
921
922
923
924
925
926
927
928
929
930
931
932
933
934
935
936
937
938
939
940
941
942
943
944
945
946
947
948
949
950
951
952
953
954
955
956
957
958
959
960
961
962
963
964
965
966
967
968
969
970
971
972
973
974
975
976
977
978
979
980
981
982
983
984
985
986
987
988
989
990
991
992
993
994
995[/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 27Sep2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sda.
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]4.04 and higher[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/boot/bkpbootx64.efi /EFI/boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/microsoft/boot/bootmgfw.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda4: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 2906 of /dev/sdb1 [COLOR=#AA22FF]**for **[/COLOR]its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1                   1 1,250,263,727 1,250,263,727  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sda1           2,048       534,527       532,480 -
/dev/sda2         534,528    40,624,127    40,089,600 Windows Recovery Environment [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda3      40,624,128    41,156,607       532,480 EFI System partition
/dev/sda4      41,156,608    41,418,751       262,144 Microsoft Reserved Partition [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda5      41,418,752   717,783,694   676,364,943 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda6     717,785,088 1,229,502,463   511,717,376 Data partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]
/dev/sda7   1,229,502,464 1,250,263,039    20,760,576 Swap partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        648D-DD82                              vfat       SONYSYS
/dev/sda2        74D09CA8D09C71DA                       ntfs       Recovery
/dev/sda3        A493-926E                              vfat       
/dev/sda5        40CEA28ACEA277B4                       ntfs       
/dev/sda6        5110ffca-d09e-434a-bcc4-d78723d781f8   ext4       
/dev/sda7        10534b2d-0307-4c74-aedb-03995061416b   swap       
/dev/sdb1        0872-D3ED                              vfat       [COLOR=#B8860B]PENDRIVE[/COLOR]

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sdb1        /cdrom                   vfat       [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda6/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

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

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#BB4444]"${feature_menuentry_id}"[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"--id"[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]export [/COLOR]menuentry_id_option

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
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_all_video_module[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
insmod all_video
  [COLOR=#AA22FF]**else**[/COLOR]
insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_default_font_path[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR]unicode
[COLOR=#AA22FF]**else**[/COLOR]
insmod part_gpt
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,gpt6'[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-efi[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,gpt6  5110ffca-d09e-434a-bcc4-d78723d781f8
[COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 5110ffca-d09e-434a-bcc4-d78723d781f8
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"/usr/share/grub/unicode.pf2"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if **[/COLOR]loadfont [COLOR=#B8860B]$font[/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]$prefix[/COLOR]/locale
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
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${1}"[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${1}"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
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
menuentry [COLOR=#BB4444]'Ubuntu'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-simple-5110ffca-d09e-434a-bcc4-d78723d781f8'[/COLOR] [COLOR=#666666]{[/COLOR]
recordfail
    load_video
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    insmod part_gpt
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,gpt6'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-efi[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,gpt6  5110ffca-d09e-434a-bcc4-d78723d781f8
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 5110ffca-d09e-434a-bcc4-d78723d781f8
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]linux    /boot/vmlinuz-3.11.0-12-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]5110ffca-d09e-434a-bcc4-d78723d781f8 ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
    initrd    /boot/initrd.img-3.11.0-12-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]'Advanced options for Ubuntu'[/COLOR] [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-advanced-5110ffca-d09e-434a-bcc4-d78723d781f8'[/COLOR] [COLOR=#666666]{[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-12-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-12-generic-advanced-5110ffca-d09e-434a-bcc4-d78723d781f8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        insmod part_gpt
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,gpt6'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-efi[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,gpt6  5110ffca-d09e-434a-bcc4-d78723d781f8
        [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 5110ffca-d09e-434a-bcc4-d78723d781f8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-12-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-12-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]5110ffca-d09e-434a-bcc4-d78723d781f8 ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-12-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.11.0-12-generic-recovery-5110ffca-d09e-434a-bcc4-d78723d781f8'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,gpt6'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-efi[COLOR=#666666]=[/COLOR]hd0,gpt6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,gpt6  5110ffca-d09e-434a-bcc4-d78723d781f8
        [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 5110ffca-d09e-434a-bcc4-d78723d781f8
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 3.11.0-12-generic ...'[/COLOR]
        linux    /boot/vmlinuz-3.11.0-12-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]5110ffca-d09e-434a-bcc4-d78723d781f8 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-3.11.0-12-generic
    [COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/25_custom ###*[/COLOR]

menuentry [COLOR=#BB4444]"Windows UEFI bootmgfw.efi"[/COLOR] [COLOR=#666666]{[/COLOR]
search --fs-uuid --no-floppy --set[COLOR=#666666]=[/COLOR]root A493-926E
chainloader [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR]/EFI/Microsoft/Boot/bootmgfw.efi
[COLOR=#666666]}[/COLOR]

menuentry [COLOR=#BB4444]"Windows Boot UEFI loader"[/COLOR] [COLOR=#666666]{[/COLOR]
search --fs-uuid --no-floppy --set[COLOR=#666666]=[/COLOR]root A493-926E
chainloader [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR]/EFI/Boot/bkpbootx64.efi
[COLOR=#666666]}[/COLOR]

menuentry [COLOR=#BB4444]"EFI/boot/bkpbootx64.efi"[/COLOR] [COLOR=#666666]{[/COLOR]
search --fs-uuid --no-floppy --set[COLOR=#666666]=[/COLOR]root 648D-DD82
chainloader [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR]/EFI/boot/bkpbootx64.efi
[COLOR=#666666]}[/COLOR]

menuentry [COLOR=#BB4444]"EFI/microsoft/boot/bootmgfw.efi"[/COLOR] [COLOR=#666666]{[/COLOR]
search --fs-uuid --no-floppy --set[COLOR=#666666]=[/COLOR]root 648D-DD82
chainloader [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR]/EFI/microsoft/boot/bootmgfw.efi
[COLOR=#666666]}[/COLOR]

menuentry [COLOR=#BB4444]"EFI/boot/bootx64.efi"[/COLOR] [COLOR=#666666]{[/COLOR]
search --fs-uuid --no-floppy --set[COLOR=#666666]=[/COLOR]root 74D09CA8D09C71DA
chainloader [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR]/EFI/boot/bootx64.efi
[COLOR=#666666]}[/COLOR]

menuentry [COLOR=#BB4444]"EFI/microsoft/boot/bootmgfw.efi sda2"[/COLOR] [COLOR=#666666]{[/COLOR]
search --fs-uuid --no-floppy --set[COLOR=#666666]=[/COLOR]root 74D09CA8D09C71DA
chainloader [COLOR=#666666]([/COLOR][COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR][COLOR=#666666])[/COLOR]/EFI/microsoft/boot/bootmgfw.efi
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/25_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
menuentry [COLOR=#BB4444]"Windows Boot Manager (UEFI on /dev/sda3)"[/COLOR] --class windows --class os [COLOR=#666666]{[/COLOR]
    insmod part_gpt
    insmod fat
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,gpt3'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,gpt3 --hint-efi[COLOR=#666666]=[/COLOR]hd0,gpt3 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,gpt3  A493-926E
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root A493-926E
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]chainloader /EFI/Microsoft/Boot/bootmgfw.efi
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_uefi-firmware ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg
[COLOR=#AA22FF]**elif**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${config_directory}"[/COLOR] -a -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sda6/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/sda6 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]5110ffca-d09e-434a-bcc4-d78723d781f8 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# /boot/efi was on /dev/sda3 during installation*[/COLOR]
[COLOR=#008800]*#UUID=A493-926E  /boot/efi       vfat    defaults        0       1*[/COLOR]
[COLOR=#008800]*# swap was on /dev/sda7 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]10534b2d-0307-4c74-aedb-03995061416b none            swap    sw              0       0
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]A493-926E    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda6: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sdb1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------

[COLOR=#AA22FF]**if **[/COLOR]loadfont /boot/grub/font.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray

menuentry [COLOR=#BB4444]"Try Ubuntu without installing"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz.efi  [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"Install Ubuntu"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz.efi  [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"OEM install (for manufacturers)"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz.efi  [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity quiet splash oem-config/enable[COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR] --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"Check disc for defects"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz.efi  [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]=========================[/COLOR] sdb1/syslinux/syslinux.cfg: [COLOR=#666666]==========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# D-I config version 2.0*[/COLOR]
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sdb1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]=================[/COLOR] sdb1: Location of files loaded by Syslinux: [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]==============[/COLOR] sdb1: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 syslinux/chain.c32                 :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]
 syslinux/gfxboot.c32               :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]
 syslinux/menu.c32                  :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]
 syslinux/vesamenu.c32              :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown GPT Partiton Type
[COLOR=#B8860B]329701f46e06124e8273346c5641494f[/COLOR]

[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

cat: /tmp/BootInfo-PLm4as4H/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-PLm4as4H/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-PLm4as4H/Tmp_Log: No such file or directory
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/4359/mounts[COLOR=#666666])[/COLOR] leaked on lvscan invocation. Parent PID 17811: bash
  No volume groups found

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2013-11-01__23h11 [COLOR=#666666]===================[/COLOR]
boot-repair version : 3.199~ppa31~saucy
boot-sav version : 3.199~ppa31~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa31~saucy
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Ubuntu 13.10, saucy, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/casper/vmlinuz.efi [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --

WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sda'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]


[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda3@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi[/COLOR]
[COLOR=#BB4444]/dev/sda6:Ubuntu 13.10 (13.10):Ubuntu:linux[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/loop0: TYPE="squashfs"[/COLOR]
[COLOR=#BB4444]/dev/sda1: LABEL="SONYSYS" UUID="648D-DD82" TYPE="vfat"[/COLOR]
[COLOR=#BB4444]/dev/sda2: LABEL="Recovery" UUID="74D09CA8D09C71DA" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda3: UUID="A493-926E" TYPE="vfat"[/COLOR]
[COLOR=#BB4444]/dev/sda5: UUID="40CEA28ACEA277B4" TYPE="ntfs"[/COLOR]
[COLOR=#BB4444]/dev/sda6: UUID="5110ffca-d09e-434a-bcc4-d78723d781f8" TYPE="ext4"[/COLOR]
[COLOR=#BB4444]/dev/sda7: UUID="10534b2d-0307-4c74-aedb-03995061416b" TYPE="swap"[/COLOR]
[COLOR=#BB4444]/dev/sdb1: LABEL="PENDRIVE" UUID="0872-D3ED" TYPE="vfat"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Windows not detected by os-prober on sda5.[/COLOR]

[COLOR=#BB4444]WARNING: GPT (GUID Partition Table) detected on '[/COLOR]/dev/sda[COLOR=#BB4444]'! The util sfdisk doesn'[/COLOR]t support GPT. Use GNU Parted.


WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sda'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]

[COLOR=#BB4444]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/boot/bootmgfw.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bkpbootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of .bkp file detected: /mnt/boot-sav/sda1/EFI/boot/bkpbootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda3/EFI/Microsoft/Boot/bootmgfw.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/sda3/EFI/Boot/bkpbootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of EFI/Boot file detected: /mnt/boot-sav/sda3/EFI/Boot/bootx64.efi[/COLOR]
[COLOR=#BB4444]Presence of .bkp file detected: /mnt/boot-sav/sda3/EFI/Boot/bkpbootx64.efi[/COLOR]

[COLOR=#BB4444]=================== sda6/etc/grub.d/ :[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root    4096 Oct 28 03:50 grub.d[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root root    4096 Oct 27 03:18 grub.d.bak[/COLOR]
[COLOR=#BB4444]total 72[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  7850 Oct 10 17:48 00_header[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  5949 Aug 15 08:26 05_debian_theme[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 11479 Oct 10 17:48 10_linux[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 10258 Oct 10 17:48 20_linux_xen[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   907 Oct 28 03:50 25_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 11531 Oct 10 17:48 30_os-prober[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  1426 Oct 10 17:48 30_uefi-firmware[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   214 Oct 10 17:48 40_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   216 Oct 10 17:48 41_custom[/COLOR]
[COLOR=#BB4444]-rw-r--r-- 1 root root   483 Oct 10 17:48 README[/COLOR]




[COLOR=#BB4444]=================== sda6/etc/default/grub :[/COLOR]

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
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]



/boot/efi detected in the fstab of sda6: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]A493-926E     [COLOR=#666666]([/COLOR]sda3[COLOR=#666666])[/COLOR]
[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode [COLOR=#AA22FF]**for **[/COLOR]this live-session.
SecureBoot disabled. [COLOR=#666666]([/COLOR]maybe sec-boot, Please report this message to boot.repair@gmail.com[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA Hitachi HTS72756 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 640GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  274MB   273MB   fat32           EFI system partition          hidden
2      274MB   20.8GB  20.5GB  ntfs            Basic data partition          hidden, diag
3      20.8GB  21.1GB  273MB   fat32           EFI system partition          boot
4      21.1GB  21.2GB  134MB                   Microsoft reserved partition  msftres
5      21.2GB  368GB   346GB   ntfs            Basic data partition          msftdata
6      368GB   630GB   262GB   ext4
7      630GB   640GB   10.6GB  linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]


Model: SanDisk Cruzer [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 4022MB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      19.5kB  4014MB  4014MB  primary  fat32        [COLOR=#B8860B]boot[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:640GB:scsi:512:4096:gpt:ATA Hitachi HTS72756;
1:1049kB:274MB:273MB:fat32:EFI system partition:hidden;
2:274MB:20.8GB:20.5GB:ntfs:Basic data partition:hidden, diag;
3:20.8GB:21.1GB:273MB:fat32:EFI system partition:boot;
4:21.1GB:21.2GB:134MB::Microsoft reserved partition:msftres;
5:21.2GB:368GB:346GB:ntfs:Basic data partition:msftdata;
6:368GB:630GB:262GB:ext4::;
7:630GB:640GB:10.6GB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

BYT;
/dev/sdb:4022MB:scsi:512:512:msdos:SanDisk Cruzer;
1:19.5kB:4014MB:4014MB:fat32::boot;


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sdb1 on /cdrom [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/firmware/efi/efivars [COLOR=#AA22FF]type [/COLOR]efivarfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
systemd on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,none,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/999/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]ubuntu[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/sda2 on /mnt/boot-sav/sda2 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda3 on /mnt/boot-sav/sda3 [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/sda5 on /mnt/boot-sav/sda5 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda6 on /mnt/boot-sav/sda6 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout tpm0 uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda1/1:

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 82 dd 8d 64 4e  4f 20 4e 41 4d 45 20 20  |..[COLOR=#666666])[/COLOR]...dNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |[COLOR=#666666]{[/COLOR]......|.N..V@.A|
00000070  bb aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 [COLOR=#AA22FF]cd [/COLOR]13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 [COLOR=#AA22FF]cd [/COLOR]c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...[COLOR=#666666]}[/COLOR].[COLOR=#666666]}[/COLOR].....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 [COLOR=#AA22FF]cd [/COLOR]10 eb ee a0 fb 7d  |<.t............[COLOR=#666666]}[/COLOR]|
000000f0  eb e5 a0 f9 7d eb e0 98  [COLOR=#AA22FF]cd [/COLOR]16 [COLOR=#AA22FF]cd [/COLOR]19 66 60 80 7e  |....[COLOR=#666666]}[/COLOR].......f[COLOR=#BB4444]`[/COLOR].~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 [COLOR=#AA22FF]cd  [/COLOR]13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200
ls /mnt/boot-sav/sda2/1:
ls /mnt/boot-sav/sda2: Autorun
Autorun.inf
boot
bootmgr
bootmgr.efi
data
EFI
etfsboot.com
HDD
idf
Recovery
snyhdrcv.ini
Sony
sources
System Volume Information  . Please report this message to boot.repair@gmail.com

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 08 00  |........?....[COLOR=#666666]([/COLOR]..|
00000020  00 00 00 00 80 00 80 00  ff b7 63 02 00 00 00 00  |..........c.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  da 71 9c d0 a8 9c d0 74  |.........q.....t|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
ls /mnt/boot-sav/sda3/1:

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda3
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 01 7e 20  |.X.MSDOS5.0...~ |
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 e0 6b 02  |........?.....k.|
00000020  00 20 08 00 c1 0f 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 6e 92 93 a4 4e  4f 20 4e 41 4d 45 20 20  |..[COLOR=#666666])[/COLOR]n...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |[COLOR=#666666]{[/COLOR]......|.N..V@.A|
00000070  bb aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 [COLOR=#AA22FF]cd [/COLOR]13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 [COLOR=#AA22FF]cd [/COLOR]c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...[COLOR=#666666]}[/COLOR].[COLOR=#666666]}[/COLOR].....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 [COLOR=#AA22FF]cd [/COLOR]10 eb ee a0 fb 7d  |<.t............[COLOR=#666666]}[/COLOR]|
000000f0  eb e5 a0 f9 7d eb e0 98  [COLOR=#AA22FF]cd [/COLOR]16 [COLOR=#AA22FF]cd [/COLOR]19 66 60 80 7e  |....[COLOR=#666666]}[/COLOR].......f[COLOR=#BB4444]`[/COLOR].~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 [COLOR=#AA22FF]cd  [/COLOR]13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 78 02  |........?.....x.|
00000020  00 00 00 00 80 00 80 00  8e 82 50 28 00 00 00 00  |..........P[COLOR=#666666]([/COLOR]....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  b4 77 a2 ce 8a a2 ce 40  |.........w.....@|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sda'[/COLOR]! The util fdisk doesn't support GPT. Use GNU Parted.


[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G  119M  3.8G   4% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      789M  1.2M  788M   1% /run
/dev/sdb1      vfat       3.8G  1.3G  2.5G  35% /cdrom
/dev/loop0     squashfs   843M  843M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.9G   36K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G   76K  3.9G   1% /run/shm
none           tmpfs      100M   52K  100M   1% /run/user
/dev/sda1      vfat       256M   14M  243M   6% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     20G   19G  1.1G  95% /mnt/boot-sav/sda2
/dev/sda3      vfat       252M   20M  233M   8% /mnt/boot-sav/sda3
/dev/sda5      fuseblk    323G  104G  220G  33% /mnt/boot-sav/sda5
/dev/sda6      ext4       241G  3.2G  225G   2% /mnt/boot-sav/sda6

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: 0xf74d0189

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1250263727   625131863+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    b  W95 FAT32


EFI detected. Please check the options.

[COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will reinstall the grub-efi of sda6, using the following options:        sda3/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot backup-and-rename-efi-files


rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
rm /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi.grb
rm /mnt/boot-sav/sda3/efi/Boot/bootx64.efi
Quantity of real Windows: 1
df: ‘/dev/sda3@/efi/Microsoft/Boot/bootmgfw.efi’: No such file or directory
Could not detect USEDPERCENT of sda3@/efi/Microsoft/Boot/bootmgfw.efi [COLOR=#666666]()[/COLOR].
df: ‘/dev/sda3@/efi/Microsoft/Boot/bootmgfw.efi’: No such file or directory

Mount sda3 on /mnt/boot-sav/sda6/boot/efi
ls /mnt/boot-sav/sda6/boot/efi/1:
grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.00-19ubuntu2,grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.

chroot /mnt/boot-sav/sda6 efibootmgr -v
BootCurrent: 0000
BootOrder: 0000,0001
Boot0000* EFI USB Device    ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]1d,0[COLOR=#666666])[/COLOR]USB[COLOR=#666666]([/COLOR]0,0[COLOR=#666666])[/COLOR]USB[COLOR=#666666]([/COLOR]1,0[COLOR=#666666])[/COLOR]HD[COLOR=#666666]([/COLOR]1,26,779fc2,00000000[COLOR=#666666])[/COLOR]RC
Boot0001* Windows Boot Manager    HD[COLOR=#666666]([/COLOR]3,26be000,82000,f4208db1-1bd1-4b0f-937c-2e9b1b62021b[COLOR=#666666])[/COLOR]File[COLOR=#666666]([/COLOR]EFIMicrosoftBootbootmgfw.efi[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]...i................

chroot /mnt/boot-sav/sda6 uname -r
Kernel: 3.11.0-12-generic

Reinstall the grub-efi of sda6
Installation finished. No error reported.
grub-install --efi-directory[COLOR=#666666]=[/COLOR]/boot/efi --target[COLOR=#666666]=[/COLOR]x86_64-efi : BootCurrent: 0000
BootOrder: 0002,0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
Boot0002* ubuntu
[COLOR=#AA22FF]exit [/COLOR]code of grub-install :0
mv 25_custom
ls /mnt/boot-sav/sda1/1:
ls /mnt/boot-sav/sda6/boot/efi/1:
df /dev/sda3
Save and rename /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi [COLOR=#666666]([/COLOR]/mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi[COLOR=#666666])[/COLOR]
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bootx64.efi
ls /mnt/boot-sav/sda6/boot/efi/1:
Add /mnt/boot-sav/sda6/boot/efi efi entries in /mnt/boot-sav/sda6/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/Boot/bkpbootx64.efi
sda3/bkpbootx64.efi already added
sda3/bootmgfw.efi already added
df /dev/sda1
Save and rename /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi [COLOR=#666666]([/COLOR]/mnt/boot-sav/sda1/EFI/Boot/bkpbootx64.efi[COLOR=#666666])[/COLOR]
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
ls /mnt/boot-sav/sda1/1:
Add /mnt/boot-sav/sda1 efi entries in /mnt/boot-sav/sda6/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda1/EFI/boot/bkpbootx64.efi
Adding custom /mnt/boot-sav/sda1/EFI/microsoft/boot/bootmgfw.efi
df /dev/sda2
cp /mnt/boot-sav/sda6/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi [COLOR=#666666]([/COLOR]& .grb[COLOR=#666666])[/COLOR]
ls /mnt/boot-sav/sda2/1:
ls /mnt/boot-sav/sda2: Autorun
Autorun.inf
boot
bootmgr
bootmgr.efi
data
EFI
etfsboot.com
HDD
idf
Recovery
snyhdrcv.ini
Sony
sources
System Volume Information  . Please report this message to boot.repair@gmail.com
Add /mnt/boot-sav/sda2 efi entries in /mnt/boot-sav/sda6/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda2/EFI/boot/bootx64.efi
Adding custom /mnt/boot-sav/sda2/EFI/microsoft/boot/bootmgfw.efi
Installation finished. No error reported.
grub-install --efi-directory[COLOR=#666666]=[/COLOR]/boot/efi --target[COLOR=#666666]=[/COLOR]x86_64-efi : BootCurrent: 0000
BootOrder: 0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
BootCurrent: 0000
BootOrder: 0002,0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
Boot0002* ubuntu
[COLOR=#AA22FF]exit [/COLOR]code of grub-install :0

chroot /mnt/boot-sav/sda6 efibootmgr -v
BootCurrent: 0000
BootOrder: 0002,0000,0001
Boot0000* EFI USB Device    ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]1d,0[COLOR=#666666])[/COLOR]USB[COLOR=#666666]([/COLOR]0,0[COLOR=#666666])[/COLOR]USB[COLOR=#666666]([/COLOR]1,0[COLOR=#666666])[/COLOR]HD[COLOR=#666666]([/COLOR]1,26,779fc2,00000000[COLOR=#666666])[/COLOR]RC
Boot0001* Windows Boot Manager    HD[COLOR=#666666]([/COLOR]3,26be000,82000,f4208db1-1bd1-4b0f-937c-2e9b1b62021b[COLOR=#666666])[/COLOR]File[COLOR=#666666]([/COLOR]EFIMicrosoftBootbootmgfw.efi[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]...i................
Boot0002* ubuntu    HD[COLOR=#666666]([/COLOR]3,26be000,82000,f4208db1-1bd1-4b0f-937c-2e9b1b62021b[COLOR=#666666])[/COLOR]File[COLOR=#666666]([/COLOR]EFIubuntugrubx64.efi[COLOR=#666666])[/COLOR]

chroot /mnt/boot-sav/sda6 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda3@/EFI/Microsoft/Boot/bootmgfw.efi
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.[/COLOR][/TD]
[/TR]
[/TABLE]

```

Could anyone explain what this means or how to fix it?

Thanks!

---

### Post by oldfred on 2013-11-03
@trevorrr.rice
This says ubuntu is first. From UEFI menu do you see these boot options an clicking on Ubuntu work?

BootOrder: [COLOR=#ff0000]0002[/COLOR],0000,0001
Boot0000* EFI USB Device
Boot0001* Windows Boot Manager
Boot[COLOR=#ff0000]0002[/COLOR]* ubuntu

---

### Post by trevorrr.rice on 2013-11-03
@oldfred
Assuming I am on the right menu, all I see is: 
Boot Priority
External Device
Internal Optical Disc Drive
Internal Hard Disk Drive
Network

If I am not looking at the right thing, let me know.

Thanks.

---

### Post by oldfred on 2013-11-03
Is there a sub-menu under boot priority?

The list above was from your system. UEFI was queried by Boot-Repair and it showed those entries.

---

### Post by trevorrr.rice on 2013-11-03
Here is a picture of it:

[http://i.imgur.com/htdW1iM.jpg](http://i.imgur.com/htdW1iM.jpg)

I don't believe there is a sub-menu.  Or if there is, I'm not sure how to access it.

---

### Post by oldfred on 2013-11-03
If it has a sub menu it should have the arrow head or sideways diamond and you hit enter as shown below, but you do not show any of those.
Do you have the newest UEFI/BIOS from your vendor?

---

### Post by trevorrr.rice on 2013-11-04
I have BIOS Version: R0142C5 for my Sony Vaio.
I have not been able to find if that is the latest version though.

---

### Post by trevorrr.rice on 2013-11-05
Bump?

---

### Post by oldfred on 2013-11-05
Did you search your local Sony support site for a newer UEFI/BIOS. 
I found this which is your current, but without exact model do not know if newer version is available or not.
[http://www.sony-mea.com/support/download/502251](http://www.sony-mea.com/support/download/502251)

Some also find rEFInd works with the limited UEFI systems.
       Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

### Post by trevorrr.rice on 2013-11-05
I was able to find my model.  According to this: [http://i.imgur.com/M7n5eMz.png](http://i.imgur.com/M7n5eMz.png) I have the latest version for my model.

I will take a look at those other links in the mean time.

---

### Post by trevorrr.rice on 2013-11-07
So is there any way to get GRUB to work with my current UEFI?  It seems like GRUB would be simpler than the alternatives.

---

### Post by oldfred on 2013-11-07
Have you tried the rename? Boot-Repair often does that for buggy UEFI. It renames grub2's shim file to be the Windows efi file. Shim has the same Microsoft signing key so it works when in the Windows efi folder.

       # for Windows, but for UEFI systems that only boot this file, grub or shim may get renamed to this and this backed up.
/EFI/Microsoft/Boot/bootmgfw.efi


 Changed see below - Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
If B-R is used in a UEFI session, it will never create bkp by default. 
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.

      
 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)


 Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Not sure the exact screens you now see. Boot-Repair gets bug fixes & updates. Above were from several users that used it.

Also if your computer only boots with secure boot on, then you need to boot Boot-Repair in secure boot mode and run it to install the signed kernels so Ubuntu can boot with secure boot on.

---

### Post by trevorrr.rice on 2013-11-08
So I ran boot-repair again after applying the "Backup and rename EFI files" option.  Here is my output: [http://paste.ubuntu.com/6384225/](http://paste.ubuntu.com/6384225/)

I would also like to add that the last sentence after running boot-repair was "Please do not forget to make your BIOS boot on sda3/EFI/ubuntu/grubx64.efi file!"

How do I go about making my BIOS boot to that?

Also, when you say > Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.ef, do I need to manually do this or is boot-repair suppose to do this?

If I need to manually do this, how do I do that?

Thanks again.

---

### Post by oldfred on 2013-11-08
In UEFI the actual entry will be ubuntu, but you actually are booting the shim file. UEFI shows folder names with boot files.

If the ubuntu entry does not work then Boot-Repair can copy & rename grub2's shim. It gets put into the Windows folder, so from UEFI when you boot Windows you actually boot grub.

Some have manually done it just by copying shim to the Windows folder and renaming both the Windows bootmgfw.efi to a backup name and rename shim to bootmgfw.efi. Then you have to manually add a grub menu entry to boot the renamed Windows efi file. Boot-Repair does all that automatically. 
 available as a "Rename Windows EFI files" option in the Advanced Options

---

### Post by trevorrr.rice on 2013-11-08
Even after running boot-repair, I see no option for Ubuntu.

Edit: Never mind, it works!  I really appreciate your patience and helping me out.

One last question.  This what my menu looks like:  [http://i.imgur.com/J4KmElL.jpg](http://i.imgur.com/J4KmElL.jpg)

What are all of these options for?  I chose Windows Boot UEFI Loader to make sure Windows still worked, and it did.  Is there any point to the other options?

It's not a big deal but is there a way to get rid of these to simplify GRUB?

---

### Post by oldfred on 2013-11-08
Grub run scripts to add the entries. They now put the older kernels in Advanced options to keep the menu simple, but you should houseclean old kernels periodically.

Boot-Repair did its rename so it added entries to 25_custom and grub2's os-prober added its entries for other systems installed. Up until 13.10 grub2's os-prober only created BIOS entries that did not work with UEFI, so you had to rely on the Boot-Repair entries.

You can turn off os-prober or if those are what you want, edit more out of 25_custom. And you can change titles to be anything you want.

More info in the link in my signature. See section on efi menu cleanup.

---

### Post by trevorrr.rice on 2013-11-08
Thanks for all the help and info.

Marked as solved.

---

