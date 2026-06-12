---
title: "Trouble with drivers for hard disk controllers"
date: 2017-10-01
forum: Installation &amp; Upgrades
---

### Post by rg450 on 2017-10-01
Hi,

I'm trying to set up a XPEnology NAS server, based on an old computer. The computer is running the Synology open source distro, which does not contain a compiler, so I'm using Ubuntu to cross-compile driver modules for this system.

So far I have followed this guide: 
[https://hallard.me/how-to-install-kernel-modules-on-synology-ds1010-dsm-4-1/](https://hallard.me/how-to-install-kernel-modules-on-synology-ds1010-dsm-4-1/)


I've set up my build environment in /usr/local/x86_64-pc-linux-gnu/source/linux-3.10.x/
I've managed to compile a few drivers, and I got the onboard PATA controller to work this way, so I guess I'm doing the procedure correctly.

However, I have problems with the following cards: 
Silicon Image SIL0680: I've installed the driver but nothing happens
Silicon Image SIL3114: Seems to find the controller (what used to be drive 0 in synology is moved to drive 4, so I guess it sees the controller, but it does not find the drives attached)
Silicon Image SIL3512: I get nothing

I have inserted appropriate modules for the cards using "insmod", but this command does not return any error messages. Is there a way to see what's going on, and why this is not working?

For the Silicon Image -based controllers I found appropriate drivers by entering "make menuconfig". 


---------------


I also have a Highpoint RocketRAID 2640, which does not have a driver in the menuconfig. I have downloaded driver sources from their webpage, but I don't understand how to compile them.

According to the instructions that come with the driver I should enter this directory:
rr264-linux-src-v1.5 (driver directory)/product/rr2640/linux/
then build the driver from there. I've tried a lot of different things. Following the instruction in the readme, my guess is the command should look something like this:
make KERNELDIR=/usr/local/x86_64-pc-linux-gnu/source/linux-3.10.x/ CROSS_COMPILE=/usr/local/x86_64-pc-linux-gnu/bin/x86_64-pc-linux-gnu- ARCH=x86_64

which gives the following response:
grep: /usr/local/x86_64-pc-linux-gnu/source/linux-3.10.x//include/linux/version.h: No such file or directory
expr: syntax error
grep: /usr/local/x86_64-pc-linux-gnu/source/linux-3.10.x//include/linux/version.h: No such file or directory
expr: syntax error
../../../inc/linux/Makefile.def:88: *** Only kernel 2.4/2.6/3.x is supported but you use ..  Stop.

so I check, and it's correct. /usr/local/x86_64-pc-linux-gnu/source/linux-3.10.x/include/linux/version.h does not exist.

so a google search reveals that I'm (probably) missing the kernel headers. The kernel version should be 3.10.77, so I tried:
sudo apt-get install linux-headers-3.10.77
"Unable to locate package"
I don't know if this would have solved it, but this is as far as I got. My guess is that apt-get would only get me headers for the running kernel, and probably would not put the files where I want them.

---

### Post by rg450 on 2017-10-01
update: I tried inserting all 3 Silicon image controllers at the same time. Now I get their BIOSes upon boot, earlier I only got the BIOS for the 0680. The 3114 and the 3512 now works fine, and I have enough SATA ports in the system.

I came across a command: dmesg

it reveals that the 0680 is almost working, however at the end I get the following error:
findhostd uses obsolete (PF_INET, SOCK_PACKET)

Any way around this one?

Regarding the RocketRaid-card: I don't really need it now that I have enough SATA-ports through the SIL-cards. However, as it is a higher quality controller, I would prefer using it over the SIL, so I'm still interested in solving that one.

---

