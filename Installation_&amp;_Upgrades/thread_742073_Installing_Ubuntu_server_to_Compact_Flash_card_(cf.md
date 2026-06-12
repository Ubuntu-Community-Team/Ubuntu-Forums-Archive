---
title: "Installing Ubuntu server to Compact Flash card (cf2ide adapter)"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by archonon on 2008-04-01
I decided to install my Ubuntu home server to 4 GB compact flash card. It is connected to PATA-port via CF to IDE adapter, unfortunately Ubuntu server (nor desktop live-cd) doesn't recognize it. Bios does detect it just fine and also Knoppix.

In knoppix it is in /dev/hda1. I have also tried installing first Ubuntu to regular PATA-HDD and then clone entire disk to CF-drive with Ghost. But apparently grub have some problems with it, since at boot it just displays only GRUB with CF and hangs there. :(

Any ideas?

Thanks in advance.

---

### Post by coffee_bean on 2008-06-16
I don't mean to frustrate you, but we're on common themes here...

I've done a similar thing, using an 8GB Lexar CF disk on the primary, master IDE channel. I get a bit further - the BIOS and all OSs detect an 8GB hard disk, as expected. Ubuntu server sees it, partitions it and installs nicely.

Then, when I restart, I just get
> Grup Stage 1.5
Error 2

Frustrating!

---

