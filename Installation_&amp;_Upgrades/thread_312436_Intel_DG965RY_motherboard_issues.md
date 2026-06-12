---
title: "Intel DG965RY motherboard issues"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by [D-Tail] on 2006-12-04
Since I'm experiencing troubles with my newly acquired Intel DG965RY motherboard and the E6300 Core 2 Duo processor accompanying it, I'll hope to find answers here. I spent all weekend on finding a definitive solution to get Ubuntu (don't care which version, I tried all from 5.04 up to the daily 7.04) working on this system. The 6.10 and 7.04 installer would fail on me saying something like "Can't access tty; job control turned off".
After consulting the #ubuntu channel on FreeNode, I tried the alternate install CD of 6.10. This worked a little better, but the installer stated that it couldn't find any CD-ROM drive. My DVD-ROM drives are connected on the only PATA bus on my motherboard, which is supposedly a Marvell one (hence, officially unsupported). The installer would ask for a driver disk. As an alternative, I was able to select an appropriate driver module. The latter didn't work. As for the driver disk: does anyone have an image for me? I'm totally new when it comes down to setting kernel parameters and that kind of things.

On a side note: I read about Marvell patches on the internet, yet I'm absolutely clueless about how to use these.

In the meantime, I'll be on Windows :(...

A summary of my system follows below:
- Intel DG965RY motherboard
- Intel Core 2 Duo E6300 CPU @ 1.86GHz
- 2x 512MB Dual Channel Twinmos PC5300 DDR2
- Seagate Barracuda 7200.10 320GB SATA-II HDD, connected to SATA0, IDE mode
- AOpen DVD1648/BKH DVD-ROM drive, connected to the PATA bus as master
- NEC ND-3540A DVD-RW drive, connected to the PATA bus as slave
- Generic floppy disk drive

---

### Post by sleeper.design on 2007-01-20
Hi! I'm using the Intel DG965SS motherboard, and had the same problem. 
The solution for me was using an usb cdrom. Booting from the installer cd went without any problems (using NO extra kernel parameters). Once installed, my internal dvd was recognized and now works.

---

### Post by [D-Tail] on 2007-01-23
> **sleeper.design said:**
> Hi! I'm using the Intel DG965SS motherboard, and had the same problem. 
The solution for me was using an usb cdrom. Booting from the installer cd went without any problems (using NO extra kernel parameters). Once installed, my internal dvd was recognized and now works.Hi Sleeper :) I would try that, but I don't have an USB key that large (it's just 64M). So unfortunately, that's a no-go for me (yet). I might try and borrow one from a friend of mine. Thanks again for the suggestion ^_^

---

### Post by sleeper.design on 2007-02-25
IT WORKS!!!! muahahaha!!! :-D

for everyone having the G965 chipset -> USE THE LATEST FEISTY!!! 

me so happy! ;)

---

### Post by Prof.Arronax on 2007-03-17
> **sleeper.design said:**
> IT WORKS!!!! muahahaha!!! :-D

for everyone having the G965 chipset -> USE THE LATEST FEISTY!!! 

me so happy! ;)
That's just dandy...  No link to what you're talking about?  (Please remember that many of us here are absolutely new to the Linux environment.)

---

