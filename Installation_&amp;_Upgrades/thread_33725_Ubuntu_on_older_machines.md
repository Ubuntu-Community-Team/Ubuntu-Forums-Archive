---
title: "Ubuntu on older machines?"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by phend-one on 2005-05-11
Hi there,

I had ubuntu installed on a P4 1.7GHz computer at my dorm, but recently came home and thought about slapping ubuntu on an old P3 850MHz computer.

Has anyone any experience with linux performance on older PCs?

My specs for this computer are:
P3 850MHz
640Mb of PC133 RAM
GeForce 4 Ti 4200 (128MB)
Sound Blaster Live! 5.1
USB/Firewire PCI Card
Realtek Ethernet Card
SCSI ISA Card (for scanner)

Questions about this install:
1) Will I need /swap ?
2) How smooth is this going to be? Am I likely to experience worse performance than Windows XP?
3) Will there be support for my ISA SCSI Card (Currently not supported past Windows98)?

Should there be anything else to worry about?

Thanks for all your replies!

---

### Post by thecrimsonking on 2005-05-11
I installed Ubuntu on one of my older boxes with spectacular results.  Ubuntu runs noticeably faster than XP.  KDE is a little slower than Gnome though.
Specs:
600mhz P3
384MB pc133 ram
40GB WD 7200rpm HD 8MB cache
Radeon 7000 64MB PCI 
Sound Blaster (ES1371) PCI
Realtek NIC
2 CDROM drives
100MB Zip drive

I gave it a 400MB /swap  and I have not had any problems.

Sorry, I don't know about your ISA card or your Firewire/USB card.

Ubuntu installed just as smoothly as it did on my main pc.  Not a single problem.

I say give it a go, you will most likely be surprised by how great Ubuntu runs.

---

### Post by moleculardeconstruction on 2005-05-12
P2 - 400Mhz
256MB RAM

Runs fine. A little slow sometimes, but certainly useable. Fine for use with web browsing and writing documents. Doesn't really like having a lot of programs open at once, and more than about 10 tabs in firefox is slow.

I've also used ubuntu on a p200 with 64mb of RAM, which was quite slow. Probably would have been better with a more lightweight desktop.

But I have had no problems with running ubuntu on older hardware.

---

### Post by az on 2005-05-12
You should have no problems.  Unless it is a wierd scsi card, the fact that it is isa is not a problem.

Yes, ubuntu should run faster than windowsXP.

guided partitioning will create a swapt for you automatically.  You only need to worry about things like that if you do manual partitioning.

If you are keeping windows on tat machine, just start off by using the partitionner to shrink the/a windows partition.  That creates free space which you can then tell the partitionner to use with "guided partitioning"

---

### Post by GreatSunJester on 2005-05-12
P2 400, 512 meg RAM, 10 gig HD, integrated Matrox G200 video and Aureal Vortex2 sound card, old firewire card and NIC -- all detected and running.

---

### Post by derrick1985 on 2005-05-12
Cyrix II 350mhz
128mb SDRAM
ATI Video Card (no propriety drivers, too old)
ESS Solo Sound
CD Burner

All found and working properly, using XFCE, Gnome crawls slower than cold molasses going up a hill in january.

---

### Post by ylawayjdp on 2005-05-12
Installed it on a pentium 350mhz with 32mb ram was slugish when multi tasking and compliling but coped with the issue
J

---

### Post by Stormy Eyes on 2005-05-12
I've installed it on a Toshiba Tecra laptop with a Pentium Pro 233 CPU, 64MB RAM, a 4GB hard drive, and some kind of S3 video adapter. It's slow as hell with GNOME, but pretty sweet with just Openbox.

---

### Post by Nu-Buntu on 2005-05-12
You should get fine results with that setup, particularly with 640MB RAM. I would recommend going with a leaner desktop environment than Gnome or KDE, like others have mentioned here.

---

### Post by jfdill_2 on 2005-05-12
I have Ubuntu Hoary with GNOME running just fine on:

Dell Optiplex GX1
PII 450 MHz
256 MB memory
kernel 2.6.10-5-686

I have a bunch of services running:  apache2, snort, arpwatch, some other stuff.  It's not super snappy, but it works just fine if you don't mind waiting 5 seconds for a new window to open.  If you can't stand that, it should be possible to set up Xfce or another lite window manager.

---

