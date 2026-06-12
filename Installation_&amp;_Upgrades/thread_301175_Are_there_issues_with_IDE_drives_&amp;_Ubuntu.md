---
title: "Are there issues with IDE drives &amp; Ubuntu?"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by azcazandco on 2006-11-16
Hi Everyone

Are there any known issues with installing Ubuntu on IDE drives?  I have been running Dapper for months and then upgraded to Edgy online and have had no issues other than self generated ones via tinkering (all of this is on a SATA drive). All of this changed today...

I installed a 250Gb Western Digital IDE Hd today and tried to get Dapper 64 bit to install, it installed no problem but soon after logging in it would just freeze and I could do nothing.  I then tried to install dapper 32bit and had the same problem and also with a fresh copy of Edgy Eft 32bit, from what I can gather I think it might be a problem to do with DMA although I am not going to pretend to know much about it.

From what I can gather when my computer boots up, it mentions DMA 2 and I currently have the following hardware:

K8t Neo Motherboard
AMD 64bit 3200+ Socket 754
Raedon 9600pro 128mb video card
2Gb RAM
1 x 200Gb Samsung SATA Drive
1 x 80Gb SATA Drive (unsure of make)
1 x 250Gb IDE Western Digital Drive

Can't think of anything else hardware wise but please let me know if you need more info. 

I hope someone can help me as this is quite frustrating.

Thanks in advance...

---

### Post by huygens on 2006-11-16
Hi,

Maybe you should divert your question to the [64bit forum]("http://www.ubuntuforums.org/forumdisplay.php?f=134") as I have a pretty similar configuration as yours and I am able to enjoy Ubuntu 6.10 on my IDE hard disk without problems, however I am using the 32bit version even though I could use the 64bit.

