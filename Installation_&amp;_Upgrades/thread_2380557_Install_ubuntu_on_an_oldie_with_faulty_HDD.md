---
title: "Install ubuntu on an oldie with faulty HDD"
date: 2017-12-19
forum: Installation &amp; Upgrades
---

### Post by gaslight on 2017-12-19
I am stuck with a laptop that has 1Gb ram and a faulty 160gb hdd (with bad sectors).

It got me to my worst. Nothing seems to work.

I want to install ubuntu on it, even if that means to only use like 20gb partition, that would be ok.

What I've tried:

Booting puppy from live cd. 
Ubcd.
Gparted live. 

Using all of these to make a bootable usb (sd card) - it just doesnt work. The Sd card is never bootable, no matter if I use UNetBootin, or just dd, no matter how I format it, or what OS I put on it. 

I found (L)ubuntu 12.04 that fits into CD.

The cd is kind of recognized and starts "kind of booting" (no errors ie), but just hangs at the blank screen with a blinking cursor.

The Ubuntu mini cd boots fully, but it doesn't see my wireless network, and there is no way to connect a cable, as I'm using my phone to share a portable hotspot. Ubuntu mini doesnt get that. Not 16.04, or below, at least. 

Should I try an even older (l/k/x)ubuntu release? I'm running out of empty cds now too. 

All I need is to put any reasonable OS on that pc, just to launch wine, or dosbox, or at least a distro upgrade. 

Any ideas?

---

### Post by mastablasta on 2017-12-19
replace the HD drive. you should be able ot get a used one cheap. if not and if it has a SATA plug you could maybe go with a new smaller SSD drive. 

what is the GPU? what is the CPU used in it? 

maybe you need to boot it with nomodeset option. more: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also you should be able to boot from USB. it it can't boot form USB then i suggest you load boot loader such as PLOP on CD and then use it to boot from USB. that way you will use only one CD and use USB for the tests of live distros.

---

### Post by oldos2er on 2017-12-19
Lubuntu 12.04 is long out of support, I suggest you install a supported version.

---

### Post by mörgæs on 2017-12-20
The minimal ISO is, as the name suggests, minimal. One can't expect it to support all hardware.

I recommend that you bring the computer to a place with wired internet access when installing from the minimal ISO. When the minimal system runs you can install the software needed for the wirefree access.

---

