---
title: "Ornery computer locks up on Ubuntu startup"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by Nadim on 2006-09-13
I recently decided to repurpose one of my slightly older machines, and due to all the good things I've heard, decided to give Ubuntu a try.  Firing up Dapper Drake in live mode, it locks up hard during the boot up process (last message printed "Preconfiguring networking...").  

I tried a few of the more common suggestions / settings, like "acpi=no noapic nolapic", but no joy.  Most of the instructions are for Breezy Badger, so I'm assuming that the right way to modify options in Drake is to hit F6, remove the "--" from the end of the boot line, and add any options there.

Wondering if it was just Ubuntu, I tried a couple other distros...Knoppix 5.01 failed during bootup at the "autodetecting hardware" line, and Mandriva failed as well (forget exactly where, but same symptom...hard lock at bootup).

Strangely, however, Xubuntu (6.06.1) worked just fine, with just the default options!  However, I'd really like to go with the full Ubuntu distro, so I don't think that's a good long term solution, but might be useful in figuring out what's going on. 

Here's my machine spec:
AMD Tbird 1.4 GHz
Asus A7vbx mobo
512 MB RAM
Asus V8200 GeForce 3
Sound Blaster Live Platinum w/Live Drive
Plextor PX-w4824A CD-R/W
Toshiba SD-M1502 DVD-ROM
160GB Seagate HD
Dell FP1907 monitor

The help in the Dapper Drake installer sort of led in circles when trying to find any sort of Expert mode to step through things more carefully, so I'm not sure quite how to do that.  

Any ideas on things to try, or anyone run into problems of this sort, or with some of this hardware, before?

Thanks in advance!

      -Nadim

---

### Post by orb9220 on 2006-09-13
Preconfiguring networking..... You didn't list networking. Onboard lan? wireless?

Can you disable networking by bios or unplugging router to see if it boots cd?

---

### Post by Nadim on 2006-09-13
Sorry, didn't mention networking because I don't have anything installed other than the mobo's 100 Mbps Ethernet port.  I don't have a network cable plugged in at the moment, either.  I looked in the BIOS, but did not see any option to disable the onboard LAN port.

As for the last message to appear before the machine locks up, I'm worried that I'm chasing my tail a bit on this one.  Mandriva locks up after mounting the cd drives, knoppix locks up during its HW autodetect algorithm, and Unbuntu is locking up after saying that it's configuring the network.  Is there a good way to get more detail regarding exactly what it is doing...maybe that will turn something up.

---

### Post by Nadim on 2006-09-14
For anyone stumbling on this thread with similar problem, I found the answer.  I knew it didn't seem right for xubuntu to work and not ubuntu...turns out I had the 6.06.1 xubuntu disc, but only 6.06 ubuntu.  The 6.06.1 ubuntu disc fixed the problem.  

It's a little surprising that Knoppix, Mandriva, and Ubuntu would all have the same lockup problem, then the .1 maintenance release would fix it, but it's working fine now, so I'll just be happy and move on...

---