### Post by sleeper.design on 2007-03-24
What I was referring to is to use the latest Feisty Fawn beta ([https://wiki.ubuntu.com/FeistyFawn/Beta](https://wiki.ubuntu.com/FeistyFawn/Beta)) to install the system. The kernel in Feisty comes with support for the IDE interface on the Intel D965 mainboards.

---

### Post by puck.midnight on 2007-06-09
> **sleeper.design said:**
> What I was referring to is to use the latest Feisty Fawn beta ([https://wiki.ubuntu.com/FeistyFawn/Beta](https://wiki.ubuntu.com/FeistyFawn/Beta)) to install the system. The kernel in Feisty comes with support for the IDE interface on the Intel D965 mainboards.

Hello,

Just wondering, is it fine to use the current Feisty Fawn or should I still use the Beta version you mentioned. I am using a DG965RY mainboard with a E6300 processor. Will there be any difference?

---

### Post by [D-Tail] on 2007-06-10
As a matter of fact, puck.midnight, I installed 7.04beta a week before 7.04final came out. It's still running, so the chipset problems seem to have been solved! :D

---

### Post by sleeper.design on 2007-06-11
It works with the "normal" Feisty as well. Don't worry.

---

### Post by puck.midnight on 2007-06-27
OK, I tried installing Ubuntu 7.04 and it ran a 'tty' problem. I'm really not sure what's wrong. Please help..

Specifications:
Mainboard - Intel DG965RY
CPU - Intel C2D E6300
HD - 1 SATA drive, 1 PATA drive
Graphics - On-board

I'm fairly new at this so any help would be nice.

---

### Post by [D-Tail] on 2007-06-27
I'm not really sure about your harddisk configuration. I have an Intel DG965RY, Intel E6300, Intel GMA X3000 (onboard graphics) and 1 SATA HDD (Seagate, but I'm not sure about that, it's been a while ;)). Anyway, using one SATA HDD, my configuration works. By the way, I've got an LG DVD-ROM (master) and a NEC ND3540A DVD-RW drive (slave) connected to the PATA port.

Another subject though, the mainboard has issues with the ND3540A. On Windows, I couldn't burn CD/DVDs with the DMA option turned on. I had to revert to PIO mode in order to burn discs. I'm not sure about Ubuntu, but I assume it's the same. Never tried to disable DMA for that drive though, besides, I even don't know how to do that.

The TTY problem you refer to is a typical Marvell/JMicron motherboard issue, or so I've read.

---

### Post by sleeper.design on 2007-06-28
My configuration is as follows:
Intel DG965SS motherboard w/ onboard X3000 graphics
Intel E6300 CPU
1GB RAM
2 SATA HDDs
1 PATA HDD
1 PATA DVD-RW

don't know about the TTY problem... it didn't happen to me.
i just boot from 7.04 cd and everything loads with no problems whatsoever...

@D-Tail: to disable dma type in terminal:
```
sudo hdparm -d0 /dev/hdc
```
replace /dev/hdc with whatever your dvd drive is

---

### Post by [D-Tail] on 2007-08-03
@sleeper.design: The DMA disabling procedure you described doesn't work for me. Of course, I replaced /dev/hdc with /dev/scd1, because that's the drive I want DMA disabled for. I get this:```
/dev/scd1:
 setting using_dma to 0 (off)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```Is this simply saying that I should buy a new DVD/CD burner? I'm kind of desperate now, as nothing seems to work, but reboot to Windows and burn a CD in PIO mode there...

---

### Post by hammedhaaret on 2007-08-17
I also had a tty problem at first, but I found a way around it.
([http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off))

but then, it failed to start the X server and i think it's the driver for my onboard Intel GMA X3000 graphics.
I read that the driver has just been released and is somewhat hard to install.

I'm still looking for a solution and I'll write it here if I find one.

---

### Post by sleeper.design on 2007-08-18
> @sleeper.design: The DMA disabling procedure you described doesn't work for me. Of course, I replaced /dev/hdc with /dev/scd1, because that's the drive I want DMA disabled for. I get this:```
/dev/scd1:
 setting using_dma to 0 (off)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```Is this simply saying that I should buy a new DVD/CD burner? I'm kind of desperate now, as nothing seems to work, but reboot to Windows and burn a CD in PIO mode there...

Try it without the "1" -> sudo hdparm -d0 /dev/scd
Thats because you're referencing the whole drive instead of a "partition" on the cd.


> also had a tty problem at first, but I found a way around it.
([http://ubuntuforums.org/showthread.p...rol+turned+off](http://ubuntuforums.org/showthread.p...rol+turned+off))

but then, it failed to start the X server and i think it's the driver for my onboard Intel GMA X3000 graphics.
I read that the driver has just been released and is somewhat hard to install.

I'm still looking for a solution and I'll write it here if I find one.
Are you sure you're using the latest (final) install cd ? Is it Feisty??
Like I wrote before... since using the Feisty Beta2, I haven't had any problems installing or running Ubuntu. I had a little problem with the resolution on X3000 and a new monitor but I got it work.

---