### Post by pe1227 on 2005-05-16
I installed it Sunday on a PIII 500 w/128mb SD100  Ram and 20G HD.  Works pretty well and much faster than the previous Win2k pro.   \\:D/

---

### Post by az on 2005-05-16
[QUOTE=Stormy Eyes]I've installed it on a Toshiba Tecra laptop with a Pentium Pro 233 CPU, 64MB RAM, a 4GB hard drive, and some kind of S3 video adapter. It's slow as hell with GNOME, but pretty sweet with just Openbox.[/QUOTE]

Ha!  Toshiba Satellite 360CDT laptop, 166 CPU, 2.1 HD, C&T video.  Nya Nya!  Mine is smaller than your's!

---

### Post by DutchLau on 2005-05-16
[QUOTE=jfdill_2]I have Ubuntu Hoary with GNOME running just fine on:

Dell Optiplex GX1
PII 450 MHz
256 MB memory
**kernel 2.6.10-5-686**
[/QUOTE]

What on earth do you have the 686 kernel installed for on that system? i686 is optimized for Pentium Pro / Pentium 4 isn't it?  :razz:  i386 will do fine for you

---

### Post by jfdill_2 on 2005-05-16
[QUOTE=DutchLau]What on earth do you have the 686 kernel installed for on that system? i686 is optimized for Pentium Pro / Pentium 4 isn't it?  :razz:  i386 will do fine for you[/QUOTE]
Pentium II came after the Pentium Pro and it is very similar to the PPro, it is also an i686 chip with MMX extensions, otherwise the system could not boot with the i686 kernel.  I hope you will try the i686 kernel on a Pentium sometime :twisted:

---

### Post by ddocta on 2005-05-16
I run ubuntu on my 700Mhz Thinkpad X21.  It rund pretty good as long as there isn't too much multi tasking.  I would definitely suggest not using KDE, GNOME is pretty good, but for speed, XFCE does really good.

---

### Post by Rodrigo on 2005-05-17
My pc is an ooooold compaq presario (its like 4 years old)
AMD Duron 700Mh, 386MB pc100, 80GB western digital & 10GB Quantum fireball, Nvidia TNT2 32Mb (8x AGP  :razz: ).

well, ubuntu kind if works better... but (sorry its true) my "tweaked" winxp pro runs much faster... after removing all FX and useless services LOL  :wink: 

The only question I have is that: Is there any way to dissable FX (by FX I mean: window draws while moving it, or stuff like that) in Gnome? (the only thing I could found is in the gnome register... a key call animation or something like that.

Any way, Ubuntu runs superb in my pc and good overall in any "old" pc.

EDIT: I dissable the FX now ubuntu runs faster  :grin:

---

### Post by nianhbg on 2005-06-02
[QUOTE=Rodrigo]My pc is an ooooold compaq presario (its like 4 years old)
AMD Duron 700Mh, 386MB pc100, 80GB western digital & 10GB Quantum fireball, Nvidia TNT2 32Mb (8x AGP  :razz: ).

well, ubuntu kind if works better... but (sorry its true) my "tweaked" winxp pro runs much faster... after removing all FX and useless services LOL  :wink: 

The only question I have is that: Is there any way to dissable FX (by FX I mean: window draws while moving it, or stuff like that) in Gnome? (the only thing I could found is in the gnome register... a key call animation or something like that.

Any way, Ubuntu runs superb in my pc and good overall in any "old" pc.

EDIT: I dissable the FX now ubuntu runs faster  :grin:[/QUOTE]
 Im running ubuntu on a Toshiba Tectra 7000 p133 64 mb ram 4Gb hd and 3Com wireless card

---

### Post by Fugee on 2005-06-20
I'm using a self made K6/2-500 machine. It has a Netgear EA201 (an old ISA NIC), a Linksys wireless WMP54, Trident Providia 9685, Soundblaster, Lexmark Z515, 128 MB RAM...

This system has been a bitch to configure. Took some doing but I finally got most everything working, except the printer and the wireless NIC. Not too concerned with the wireless NIC tho. Still haven't found any good info on the printer. The only thing that worked correctly right off was the sound card. I'm playing with the different Window Managers at the moment. GNOME crawls, KDE is much more responsive. Openbox and Fluxbox are extremely fast, but not too appealing to me. XFCE4 looks promising and will play with it next.

---

