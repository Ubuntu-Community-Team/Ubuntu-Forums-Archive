---
title: "Breezy Stalls on Core Packages"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by grapea on 2005-12-01
This is driving me up the wall.  Breezy install keeps stalling between 5 - 55% while installing base system, usually at 31-32% (while installing core packages).  I have tried this on 4 identical (almost) machines many times and using 2 different pressed installs.

Live CD works no worries.

Machines are:
AMD-K6 300-500Mhz
256Mb RAM
ATAPI CD-ROM
Samsung SV0432D LBA, UDMA 66 4.4Gb IDE HD

In frustration found an old install of TurboLinux 6 and tried an install of that - worked fine.

Any help very much appreciated - I am a newbie to linux so go easy on me.
:confused:

---

### Post by bwog on 2005-12-02
Did you check the CD checksum?

Perhaps you need special bootparameters, they are found in the install CD help (F1 to F8 ).

---

### Post by grapea on 2005-12-04
[QUOTE=bwog]Did you check the CD checksum?

Perhaps you need special bootparameters, they are found in the install CD help (F1 to F8 ).[/QUOTE]


Thanks - yes checked it OK and tried a number of bootparameters - with varied results (i.e. sometimes only 6 percent through installing base system).  Most commonly I get 31/32 percent before lockup).

---

### Post by bwog on 2005-12-04
What might help is to search the net for your motherboard or chipset in combination wit linux (or even ubuntu). Chances are that somebody already solved your problem.

You amount of RAM is OK, but the disk are small, therefore you might consider this light version: [https://wiki.ubuntu.com/InstallingXubuntu](https://wiki.ubuntu.com/InstallingXubuntu)

It may help to put more hardware specs here, but there are no guarantees ofcourse. It should work in the end.

---

### Post by erik187 on 2005-12-07
I'm having the same problem. My computer freezes at 32-34% of the core installation. I tried to install Xubuntu but still have same problem. Here are my computer specs:

HP Vectra VL 6/400 Series 8 DT (Pentium 2 400Mhz)
448 Meg RAM
Samsung SV0432D 4.4Gig

I have successfully installed Damn Small Linux 1.5 on this system but not Ubuntu. Perhaps it's the hard drive.

---

