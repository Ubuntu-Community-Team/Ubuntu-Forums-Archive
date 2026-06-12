---
title: "Fresh install without USB or CD?"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by dabbi2000 on 2010-10-05
I have a >5 year old laptop, running Maverick (Ubuntu 10.10) but I need to do a clean install since the video driver is all screwed.

The laptop is without USB boot option in BIOS. The CD drive is physically removed.

The HD partitions are
/dev/sda1 (ext4) 15gb mounted as /
/dev/sda2 (extended)
 /dev/sda5 (linux-swap) 2gb
 /deb/sda6 (ext4) 20gb mounted as /home


How can I do a fresh install??

---

### Post by coffeecat on 2010-10-05
> **dabbi2000 said:**
> How can I do a fresh install??

With some difficulty.

The only thing I can think of is to take the hard drive out and use another machine to do a fresh install onto it. The hardware difference won't matter because Linux probes for hardware on bootup, but there are one or two technical challenges.

With a >5 year old laptop that's probably going to be an older ide PATA drive. Which would mean that you would have to 

1 Put the drive in a 2.5 inch enclosure with a PATA connector. Or -
2 Use another older laptop. Or -
3 Use a desktop with a 2.5 to 3.5 inch PATA caddy converter.

You'd also have to ensure that grub got installed to the mbr of the removed drive rather than the main drive of the machine you were using.

Interesting project. Perhaps someone else has a better idea.

---

