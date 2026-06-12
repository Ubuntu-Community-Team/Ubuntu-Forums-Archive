---
title: "keep getting Errno5 input/output error on install"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by neatokino on 2008-02-03
I just put together a computer with a Gigabyte GA-EP35-DS3P motherboard, 4GB of Ram, a Western Digital Caviar 750Gig HD,  a Samsung DVD burner, a Gigabyte 8600GTS video card, and an e8400 Wolfdale 3Mhz processor.  This was my first build, probably overkill for what I need, but lots of fun to put together.    When I fired it up with the Gutsy 64 live CD, it worked perfectly, so I figured an install would be really easy.

I want this to be a pure Ubuntu install, no Windows.   When I start the installation process, the HD seems to get formatted and partitioned ok , but installation stops halfway into the installation process  and I get a window that says:

Failed to copy files;  faulty CD/DVD or hard disk

[Errno 5] input/output error

(followed by lots of stuff about how my disc, disc drive, or hard drive might be faulty).

At first, I figured there was something wrong with the DVD drive or the hard drive, both brand new,  but I've tried replacing both of them with working drives from another computer, and I get the same error message.  I then tried installing the 32bit version of Gutsy and got the same error message.

I tried using the alternate install disc, but that doesn't seem to want to boot up at all.

Does anyone have any idea what's happening here?  As I said, the 64bit live CD works quite well;  is there something in the BIOS that I need to set in order to allow Ubuntu to be written to my hard drive?
Any ideas????

TIA
Michael

---

### Post by Pearldiver on 2008-04-14
Hi neatokino,

I run into the same problem. got a GA-MA78GM-S2H motherboard, 2120gb Mactor and a 750gb Samsung HDD's, 2 GB dual channel ddr800 kit and a x2 BE-2400 processor in an antec Fusion case.

Have you already figured out what the problem is? Cause i tried everything but without any luck so i thing i have to switch to mediaportal....:(

Kind regards,
Pearldiver

---

### Post by valugi on 2008-04-17
This is a hard disk error. Try to format the disk or to check for phisical errors

---

### Post by xymor on 2008-05-18
I'm getting the same errors. I've tried hardy, hardy-amd64 and hardy-kubuntu and during the install a get a lot of 'faulty CD/DVD or hard disk'. 

To eliminate a falty hdd I did a fresh install of WinXP and then Edgy, successfully with both. 

I checked the forums and someone adviced to use the options 'noapic acpi=off -d 1 /dev/hdc', that did reduce the number or errors during isntall, but didn't eliminate them.

---

