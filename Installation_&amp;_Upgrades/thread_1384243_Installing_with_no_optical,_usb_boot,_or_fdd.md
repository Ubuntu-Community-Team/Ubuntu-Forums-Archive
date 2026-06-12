---
title: "Installing with no optical, usb boot, or fdd"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by mr_arc on 2010-01-18
Hi all

I have a Dell Lattitude LS. It gets used for very light web browsing, RDP into my main PC and also to access Megasquirt in my car.

It had until recently a stripped out XP install there that ran ok despite the laptop being a P3 500, 256mb RAM.

That install is now damaged, it gets as far as the login screen and then hangs. Instead of repairing it, i want to put ubuntu on there as i think it'll manage the (lack of) resources better.

However, the laptop has no optical drive, cannot boot from USB and i'm not sure if the external FDD i have for it works either (it's a bit crusty).

I do have a pata > usb convertor to access the drive via my main PC though. 

Am just not sure what I can put on there to let me boot and then install.

Is it plausible to make the HDD act like a LiveCD?

Should I partition it, and copy the install ISO contents into one of the partitions, and go from there - but how do i make that bootable?

I do have another laptop with a PATA HDD that does have a working optical drive. Could I begin the install on that, then pull the drive and swap it over at some point during the install - or is that a no go?

---

### Post by John Bean on 2010-01-18
> **mr_arc said:**
> I do have another laptop with a PATA HDD that does have a working optical drive. Could I begin the install on that, then pull the drive and swap it over at some point during the install - or is that a no go?

I'd do a full install before swapping. There's a reasonably good probability that it will boot just fine and adapt to the new hardware, and assuming it can obtain network connectivity it can then be updated as appropriate.

---

### Post by mr_arc on 2010-01-18
Ok, I'll give that a go first. If there is any issue with the onboard wired LAN, I'll bung a WiFi card in that I know plays nice.

---

### Post by mr_arc on 2010-01-18
hmm seems the spare laptop doesnt even have enough ram to boot the installer

---

