---
title: "failing durring base install."
date: 2004-11-05
forum: Installation &amp; Upgrades
---

### Post by FictionPimp on 2004-11-05
Both debian Sarge and Ubuntu both fail durring install on my PC. they will get to installing base system and error out on a random package.  I've tried a few different things to fix this. I changed my bios from enhanced to legacy for sata support, and i've tried turning off acpi. I've also tried both 2.4 and 2.6 kernels. I can install libranet, arch, gentoo, redhat, suse, and mandrake without issue. When the sata support in bios is set to legacy, the install disk can not find my dvd drive. When its in enhanced it works fine until it gets to installing the base system. I even suspected I didnt' have enough hard drive space so I let the installer partition my entire 160 gig drive into 2 partitions 158 for linux 2 for swap. I have also tried both reiser and ext3 file systems.

I suspect the problem to be with my sata drive, but I'm not sure how. I'm very sure the cd itself is fine, i've verified its checksums multiple times and even bought higher quality cd's. It also installs fine on my older amd box.

anyways, here's my system specs.

Intel i865perl motherboard onboard lan and sound
p4 3ghz 800mhz fsb
nvidia FX5900XT video card.
Sony 8X dvd burner (ide on secondary channel)
Samsung sata 160 gig (on sata 1)
1 gig of kingston ram.
ps/2 keyboard
usb mouse


If anyone has any suggestions, please let me know. I really like debians package managment. I'm currently use arch linux on this system, but I would really like all my systems to run the same distro or at least be debian based.

---

### Post by vbouw on 2004-11-06
Well I have the same problems with my geforce 5600 256 mb vard!
Mandrake/SuSe 9.1/Libtanet no problems!
I got the advice to install the Nvidea driver(s) nut HOW if I can't get into the Ubuntu program itself!
I think the Nvidea cards are a problem for most Linux OS,
Vic
PS: I'm a newie with linux and my english not so well cause I'm dutch
regards

---

### Post by az on 2004-11-06
WHat sarge installer did you try?  The RC2 is said to support tons of hardware...

---

### Post by vbouw on 2004-11-06
Sorry but what do you mean by Sarge?

---

### Post by FictionPimp on 2004-11-06
[QUOTE=azz]WHat sarge installer did you try?  The RC2 is said to support tons of hardware...[/QUOTE]


I tried pre-RC2. I'll download the rc2 installer and give it a try tonight.

**Update. I just tried to latest nightly of the debian sarge installer. Still getting the same error I get with Ubuntu and debian installers. it says this 

Moving /usr/info/dir to /usr/share/info/dir
Mkaing /usr/info/ a symlink to /usr/share/info

tar: Read 6144 bytes from -
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libc6_2.3.2.ds1-18_i386.deb( -- install):
subprocess dpkg-deb --control returned error exit status 2
Errors were encoutered while processing:
var/cache/apt/archives/libc6_2.3.2.ds1-18_i386.deb

If I run this over and over the actualy .deb file with the problem will change. But the error is always the same. This happens with netinstall and regular install cd's from debian, and the ubuntu install disk.

Any ideas?

---

### Post by Mighty Mik on 2004-11-07
With Sarge...lately i've had problems w/ the install...I think it's an archives problem...BUT i was able to install from the berkeley.edu site.

---

### Post by FictionPimp on 2004-11-11
Well, I finally got sarge to work by using that mirror. I still havn't been able to get Ubuntu installed though, oh well. I'll just use sarge, no reason to mess with it if its working.

---

