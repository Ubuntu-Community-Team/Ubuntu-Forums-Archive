---
title: "Can't install windows 7"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by DerektheRed on 2010-01-22
So I installed ubuntu because my computer was doing really poorly under vista after about 9 months of use. ubuntu is cool and all, and it was good to have a computer that actually worked until I could afford windows 7, but now when I put the windows disc in it says 'error, cannot find autorun program.' I searched and people said that I could put the disc in and reboot, but my computer just ignores the disc and loads ubuntu. I have wine installed. What's wrong and why can't I install windows 7?

---

### Post by Mark Phelps on 2010-01-22
You can't use Wine to install Windows -- if that's what you're trying to do.

You will have to repartition your drive to make room for an NTFS partition for Win7.  It can't read the Linux partitions, so it can't shrink them on its own.

You do that by booting from a LiveCD, running the Partition Editor, and shrinking your Ubuntu partition.

You need to change the BIOS setting in your machine to boot from CD before it boots from the hard drive.

Also, when you boot from a CD, there's typically a message about pressing a key.  If you miss that, it will skip the CD boot and go straight to the hard drive.

---

