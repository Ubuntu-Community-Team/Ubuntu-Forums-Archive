---
title: "[SOLVED] Ubuntu 14.04 installation dual boot windows 8.1 black screen after install"
date: 2014-07-10
forum: Installation &amp; Upgrades
---

### Post by Delliriumy on 2014-07-10
I'm using ubuntu on a regular basis at work and never occurred such problem like this one @ home.
I've read so many topics about black screen after selecting "install ubuntu" but none of which ever helped(nomodeset etc.. for F6 launch options).

Details :

HDD : NTFS (to be shared with ubuntu).
GPU : NVIDIA GF GTX 660 / Intel HD GRAPHICS 4000
Motherboard: ASRock Z77 Extreme6

Any ideas or similar problems ? :/

---

### Post by oldfred on 2014-07-10
Are you booting with Intel video or nVidia enabled?
With nVidia you definitely need nomodeset, but Intel may need other settings & Z77 may need settings.

 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by Delliriumy on 2014-07-11
I finally found out the problem this morning when i had more time, well...kinda odd but god bless internetz.
In [this]("http://www.linuxforums.org/forum/installation/191033-massive-linux-install-fail.html") thread guy served a solution that at first glance was kinda odd, but it works :

"Its been a while but I finally figured out the problem a few days ago. It was as simple as moving my sata3 drives to the Intel sata port on the motherboard (SATA3_0_1, grey, next to black). I mistakenly had one of them plugged into the Asmedia sata port, which Linux apparently doesn't have a driver for. Burningbright, check your sata cables. I'm willing to bet you did the same thing."

Im not marking this thread SOLVED untill i install and run ubuntu properly.

---

### Post by David_A._Lessnau on 2014-09-25
> **Delliriumy said:**
> I finally found out the problem this morning when i had more time, well...kinda odd but god bless internetz.
In [this]("http://www.linuxforums.org/forum/installation/191033-massive-linux-install-fail.html") thread guy served a solution that at first glance was kinda odd, but it works :

"Its been a while but I finally figured out the problem a few days ago. It was as simple as moving my sata3 drives to the Intel sata port on the motherboard (SATA3_0_1, grey, next to black). I mistakenly had one of them plugged into the Asmedia sata port, which Linux apparently doesn't have a driver for. Burningbright, check your sata cables. I'm willing to bet you did the same thing."

Im not marking this thread SOLVED untill i install and run ubuntu properly.


I registered just to say thanks for that solution.  I've been wrestling with various forms of Ubuntu 14.04 Live CDs for a couple of days and couldn't figure out why they wouldn't boot (as a CD or as a USB flash drive).  The Asmedia ports were the thing.  Once I unplugged the drives I had connected to those, the Live CD booted fine.

Again, thanks.

---

