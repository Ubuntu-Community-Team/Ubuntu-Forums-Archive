---
title: "Another dual boot problem"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by garagestmarien on 2011-03-27
Okay, my system is acer desktop, celron 2.8ghz, 2gig ram, 2 hard drives.
Drive one 80g and running windows 7 ultimate. Drive 2 100g and free. Nvidia fx5900 turbo graphics with 256meg ram and 512 system shared.

I have tried many times to install 10.10 but have had no luck.
I can run it from the live cd and use everything except gparted, but when I try install from the ubuntu desk top, or from the cd booting up, it just hangs.
From the live cd I have tried to run gparted, but it just does a search and then crashes. I tried to send the error report, but that crashed as well!!!

I downloaded the gparted live cd and that runs, but also as soon as I open the gparted program it searches and crashes.

Any ideas how I can install 10.10?

(I have also tried wubi, but that just says no disk in drive and I can only clear that by rebooting windows - although I am looking for a permenant installation anyway)

---

### Post by oldfred on 2011-03-28
I have a newer nVidia card and have to use nomodeset both for liveCD and first boot. But the nVidia driver I use I think does not include your older card.

I had this in my notes:
Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

You should try the Generic settings as well as nomodeset.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by PCNetSpec on 2011-03-28
Are you running any type of RAID ?

Have you tried the Alternate Install CD ?

When you boot to the LiveCD desktop can you access both/any of the hard drives ?
(ie. is Ubuntu detecting both drives)

Are there any error messages displayed when you try to install ?

Can you give us the make and model of your motherboard.

---

### Post by garagestmarien on 2011-03-31
I have found the cause.
It was the usb sticks I had plugged in.
I unplugged them and then everything worked fine.
Weird that should be the cause, but that's what has solved my problem.

Many thanks for the help from all of you.

John

---

