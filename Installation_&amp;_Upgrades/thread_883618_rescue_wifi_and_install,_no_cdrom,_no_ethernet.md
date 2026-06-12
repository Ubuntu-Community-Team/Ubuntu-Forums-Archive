---
title: "rescue wifi and install, no cdrom, no ethernet"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by remifrommontpellier on 2008-08-08
Hello,

I have a tricky problem with an old dell inspiron laptop: The on-board ethernet card packed up. During the upgrade to feisty, the cd drive packed up too, leaving me with an unfinished system to which i can login but only in terminal mode. :(

At that moment in time (10 months ago) i got hold of a different laptop and left the dell in its case. Unfortunately that other laptop, a thinkpad T40, cannot run its soundcard with ubuntu - several posts on this subjects on the forum - and i now need sound, so i'm trying to resuscitate the dell.

The dell has a broadcom on-board wireless card:

lspci | grep Broadcom
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

It had wireless working with dapper using ndswrapper, and the files are still on the hard drive:

:~/Broadcom$ ls   (were i downloaded all drivers to get wifi running)
bcmwl5.inf bcmwl5.sys ndiswrapper-1.48 ndiswrapper-1.48.tar.gz sp34152.exe

but if i run $ndiswrapper -i bcmwl5.inf

i get an error message: ndiswrapper command not found.

this is were i got stuck as i normally sort ubuntu problems with apt-get install. Not now that i've lost network connection!

I have tried to do a network install, but the dell doesn't connect to the thcp server (i don't get that error with the thinkpad so it points to the non working on-board network card)

I could try to use an old pcmcia network card - my first ubuntu laptop had one - but how can i transfer the configuration files without floppy or cdrom? .

Or do an install with a usb stick, but before wiping the hard drive i'd like to try to rescue the existing system by getting the wifi to work and then running the upgrade from it. :confused:

Any help would be appreciated. Thanks guys!

---

### Post by mattduckman on 2008-08-08
i'm a bit confused, but if you want to install ndiswrapper, you can download the packages from ubuntu, use a usb stick to transfer them to your laptop, and use dpkg to install them. here are the packages that you need, the download links are at the bottom of the pages:

[http://packages.ubuntu.com/feisty/ndiswrapper-common](http://packages.ubuntu.com/feisty/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/ndiswrapper-utils-1.9)

---

### Post by remifrommontpellier on 2008-08-08
Thanks for your reply.

ndiswrapper is already present on the system. wifi did work on that computer, using ndiswrapper and the broadcom driver, until the cdrom packed up during a distribution upgrade. Since then, the wifi card doesn show up on ifconfig/iwconfig.

All the advice i found rely on ubuntu/debian amazing ability to download anything it needs from repositories.

But until i fix wifi on this machine, i cannot download anything!

cheers!

---

### Post by mattduckman on 2008-08-08
this error from your first post implies that ndiswrapper is either not installed or not properly installed:

> **remifrommontpellier said:**
> 
i get an error message: ndiswrapper command not found.


while on package.ubuntu.com, i noticed that starting with feisty that ndiswrapper-utils got renamed to ndiswrapper-utils-1.9, which might be why your having problems.

i suggest you just try it, since i don't have any other ideas :)

---

### Post by remifrommontpellier on 2008-08-08
hmmm, that's a good idea.

but, should i check which kernel is still running first? i was upgrading from dapper when this happened, and i don't know which is now running.

so I run the command "lsb_release -a" and learn that release 7.10 gutsy is running on that machine.

does this mean that the version of ndiswrapper on the hard drive is outdated and cannot run with gutsy?

cheers!

---

### Post by remifrommontpellier on 2008-08-11
Some progress: i've installed hardy on this machine with a usb stick :D

No wireless yet, it's a broadcom 4309 chipset so needs some broacom copyrighted firmware that cannot be distributed. these files need to be downloaded separately and then built. 

i followed these guidelines: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) 

Unfortunately, when running the "make" command, i got floaded with error messages and couldn't install the software.

I wonder if i should use ndiswrapper instead...

---

