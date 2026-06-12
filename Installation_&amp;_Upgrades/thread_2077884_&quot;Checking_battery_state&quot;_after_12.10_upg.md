---
title: "&quot;Checking battery state&quot; after 12.10 upgrade"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by bkbk on 2012-10-29
The upgrade from 12.04 to 12.10 via the update manager seemed to go OK, but after rebooting a problem arose. After GRUB, I see the Lubuntu splash screen, but then I get a black screen that repeatedly flashes "*Checking battery state [OK}". This happens even when I try to boot in the older versions of Linux available through GRUB. From that black screen, I'm not able to get any prompt, but I can reboot with Ctl-Alt-Del.

I've gone to recovery mode and gotten a prompt from there. In these forums, there were suggestions to reconfigure lightdm and lxdm, but this didn't help me, assuming I was entering the right commands. I see that the problem is often associated with graphics drivers. This is an old PC and the graphics card seems to be SiS 65x/M650/740. I found that out by starting the PC with Puppy Linux on a USB drive.

Help would be appreciated telling me the specific steps to take.

---

### Post by funicorn on 2012-10-30
Basic information is needed, such as /var/log/Xorg.0.log,/var/log/kern.log,/var/log/dmesg

Also, please paste the output of `lspci`

Before you proceed with following, you'd better look into the above log files and see what happened during system boot.

----------------------------------------------------------------------------------------------------------------------------------------
As far as I know your graphical card should be driven by the old nvidia-173, so check it's been installed.
```

dpkg -l nvidia-173

```
If so, try to reconfigure it with 
```

dpkg-reconfigure nvidia-173

```
If not, install it
```

sudo apt-get install nvidia-173

```

If the installation fails, look into the error reported.

---

### Post by bkbk on 2012-11-04
Thanks for the reply, funicorn. Just got power back after the hurricane. I gave the lspci command after starting the pc with Puppy. (I tried to attach the log files, but they're too big to be posted.) Based on what you see here, should I attempt the nvidia-173 commands? Would I do them after starting the pc in Ubuntu's recovery mode? Thx.

lspci:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] C-Media AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0f.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:10.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

---

### Post by cozski on 2012-11-12
Hey, I've had a similar issue [http://ubuntuforums.org/showthread.php?t=2081346&highlight=checking+battery+upgrade](http://ubuntuforums.org/showthread.php?t=2081346&highlight=checking+battery+upgrade) but so far no response. At the minute just being able to boot into recovery mode would help but I can't seem to figure that out :confused: Any ideas? Thanks.

---

### Post by bogan on 2012-11-12
> **cozski said:**
> Hey, I've had a similar issue [http://ubuntuforums.org/showthread.php?t=2081346&highlight=checking+battery+upgrade](http://ubuntuforums.org/showthread.php?t=2081346&highlight=checking+battery+upgrade) but so far no response. At the minute just being able to boot into recovery mode would help but I can't seem to figure that out :confused: Any ideas? Thanks.Hi!. **cozski**, checkout you other thread, **bogan**.

---

### Post by cozski on 2012-11-13
> **bogan said:**
> Hi!. **cozski**, checkout you other thread, **bogan**.

Heading over now..... thanks ;)

---

