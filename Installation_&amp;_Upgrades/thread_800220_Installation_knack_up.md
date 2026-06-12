---
title: "Installation knack up"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by wishful9 on 2008-05-19
trying to install ubuntu 64 8.04, hardy.  tried alternative with little joy.

firstly cd wrote incorrectly and had corrupted files.
second time passed cd check

this time though it froze after an error involving my wireless broadcomm piece of rubbish.

and a display about kernel panic, not a software issue, and then time unstable delta=4034204893ns or something to that effect.

heard fb=false may work but i've no idea how to do fb, and whats all this noapci, etc?

anyway trying torrents of alternative and live cd again

by the way laptop is hp pavillion zv5255eu.
nothing but trouble!

---

### Post by Cap'n Skyler on 2008-05-19
can you run it with the live cd?

---

### Post by wishful9 on 2008-05-22
tried live cd
same problem gets to a point then nothing but the caps lock light flickering.

tried upgrade within update manager, installs fine but come boot up, same problem!?

guess i'm sticking with 7.10 for now.

---

### Post by Cap'n Skyler on 2008-05-22
carp!!
the 'Buntu is really good about getting in and booting on just about everything.sorry i am no use for getting beyond that--we need someone with more skillz than i to get past this.
can you try another live cd and see if it too hangs?
maybe try a knoppix or puppy live cd?
Knoppix has near God-like hardware detection,it SHOULD go on and start up for ya.
if knoppix hangs too,might be an indicator that there is something on your comp or settings that is not liked.
good luck--post up more when you can.

Moofs

---

### Post by wishful9 on 2008-05-22
tried knoppix live cd works fine just like ubuntu. it's just i want the most recent version.  

it is a hp pavillion laptop from about 2004 so it's on it's way out but had a recent injection of optimism for the old girl after converting completely from windows, runs like a new computer now!

i'll just wait for a major update but i'll keep it open incase a ubuntu wizard comes along.

---

### Post by sickofthesea on 2008-05-23
I've got the same problem trying to install Xubuntu AMD64 8.04 on an HP Pavilion zv5358ea. Hangs on install with nothing but the caps lock light flashing.

It's had several versions of Ubuntu on this laptop over the years, the only problems being the broadcom wireless and the card reader. This is something new. I've got used to finding workarounds on this laptop so I'll post if I find one - I'm working on it.

Rgds,

Martin

---

### Post by sickofthesea on 2008-05-23
Mmmm, not this time it seems. I've had enough of trying now. Looks like this will be the first 'buntu that won't install on my lappy.

It seems to be a kernel/hardware issue. The flashing caps light is definitely a kernel panic and apart from it reporting the following I have no idea what the problem actually is or whether there is a way around it;

HARDWARE ERROR
CPU 0: Machine Check Exception         4 Bank 4: b200000000070f0f
TSC 1c82864c2e
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor.
Kernel panic - not syncing: Machine check
Clocksource tsc unstable (delta = 4687308745 ns)

I think it might be buggy nForce chipsets in these models of laptop, in which case there's probably not a lot we can do except cry!!

Rgds,

Martin

---

### Post by wishful9 on 2008-05-25
exactly what i got bit o a mystery. i might try removing the wireless card as i'm sure it said something about broadcom. i tried upgading in gutsy as i said and blacklisting the module but that didn't work. when installing did it say you have scsi hdd? don't know the relevance  but i always thought mine was ide? it started to boot so i'm sure it's nothing.

---

### Post by sickofthesea on 2008-06-03
I don't know about identified as scsi but they are listed as sda1, sda2, sdb1, etc. now instead of the old hda1, hda2, hdb1. I think this is just a new way of doing things.

When I get a chance I will log this as a bug report because it means the latest Ubuntu is completely uninstallable on this series of laptops and that's a lot of laptops (probably)!

Rgds,

Martin

---

### Post by wishful9 on 2008-06-08
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720)

already reported.

i'm going to upgrade and blacklist (after it's replaced by the upgrade) b43legacy before reboot, may work may not?

Simon

---

### Post by sickofthesea on 2008-06-08
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238042](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238042)

I'm not sure if my problem is related to the broadcom chip or not. I'll try another install, boot with a knoppix disc and blacklist the bcm43xx driver and see what happens.

I'll post again when I've done that but doubt if it'll be before the weekend now.

Good luck!

Martin

---

### Post by sickofthesea on 2008-06-12
SOLVED/FIXED/YIPPEE:

I'm now typing this on my lappy with a freshly installed Xubuntu 8.04. It was the broadcom drivers. I blacklisted both the b43xx and the b43legacy and it booted straight away. clocksource=hpet did nothing.

All the times I have installed linux on this 64bit laptop, I've always installed a 32bit version because of the broadcom wireless chipset. I have never been able to get the bcm43xx drivers to work and always had to resort to ndiswrapper with 32bit Windows drivers to get it working, hence the necessity of a 32bit version of linux.

So for this latest release I purchased (beforehand) a wireless card with a gpl driver available here [http://www.thelinuxemporium.co.uk/products/wireless/#pidR26799](http://www.thelinuxemporium.co.uk/products/wireless/#pidR26799) for £10, so that I could finally have a 64bit linux installed AND have working wireless. Subsequently I then still had a problem with the broadcom drivers, this time stopping it booting!! Aaargh! How annoying are broadcom?? Thankfully the card from The Linux Emporium worked out of the box (once the machine finally booted!)

Thanks for everyones help, appreciate it.

Martin

---

### Post by wishful9 on 2008-06-17
it worked!
from gutsy upgraded and after replace blacklist prompt, i added text before upgrade so it would show up.
added the lines:
blacklist b43
blacklist ssb
blacklist b43legacy

may be over zealous with ssb but would rather get it working and then counter problems.

Simon

---

