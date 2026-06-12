---
title: "Sound Juicer cannot encode mp3 any more after Dapper-Upgrade"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2006-06-18
Hi,

with Breeze, I could rip and encode mp3 files with Sound Juicer without problems. But after upgrading to Dapper, Sound Juicer seems not to know my mp3 profile any more. :confused: 

After starting it for the first time, I got an error message that it cannot initialize the currently used profile (which was the mp3 profile). However, when I checked, there were only profiles for .ogg and .flac.

Sadly, I changed the profile and cannot reproduce the error message. But when I try to add a new profile, sound juicer quits suddenly. 

gstreamer0.8lame is installed, mp3 playback is possible with Totem, XMMS, ...

Some information on my machine:

```
timo@ubuntu:~$ hdparm -i /dev/hdc

/dev/hdc:

 Model=PHILIPS CD-RW/DVD-ROM SCB5265, FwRev=TX03, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no

 * signifies the current active mode

timo@ubuntu:~$ sound-juicer
Could not fully determine drive profile 0: Error reading disc information

** (sound-juicer:7142): WARNING **: Error getting media type

timo@ubuntu:~$ sound-juicer --gst-version
GStreamer Core Library version 0.10.6
timo@ubuntu:~$ uname -a
Linux ubuntu.timo 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux
timo@ubuntu:~$

```

Personally, I prefer .ogg to .mp3 - but my mp3 player does not. :rolleyes: 

Any ideas?

Bye,
Timo

---

### Post by Marller on 2006-06-18
[QUOTE=Timokl]gstreamer0.8lame is installed, mp3 playback is possible with Totem, XMMS, ...[/QUOTE]

Sound Juicer in Dapper was upgraded to gstreamer0.10. Maybe if you installed gstreamer0.10-lame it might be the solution.

---

### Post by Timokl on 2006-06-18
[QUOTE=Marller]Sound Juicer in Dapper was upgraded to gstreamer0.10. Maybe if you installed gstreamer0.10-lame it might be the solution.[/QUOTE]

I tried that already - but the repositories have no gstreamer0.10-lame, there is only gstreamer0.8-lame. 

Bye,
Timo

---

### Post by sportrider on 2006-08-09
You have to install gstreamer-10 ugly-multiverse

---

### Post by Timokl on 2006-08-11
Yes, that helped. Thanks.

---

