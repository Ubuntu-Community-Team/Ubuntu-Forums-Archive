---
title: "Linux on a WYSE V10L Client?"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by Chris Grk-O-Matic on 2010-01-05
So we have a bunch of these WYSE's sitting around [doing nothing] at work and suffice to say, my boredom leads to an insatiable curiosity.
 
I'm wondering if I can run Linux on it off a bootable USB hard or flash drive. Anyone ever try this?
 
 
Chris

---

### Post by huba! on 2010-01-16
Yes, it is possible, I just tried it myself. While the "Wyse"-Logog is displayed after power-on. press DEL and you will see that the V10L has a standard PC-BIOS. It will prompt you for a password, the standard password if it was not changed is "Fireport". Them, you can select "USB-ZIP" as the first boot device, just as you would on a full-sized PC.
Hope I could help!

---

### Post by Chris Grk-O-Matic on 2010-01-18
That's cool. Boredom-B-Gone!

---

### Post by suprphrk on 2010-05-17
I've been trying about every LiveCD I could find for Ubuntu, LUbuntu, KBuntu, etc.  I can't get any of these to boot completely into a working OS.  Can you tell me what flavor of Linux you got on the V10L and a short how-you-did-it or link?  

I've been trying for a few days now, and I just keep getting to the same point of booting and it stops.  It sticks at one screen (forget what it says right now) but all of my searches point to bad memory.  I figured it's because it's using a low amount from the V10L and then trying to use the thumb drive, so it's probably not an invalid error.  Plus, I get it with a couple distros.

Any insight?  Instructions?  Wanna do it for me?  ;)  I'm about to try gOS next, it looks like my Mac so maybe it'll be dumbed down... er... easy enough... for me to get through it.

Thanks in advance.

---

### Post by g0llem on 2010-09-08
Hi,

Did you succeed in flashing the Wyse VL10 with ubuntu?
We have some VL10 clients here and I would like to use them as linux machines. If linux is able to function on these thin clients I can use them for Xibo, an open source project for narrow casting. We are deploying it on windows clients now but these VL10 would be a better solution. :)

---

### Post by lrgmmc on 2010-12-15
have you considered ltsp? the V10L has pxe boot option right? might be a thought.

---

### Post by Chris Grk-O-Matic on 2011-02-23
I was able to successfully boot [on a thumbdrive] Puppy Linux, NetBuntu, and MythTV on the V10L. Nifty little thing it is. Puppy is perfect for it. However Myth works but the video stutters. The V10L has an 800Mhz processor, but perhaps not enough power on the video end to drive the video content. I'm wondering if the 128MBit (?) flash memory, which I looked and looked to see if it was modular, is the culprit because streaming TV seemed like it was writed to the thumbdrive as indicated by the flashing LED.
 
I would like to see if I can netboot it.
 
For install, I had to upgrade the RAM to 1Ghz. Then change the boot order so that it recognizes the thumbdrive first.

---

### Post by BrainDeid on 2011-06-06
I tried this on the C10 (V10 with no parallel port) and have TinyCore runing from the onboard 128meg flash disk.

I also had ChromeOS running albeit from an external drive.
TinyCore works great.

---

### Post by lrgmmc on 2011-06-06
i was looking around but couldn't find any info. But was curious if the broadcom crystalclear mini-pci would help for the video stuter. again i cant remember if this unit has a mini-pci slot.

---

### Post by thesraid on 2012-01-04
@BrainDeid How did you get Linux "running from the onboard 128meg flash disk". I have puppy Linux running from a USB disk but I was hoping to use the flash not as a place to store the OS but as swap. Does anybody know if this is possible?

---

### Post by BrainDeid on 2012-01-05
I set the PXE boot option to the last boot device, USB CDrom to first boot device and the on-board flash (it's in an ATA port) to the second last boot device.

Booted the box from a live cd, blew away the original partition and created a new one occupying the whole flash then rebooted with the TinyCore installation CD and installed using their instructions repartitioning etc again.

In the case of the C10 / V10 the internal flash is merely an PATA drive.

I do have problems getting wireless to work though, such is life :(

---

