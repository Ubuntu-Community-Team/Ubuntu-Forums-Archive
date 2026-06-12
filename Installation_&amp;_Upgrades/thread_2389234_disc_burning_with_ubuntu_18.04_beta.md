---
title: "disc burning with ubuntu 18.04 beta"
date: 2018-04-13
forum: Installation &amp; Upgrades
---

### Post by newblank25 on 2018-04-13
[h=2]Re: brasero disc burner in ubuntu 18.04 beta[/h][COLOR=#000000][INDENT]tried changing settings in K3b but that didn't work
with k3b I got message cd record has no permission to open device.
modify device settings in k3b to solve problem. 
got this from debugging notice[FONT=monospace]Devices[/FONT]
[FONT=monospace]-----------------------[/FONT]
[FONT=monospace]HL-DT-ST DVDRAM GH24NSC0 LI00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]System[/FONT]
[FONT=monospace]-----------------------[/FONT]
[FONT=monospace]K3b Version: 17.12.3[/FONT]
[FONT=monospace]KDE Version: 5.44.0[/FONT]
[FONT=monospace]Qt Version: 5.9.4[/FONT]
[FONT=monospace]Kernel: 4.15.0-13-generic[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]Used versions[/FONT]
[FONT=monospace]-----------------------[/FONT]
[FONT=monospace]cdrecord: 1.1.11[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]cdrecord[/FONT]
[FONT=monospace]-----------------------[/FONT]
[FONT=monospace]/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.[/FONT]
[FONT=monospace]/usr/bin/wodim: Resource temporarily unavailable. Cannot get mmap for 12587008 Bytes on /dev/zero.[/FONT]
[FONT=monospace]Text len: 954[/FONT]
[FONT=monospace]TOC Type: 0 = CD-DA[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]cdrecord command:[/FONT]
[FONT=monospace]-----------------------[/FONT]
[FONT=monospace]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=40 -sao driveropts=burnfree textfile=/tmp/k3b.rC5996 -useinfo -audio /tmp/k3b_audio_1_01.inf /tmp/k3b_audio_1_02.inf /tmp/k3b_audio_1_03.inf /tmp/k3b_audio_1_04.inf /tmp/k3b_audio_1_05.inf /tmp/k3b_audio_1_06.inf /tmp/k3b_audio_1_07.inf /tmp/k3b_audio_1_08.inf /tmp/k3b_audio_1_09.inf /tmp/k3b_audio_1_10.inf /tmp/k3b_audio_1_11.inf /tmp/k3b_audio_1_12.inf /tmp/k3b_audio_1_13.inf /tmp/k3b_audio_1_14.inf /tmp/k3b_audio_1_15.inf /tmp/k3b_audio_1_16.inf /tmp/k3b_audio_1_17.inf /tmp/k3b_audio_1_18.inf[/FONT]
[/INDENT]
[/COLOR]
can anyone help? thx

---

### Post by newblank25 on 2018-04-13
will this be fix with long term release?

---

