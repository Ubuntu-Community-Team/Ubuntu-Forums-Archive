---
title: "Brand New HDD, can't Install Ubuntu - Desperate for help"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Kollateral on 2010-01-07
Um... hello. n_n

I am hoping someone, *anyone*, can help me. As I've been trying to get a desktop PC to work for... months now. It was intended to work for christmas, as a gift, but it didn't go as planned.

First, back in November, I bought a t770.uk HP desktop PC, which came without a Hard drive as the perviosu owner had removed it for security reasons. A week later I got ahold of a _brand new_ - out of an anti-static sealed bag - compatable Western Digital Caviar SE 80GB SATA150 7200 HDD, and installed it as directed by my t770.uk manual. Up until now, things looked to be on a roll.

Now... as I don't have any windows OS, I figured Ubunutu would be the way to go (and it certainly is from what I've heard and read about it. I can't wait!), so I sent off for a CD and it popped through my mail a few weeks back. The problem that I am having - and I'm no expert, I'm new to this... so please bare with me if I miss an important detail - is after booting past a very breif view of the HP POST screen, the screen goes black with the error "Disc boot failure-insert system disk and press enter". I've tried placing the Ubuntu disc in (assuming it is asking for that? An OS disc) and restarting, and changing the boot order around, but no matter what I do the error persists and I can't install Ubuntu.

I don't know what steps I am supposed to take next, or what's happened...

Please help... I really want to get this PC running with Ubuntu. :confused:

---

### Post by drs305 on 2010-01-07
Kollateral, 

Welcome to Ubuntu and the Ubuntu forums. Hopefully we can get you up and running Ubuntu so you can experience the benefits of this OS.

It sounds like you have already tried it, but normally I would suggest you go into BIOS and make sure the "boot to CD" is the first option in the boot order. If you have done that, also make sure that the CD-ROM is recognized by the BIOS. If either of those things aren't set correctly you would get the results you are experiencing.

Can you try the CD in another machine? If the CD came from Canonical it should obviously be good, but perhaps it was scratched or somehow otherwise made unusable.

---

### Post by oldfred on 2010-01-07
We have seen where raid settings can cause problems. Either a hard drive that was raid before (you said yours was new?) or default raid settings in BIOS. 

Also other BIOS settings seem to be important. Several have reported similar cases as yours where other systems installed just fine, but it turned out the BIOS settings were not correct. Karmic seems to be more aware of BIOS and then does not work. One specific example was a poster who said the hard drive was not "turned on" in BIOS. I would review all the default settings in BIOS and see if any seem wrong or make a difference.

---

### Post by Kollateral on 2010-01-12
Ok, yes... I understand where your both coming from about the BIOS settings probably not being correct now since the new hard drive has been fitted (yes, it is a completely new one, never used before), but as I have no idea what I am looking for outside of changing the boot order, could you break it down into a few easy steps if possible?

---

### Post by oldfred on 2010-01-12
You should be just able to install from the CD. If you want to partition in advance:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Lundis500 on 2010-01-12
Kollateral, did you manage to change the boot order? It seems like it's the first thing you must do before you can proceed.
I think HP uses F10 to let you enter the BIOS, hard to explain what you should do there since it can differ so much.

You might also be able to press F9 for a temporary boot device, and then select cd-rom.

---

### Post by dzon65 on 2010-01-12
Had he same problem with a compaq.Although boot order was set to cd-rom first,saved as such (make sure you save those settings) it wouldn't boot.I was lucky I could find BIOS upgrades on their site.Did them and sure enough,it did.

---

### Post by recluce on 2010-01-12
Did you try to boot any other bootable CD? (to verify that your drive is not having trouble with the Ubuntu media) Borrow a Windows CD, Universal Boot CD, Knoppix CD or something like that.

Could you replace your computer's CD drive temporarily (by borrowing a CD drive from somebody)? The problem might be as simple as a broken CD drive. If your computer cannot boot from the CD (broken drive, broken CD) it would try to boot the hard drive next - and thus run into the "no system disk" issue.

---

### Post by Kollateral on 2010-01-13
Okay, no matter which way the boot order is flipped around ont he BIOS, none seem to have an effect.

I've tested the CD drives, one being a duel DVD Writer & CD-writer, and the other a DVD ROM. Both appear to work just fine? We have checked the ribbons and connectors etc, and all appear to be secure and in not loose fitting.

Any other suggestions?

---

### Post by darkod on 2010-01-13
> **Kollateral said:**
> Okay, no matter which way the boot order is flipped around ont he BIOS, none seem to have an effect.

I've tested the CD drives, one being a duel DVD Writer & CD-writer, and the other a DVD ROM. Both appear to work just fine? We have checked the ribbons and connectors etc, and all appear to be secure and in not loose fitting.

Any other suggestions?

Do you have usb stick you can use to boot from usb? Any fairly recent board should support it.

---

### Post by Kollateral on 2010-01-21
I do, but it appears to fail to recognise it?

Also, I am curious...

When I purchased my HDD as new, was there supposed to be a Disc with it? Containing drivers and whatnot to get the HDD started?

And, if I can't fix this myself (looks doubtful)... would it be worth simply taking it to my local PC World etc to have them take a look at it and hopefully fix the problem? It may cost, but I may get a PC out of it that works.

---

