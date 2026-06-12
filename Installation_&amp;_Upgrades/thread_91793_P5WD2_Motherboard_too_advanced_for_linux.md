---
title: "P5WD2: Motherboard too advanced for linux?"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by UnknownEntity on 2005-11-18
Has anyone had sucess installing any Linux distro on this motherboard?  I have tried Xandros 3.02, and Ubuntu 5.10 and neither of them work.  They each have issues either detecting the hard drives, or cd-rom drive.

Ubuntu told me it was unable to mount the cd-rom drive.  I have a Plextor 716A ATA-133 drive.  However, that controller is integrated with the SATA chipset, which also supports RAID 0,1,5,10.

Is that controller just too advanced for linux to use?

I have the ASUS P5WD2 Premium.

This is it's storage support info:
Storage/RAID
·_Intel ICH7R South Bridge:
·_1x UltraDMA 100/66/33
·_4x SATA I/II ports (3GB/s) with RAID 0, 1, 5, and 10 support

·_Silicon Image 3132 SATA controller:
·_1x Internal Serial ATA I/II
·_1x External Serial ATA

·_ITE IDE Controller:
·_2x UltraDMA 133/100/66

Thanks for any help.

---

### Post by UnknownEntity on 2005-11-18
/bump

---

### Post by JLChafardet on 2006-01-27
i was about to do the same question as i have the same mobo and it gave me the same problem some days ago, i will try to solve this. i think i know a way to cheat the installer.

I'll let you know.

---

### Post by JLChafardet on 2006-01-27
by the way, i tried Fedora4 for x64 and x86 and it installed flawlessly. just i dont like redhat based oses for my desktop.

---

### Post by JLChafardet on 2006-01-27
ok here we go.

Turn off the computer, and move the cd rom drive to the blue ide (PRI_IDE)

Turn on

go to the bios, and reset to default (RE-Overclock if you did had OC), go to the boot priority page, and select the cd rom as primary option.

save and exit.

put the cd on the drive, and install. it worked for me.

regards.

---

### Post by JLChafardet on 2006-01-28
the only thing i see is im having problems with Ubuntu 5.10 x64, some software tend to die.... im considering on moving back to ubuntu 5.10 for i386(32 bits)

---

### Post by JLChafardet on 2006-01-31
back on 32 bits, way more stabler, now i can use my software without issues :p

let me know if you managed to install ubuntu on your P5WD2 P

---

### Post by javierfh on 2006-06-07
[QUOTE=JLChafardet]back on 32 bits, way more stabler, now i can use my software without issues :p

let me know if you managed to install ubuntu on your P5WD2 P[/QUOTE]
Hello, i managed to install ubuntu into that same mother board, but im trying to monitor the CPU temp and M/B temp, but i cant succeed so far.
Have you managed to install and make lm-sensors to work?

I would appreciate any help you could provide me.

---

### Post by JLChafardet on 2007-01-14
No my friend. in fact, im having problems now with the full speed link of the network cards.

I have a small network here at home (2 desktops and 1 laptop), one of the desktops is the one with the P5WD2 Premium, 2 1gbps lan nics (Intel Tekoa Ethernet, Marvel Yukon 88E8001), the other one has a crappy advantek networks 1gbps pci nic card on it, and the laptop has a broadcom 1gbps nic.

Im NO WAY IN THE WORLD able to get the network to work at 1gbps on linux (yes yes, im not expecting a 100mb/s transfers, but at least, like on windows, 450mbps is good for me) differently than on windows that it does.

Im looking on the intel page and the marvel page to get certified drivers(if they even exists) to try to get them to work at the highest speed possible.

this enviroment is a "test" enviroment where i build tests for my job (system administration) my pc right now is the laptop (Dell XPS laptop) the other 2 pcs are "laboratory dummy pcs".

so, I will be looking forward to have this issues solved, if i manage to get this solved soon, I'll restart playing with the lm-sensors issue.

---

