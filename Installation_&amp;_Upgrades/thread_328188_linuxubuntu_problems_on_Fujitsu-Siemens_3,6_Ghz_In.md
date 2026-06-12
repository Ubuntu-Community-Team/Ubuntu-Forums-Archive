---
title: "linux/ubuntu problems on Fujitsu-Siemens 3,6 Ghz Intel computer"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by jsorhaug on 2006-12-30
Hi!

I am almost giving up Linux on my computer, but I will give it a last shot here.

I have tried for two weeks now to get Ubuntu 6.10 up going on my Fujitsu-Siemens 3,6 GhZ Intel Pentium 4 computer. I have also tried Fedora and Kubuntu 6.10, Kubuntu 6.0.6 - but they all seem to fail cooperating with my computer.

The most frequent problem is due to installation. Each time I try to install from Live-CD (via KDE/Gnome) the installer crashes, giving me an error report. I have not written it down, because it stops on various places, sometimes in the beginning of the installation, sometimes when it comes near to closure. Sometimes the Live-CD will not boot at all, leaving me with a blank screen (and the "-"sign up left on screen).

When installing via text-mode from install DVD, it usually is OK until installing GRUB. I get an error message telling me that GRUB wil not install and Lilo will not either.

From time to time (I have installed over and over again for about 10 times) everything seems OK, but when booting into Kubuntu either the screen freezes under boot or sometimes after typing username and password.

I have also problems with programs closing automatically without any error report or whatever. And, finally, I have not once managed to get a clean shutdown or reboot. The system just freezes, or goes black, or just works and works and works and works.

I am starting to believe that there are something about my hardware that Linux does not support - as both Kubuntu, Ubuntu and Fedora 6 all fails to install or work properly.

I have 2 SCSI Hard Disks (ST3200822AS (200 GB each)); one I use for WinXP and one I want to use for Linux. My motherboard is FUJITSU SIEMENS D1826-G, chipset is Intel i915P and I have 2GB DDR-ram. My videocard is RADEON X600 PRO-4.

Anybody got a suggestion on what to do? Should I try older, more stable releases, can I compile the Linux kernel on my own to prevent failures - or should I just stick with smelly old Windows?

Please help, as I am almost giving up Linux.

---

### Post by logos34 on 2006-12-30
have you tried editing the [boot options]("https://help.ubuntu.com/community/BootOptions") line on the start screen? (ie 'noacpi', 'noapic', 'nolapic', etc.)

---

### Post by nacho32 on 2006-12-30
To me it sounds like bad media burn, I'm no linux pro , but thats what is sounds like to me, and or hardware releated,  cpu -heat-voltage

---

### Post by jsorhaug on 2007-01-18
Yeah, I think there may be a hardware problem with my CPU. Sometimes Win XP also crashes while performing heavy load tasks - but not as frequent as Linux crashes. Ubuntu is currently on hold for me, as my lease contract on my computer expires - and I probably am getting a complete new pc.

---

