---
title: "installation problem scan disk stuck at 47% help!"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by heylinux on 2010-06-01
Hi i trying to install my first linux distro kubuntu on to a "Foxconn R10-S4 Intel Dual-core Atom 330 Intel 945GC Intel GMA 950 Barebone " and my installation is stuck on "scanning disks @ 47% done" for about 30mins now can someone help me with this problem?

---

### Post by heylinux on 2010-06-02
i guess this is the reason why people are turned off by linux its not easy to install.. =(

---

### Post by mvidberg on 2010-06-02
In *most* cases, doing an install a linux (of practically any flavour) on a desktop computer goes well.  There are more often problems with installing to laptops.  

If it's getting stuck on scanning your disks, perhaps you have a hardware issue?

---

### Post by heylinux on 2010-06-03
i installed windows 7 it went flawlessly  ....now why is it that happened? can anyone show me why i had such a hard time to install?

---

### Post by wojox on 2010-06-03
> **heylinux said:**
> i installed windows 7 it went flawlessly  ....now why is it that happened? can anyone show me why i had such a hard time to install?

So you eventually got kubuntu installed?

---

### Post by Istrebitel on 2010-06-03
Well the problem indeed is in detecting your devices. I have same problem yet for me it hangs for ~3-4 minutes.

The problem source may be in unoptimal installer code (for example why do a second scan if you select something then go back from the drives page, making refresh button would seem better) or in driver problems or hardware or whatever.

Use common sense in that case, thats what i do! If something doesnt work - do something to go around!

What i would do is disconnect every disk, usb flashes and other devices like windows mobile pda that i dont need during instalation to prevent installer from ever identifying it. Because when i first installed kubuntu, it identified both a 4gb usb flash and my HTC Diamond (pda)'s sd memory card, which were of coruse not used at all at process of installation.

You only need to have access to the hard drives you will be repartitioning and installing kubuntu on during the installation process. You also need mouse, keyboard and monitor. Everything else might be disconnected, and if problems arise, should be. 

Well thats how i'd do. I suppose more professionals would advise something better, but so far, this might help you.

---

### Post by heylinux on 2010-06-03
no i didnt install ubuntu on the computer just win 7 ..the only thing i used to install was a pendrive with kubuntu with no cd rom drive and 300gb harddrive...  :confused:

---

### Post by thirdimage on 2010-07-29
HOW I FIXED MINE:
1. Booted into Kubuntu liveCD (first option in installer menu)
2. Figured out my hard drive was /dev/sda, using fdisk.
3. Ran the command: dd if=/dev/zero of=/dev/sda
4. Waited a few minutes and then hit CTRL-C to cancel formatting.

WHAT HAPPENED?
The hard drive had a partition scheme which Kubuntu's partition manager couldn't support.
Neither Fdisk nor GParted could remove it.
So, i used the "dd" command to completely zero it out.
You don't need to wipe the whole drive, only the partition table.
A few minutes of zeroing should suffice.

---

### Post by Plantface on 2010-08-03
That didn't work for me.

The problem must have been that the USB stick didn't use a [local sector size of 512 bytes]("http://blog.stochasticbytes.com/2010/05/installing-ubuntu-1004-server-on-usb.html"). I pulled out the USB stick during the installation when it was going to run partman... and I'll be darned, suddenly it got past the 'scanning disks' stage.

Seriously.

---

### Post by FatsWaler on 2010-12-13
> **Plantface said:**
> That didn't work for me.

The problem must have been that the USB stick didn't use a [local sector size of 512 bytes]("http://blog.stochasticbytes.com/2010/05/installing-ubuntu-1004-server-on-usb.html"). I pulled out the USB stick during the installation when it was going to run partman... and I'll be darned, suddenly it got past the 'scanning disks' stage.

Seriously.

I had the same problem found out I had a damn usb plugged into the back...pulled it out and she worked...WTF!

---

