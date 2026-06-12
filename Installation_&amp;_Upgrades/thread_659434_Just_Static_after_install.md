---
title: "Just Static after install"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by silverwj on 2008-01-05
I just installed mythbuntu with an ATI TV Wonder 200.

Everything seems to work (chanels, guide, detection, etc.), but when I try to watch TV all I see is a replaying static clip and a dull tone.

Has anyone ever seen this.  I tried all cable us-cable* & us-bcst channel frequency tables as I wasn't sure what cable to use and I wanted to know whether the air waves worked.  I can't really test out on the airwaves though because I'm too deep in a concrete jungle to get any reception.

I read some other posts and did see someone suggesting that I try this...

myth@manx:~$ cat /dev/video0 > /tmp/video.mpg
cat: /dev/video0: Input/output error

And I have this information...

myth@manx:~$ /usr/bin/lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by silverwj on 2008-01-05
Followed this guys advice:

[http://ubuntuforums.org/archive/index.php/t-574425.html](http://ubuntuforums.org/archive/index.php/t-574425.html)

And now getting a blank screen with no sound

---

### Post by silverwj on 2008-01-05
I changed my resolution to 800 x 600 and it works now.  Thanks for listening.

---

