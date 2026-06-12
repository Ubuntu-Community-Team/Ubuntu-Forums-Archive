---
title: "Intel DQ965GF"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by spetroff on 2007-03-19
Sadly I only looked as far as Intel's site before buying this board. Inspite of what Intel says, the board seems to hate all variants of linux. Most distributions can't seem to find the dvd, and some cannot see the nic. I've heard tales that these chipsets will allow network installations, but I will eventually need the dvd. I've spent way too much time on the net looking for clues, but alas I'm a linux n00b. It is also rumoured that a 2.6.18 kernel can handle this board, but I tried to get FC6's livecd to boot with no joy either. Has anyone actually got one of these things running?

mobo: Intel DQ965GF
cpu: Intel 925 3GHz Dual Core
ram: 2GB
hdd: 2 @ Seagate 250GB SATA2 

Thanks.

Shane

---

### Post by corvex on 2007-03-30
The problem is that this chipset (intel 965) doesn't have builtin IDE controller. On your (and mine :) ) motherboard IDE interface is implemented via 3rd party controller.

Some users report that using IDE to SATA converter (pluging IDE CDROM to SATA port) solves your problem.

Good luck.

Regards,
Corvex

---

### Post by dapperteo on 2007-04-01
I have the same motherboard. I think it's a scandal that it doesn't work after so many months. I don't know exactly whose is the fault, but I write just to let you know that I'm very unsatisfied and that I'll probably avoid to use linux for the future or to recommend it. I'm really tired of spending my trying the right combination of parameters to let it install.
Do you want to know what everyone who has this motherboard and tried to install linux think? Well, simply that the so hated Windows works out of the box without waiting months or passing parameters. That's it.

---

### Post by SharkRider on 2007-04-28
I have the same system board, but running the Intel Core 2 Duo procs (E6420).

I was able to get (K)Ubuntu installed (alternate CD method), but that is pretty much it. I then ran into other issues trying to stabilize the OS in multi-user mode. [Here]("http://ubuntuforums.org/showthread.php?t=426234") is my current issue.

If I can overcome this dbus problem, I will be good to go (I hope).

I suspect that it is a bug with dbus? :confused:

---

### Post by SharkRider on 2007-04-28
I found the key! In my search through all resources, the answer for all Linux distros appear to be this:

Append "all-generic-ide" to the end of the kernel line in grub.

My earlier [post]("http://ubuntuforums.org/showthread.php?p=2553061") goes over how I installed (K)Ubuntu on my Intel DQ965GF board.

This [link]("http://kerneltrap.org/node/7020") turned me towards the find.

There is hope for this great performing/cool running systems and Linux! :KS

---