I have a K8 Neo Premium motherboard with an AMD Sempron (support 64bit instruction) and a 160GB IDE hard disk (the rest of the hardware is almost similar apart that I don't have SATA disks and I have less RAM).

Anyway, what is the output of hdparm? Could you try this command?
```
sudo hdparm -i /dev/hda
```
I'm just asking that because I'm a bit surprised by the fact that you mention DMA2... Seeing the size of your disk, I would have expected something else.
If you have time before the system freezes, could you send the output of dmesg?

Huygens

---

### Post by azcazandco on 2006-11-17
Hi, here is the output of that command... 

Model=WDC WD2500JB-00EVA0, FwRev=15.05R15, SerialNo=WD-WMAEH1172437
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

---

### Post by drphilngood on 2006-11-17
I resolved an identical problem by installing my OS to one of my two SATA drives and used the IDE for storage.  It was a conflict with my DVD drives.

---

### Post by huygens on 2006-11-17
You should ask your question to the 64bit forum. I have check your drive on internet, and actually it is working properly at UDMA5 (100Mbps) on all Linux 32bit.
Perhaps, in the 64bit release of the drive driver or on the VIA chipset driver of your mother board, there is an incompatibility.
If possible could you test with the same version of Ubuntu but in 32bit mode?

Huygens

PS:
One example of working drive like yours (even if considered slow) [http://kerneltrap.org/node/2251](http://kerneltrap.org/node/2251)
And another one where a disk controller (but from Promise and not VIA) cannot handle the drive properly under FreeBSD : [http://lists.freebsd.org/pipermail/freebsd-bugs/2003-August/002636.html](http://lists.freebsd.org/pipermail/freebsd-bugs/2003-August/002636.html) In a way you re maybe having a similar problem as they have. Try to connect your harddrive as master on the primary IDE bus. _/!\_ this may change the order of your drives name, prevented you from booting...

---

### Post by azcazandco on 2006-11-17
Okay, to give an update on this, I have been and bought an ATA133 compatible cable and now get the following when I run the same command so it looks like I have got the proper mode now.  The downside being that I definitely have the same problem...

 Model=WDC WD2500JB-00EVA0, FwRev=15.05R15, SerialNo=WD-WMAEH1172437
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=74
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

One wierd thing about this whole thing is that it always crashes if I visit the following page: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.31.5-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.31.5-inst.html)

Any further advice is appreciated, I could actually use the 80gb sata drive for my 64bit install but I would like to get to the bottom of this if I can...

Thanks again for any help.

---

### Post by huygens on 2006-11-17
So now I don't understand anymore... You can use your computer, but sometimes it crashes, more or less at unexepected intervals, apart when you access the given web page where you can reproduce the crash easily. Am I understanding you correctly ?
Hmmm, then I would not say it is a disk problem... But let's try further.
Do you remember more or less the time of the last crash? Could you look in the following file at the events that occured around that time:
/var/log/messages

What do you have there?

Huygens

---

### Post by azcazandco on 2006-11-18
Hi Huygens

Thanks for the help, I have mounted the ide drive on my working installation to get to the /var/log/messages.0 file (there was nothing in the messages other than Nov 17 17:14:11 localhost syslogd 1.4.1#17ubuntu7: restart.)

This what I can see towards the end of the file, I would have replied earlier but I am full of the flu so gave up yesterday and switched off my computer.

I hope you can make sense of this.


Nov 17 17:07:12 localhost gconfd (alan-5321): starting (version 2.14.0), pid 5321 user 'alan'
Nov 17 17:07:12 localhost gconfd (alan-5321): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 
0
Nov 17 17:07:12 localhost gconfd (alan-5321): Resolved address "xml:readwrite:/home/alan/.gconf" to a writable configuration source at position 1
Nov 17 17:07:12 localhost gconfd (alan-5321): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 17 17:07:12 localhost gconfd (alan-5321): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 
3
Nov 17 17:07:12 localhost gconfd (alan-5321): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 17 17:07:15 localhost gconfd (alan-5321): Resolved address "xml:readwrite:/home/alan/.gconf" to a writable configuration source at position 0
Nov 17 17:08:00 localhost kernel: [  294.995245] dd[5479]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffc1ed58 error 4
Nov 17 17:08:00 localhost kernel: [  294.995729] dd[5481]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffac7858 error 4
Nov 17 17:08:00 localhost kernel: [  295.001210] dd[5484]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffbe01a8 error 4
Nov 17 17:08:02 localhost kernel: [  297.932290] dd[5499]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007ffffff594e8 error 4
Nov 17 17:08:05 localhost kernel: [  297.933139] dd[5501]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffff9ca448 error 4
Nov 17 17:08:05 localhost kernel: [  297.938827] dd[5504]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffa82278 error 4
Nov 17 17:08:32 localhost kernel: [  327.614946] dd[5656]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffae3948 error 4
Nov 17 17:08:32 localhost kernel: [  327.615591] dd[5658]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffed1f68 error 4
Nov 17 17:08:32 localhost kernel: [  327.621035] dd[5660]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffd638c8 error 4
Nov 17 17:08:35 localhost kernel: [  330.604315] dd[5675]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffea9e58 error 4
Nov 17 17:08:35 localhost kernel: [  330.607176] dd[5677]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffb1c048 error 4
Nov 17 17:08:35 localhost kernel: [  330.615519] dd[5678]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffb38cc8 error 4
Nov 17 17:08:55 localhost kernel: [  349.991779] dd[5750]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007ffffff1aba8 error 4
Nov 17 17:08:55 localhost kernel: [  349.992374] dd[5752]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007ffffffe3e78 error 4
Nov 17 17:08:55 localhost kernel: [  349.997930] dd[5753]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffe2c0c8 error 4
Nov 17 17:08:58 localhost kernel: [  353.031773] dd[5768]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffb614c8 error 4
Nov 17 17:08:58 localhost kernel: [  353.034617] dd[5770]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffb121b8 error 4
Nov 17 17:08:58 localhost kernel: [  353.040561] dd[5773]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffa70378 error 4
Nov 17 17:09:19 localhost kernel: [  374.216089] dd[5920]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffdf8378 error 4
Nov 17 17:09:19 localhost kernel: [  374.216773] dd[5922]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffb2b398 error 4
Nov 17 17:09:19 localhost kernel: [  374.222363] dd[5928]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffcb38c8 error 4
Nov 17 17:09:22 localhost kernel: [  377.247657] dd[5943]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffbf5978 error 4
Nov 17 17:09:22 localhost kernel: [  377.250693] dd[5945]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffff84fea8 error 4
Nov 17 17:09:22 localhost kernel: [  377.259408] dd[5947]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffc7e758 error 4
Nov 17 17:09:37 localhost kernel: [  392.715051] dd[6017]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007ffffff7e2e8 error 4
Nov 17 17:09:37 localhost kernel: [  392.715652] dd[6019]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffed1f98 error 4
Nov 17 17:09:37 localhost kernel: [  392.721194] dd[6021]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffff9b1c78 error 4
Nov 17 17:09:41 localhost kernel: [  396.005428] dd[6036]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffff9533c8 error 4
Nov 17 17:09:41 localhost kernel: [  396.008531] dd[6038]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffff86a678 error 4
Nov 17 17:09:41 localhost kernel: [  396.014346] dd[6039]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffebd638 error 4
Nov 17 17:10:23 localhost kernel: [  438.560549] dd[6195]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffff95cbd8 error 4
Nov 17 17:10:23 localhost kernel: [  438.561119] dd[6197]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffbbbfb8 error 4
Nov 17 17:10:23 localhost kernel: [  438.566602] dd[6199]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffe8a968 error 4
Nov 17 17:10:26 localhost kernel: [  441.621314] dd[6214]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffba7438 error 4
Nov 17 17:10:26 localhost kernel: [  441.625175] dd[6216]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffbc8bc8 error 4
Nov 17 17:10:26 localhost kernel: [  441.630924] dd[6219]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffe959e8 error 4
Nov 17 17:10:32 localhost kernel: [  447.648154] dd[6361]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffa8dac8 error 4
Nov 17 17:10:32 localhost kernel: [  447.648706] dd[6363]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffcb62f8 error 4
Nov 17 17:10:32 localhost kernel: [  447.654184] dd[6364]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007ffffff87198 error 4
Nov 17 17:10:35 localhost kernel: [  450.735692] dd[6379]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffd11138 error 4
Nov 17 17:10:35 localhost kernel: [  450.738703] dd[6381]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffff8929a8 error 4
Nov 17 17:10:35 localhost kernel: [  450.744615] dd[6382]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffff807768 error 4
Nov 17 17:13:35 localhost kernel: [  630.294451] dd[8214]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffff98b968 error 4
Nov 17 17:13:35 localhost kernel: [  630.294986] dd[8216]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffdb90b8 error 4
Nov 17 17:13:35 localhost kernel: [  630.300473] dd[8217]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffc942c8 error 4
Nov 17 17:13:38 localhost kernel: [  633.449061] dd[8232]: segfault at 00000000037be913 rip 00002aaaaad3afa0 rsp 00007fffffca3438 error 4
Nov 17 17:13:38 localhost kernel: [  633.451967] dd[8234]: segfault at 00000000037be400 rip 00002aaaaad3afc0 rsp 00007fffffebd488 error 4
Nov 17 17:13:38 localhost kernel: [  633.457904] dd[8237]: segfault at 00000000000001c6 rip 00002aaaaad3afa0 rsp 00007fffffe20718 error 4
Nov 17 17:14:10 localhost exiting on signal 15

---

### Post by azcazandco on 2006-11-18
To give a quick update, I just started up my ide installed dapper 64bit and started doing updates via the update manager because it said there were some available.  It managed to do the first few and then hung, this is the final little portion of my /var/log/messages:

Nov 18 11:19:43 localhost kernel: [  314.037620] ppdev: user-space parallel port driver
Nov 18 11:19:46 localhost kernel: [  317.579527] Bluetooth: Core ver 2.8
Nov 18 11:19:46 localhost kernel: [  317.579533] NET: Registered protocol family 31
Nov 18 11:19:46 localhost kernel: [  317.579535] Bluetooth: HCI device and connection manager initialized
Nov 18 11:19:46 localhost kernel: [  317.579547] Bluetooth: HCI socket layer initialized
Nov 18 11:19:46 localhost kernel: [  317.605427] Bluetooth: L2CAP ver 2.8
Nov 18 11:19:46 localhost kernel: [  317.605432] Bluetooth: L2CAP socket layer initialized
Nov 18 11:19:46 localhost kernel: [  317.646699] Bluetooth: RFCOMM socket layer initialized
Nov 18 11:19:46 localhost kernel: [  317.646722] Bluetooth: RFCOMM TTY layer initialized
Nov 18 11:19:46 localhost kernel: [  317.646724] Bluetooth: RFCOMM ver 1.7
Nov 18 11:19:58 localhost kernel: [  329.455059] [drm] Setting GART location based on new memory map
Nov 18 11:19:58 localhost kernel: [  329.455070] [drm] Loading R300 Microcode
Nov 18 11:19:58 localhost kernel: [  329.455138] [drm] writeback test succeeded in 1 usecs
Nov 18 11:24:59 localhost exiting on signal 15
Nov 18 11:25:00 localhost syslogd 1.4.1#17ubuntu7: restart.
Nov 18 11:29:06 localhost gconfd (alan-5302): starting (version 2.14.0), pid 5302 user 'alan'
Nov 18 11:29:06 localhost gconfd (alan-5302): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 
0
Nov 18 11:29:06 localhost gconfd (alan-5302): Resolved address "xml:readwrite:/home/alan/.gconf" to a writable configuration source at position 1
Nov 18 11:29:06 localhost gconfd (alan-5302): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 18 11:29:06 localhost gconfd (alan-5302): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 
3
Nov 18 11:29:06 localhost gconfd (alan-5302): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 18 11:29:08 localhost gconfd (alan-5302): Resolved address "xml:readwrite:/home/alan/.gconf" to a writable configuration source at position 0
Nov 18 11:29:29 localhost gconfd (root-5424): starting (version 2.14.0), pid 5424 user 'root'
Nov 18 11:29:29 localhost gconfd (root-5424): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 
0
Nov 18 11:29:29 localhost gconfd (root-5424): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Nov 18 11:29:29 localhost gconfd (root-5424): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 18 11:29:29 localhost gconfd (root-5424): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 
3
Nov 18 11:29:29 localhost gconfd (root-5424): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

---

### Post by huygens on 2006-11-18
I'm sorry I can't help you further, it seems from your post that dd (a disk utility) is crashing. So you're probably right to spot a hard disk problem. But this is now too low level for me...

Sorry,
Huygens

---

