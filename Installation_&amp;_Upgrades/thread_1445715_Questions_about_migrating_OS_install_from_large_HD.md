---
title: "Questions about migrating OS install from large HD to smaller one"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by cilbuper on 2010-04-02
I need to use the drive which currently hosts an Ubuntu 9.10 server install. The Os install was the default Ubuntu partitioning.  It created sda1, sda2 and sda5, Linux, Extended and Linux/Swap partitions, respectively.  The start and end blocks for sda2 & 5 are the same.  

I am trying to figure out which method of migration would be the best.  I have used ddrescue to clone hard drives and am not sure how this would work when migrating to a smaller HD (Moving from a 74GB to a 36GB).  Would it be a good idea to shrink the partition with Gparted or something?  The OS is only about 3-4GB.

The other way I could migrate is to use the tar backup I made.  It should have everything needed as I used the notes from the Ubuntu Backup  How To page.  I just don't know how this works when installing to a new hard drive.  Would I need to create or edit the MBR of the new hard drive?  Can a tar backup capture any of the MBR info?

I guess it shouldn't make much of a difference as to which method I use so I am open to suggestions as to which to try and any suggestions as to things to make sure to do.  Much  thanks!

---

### Post by prodigy_ on 2010-04-02
You could use a tool like Acronis True Image.

---

### Post by cilbuper on 2010-04-03
> **prodigy_ said:**
> You could use a tool like Acronis True Image.

Wow, thanks for the advice.  I'll run out and buy that!  Thanks so much! Sorry for the sarcasm.  

Any suggestions with relation to the OP?

---

### Post by kennyhendrick on 2010-04-05
> **prodigy_ said:**
> You could use a tool like Acronis True Image.

Actually, and somebody correct me if I'm wrong because I'm pretty sure that I'm not, but Acronis returns a warning/error screen when attempting to clone a linux drive or partition (but not sure how the results would be for a sector by sector approach which is also offered in my version of Acronis...).

No big deal really, but for the record, the results are a non-bootable "clone" (which makes it no clone at all now does it?  

I've had great success with Acronis in windows patitions (usually using bootable media) and dd in Linux (using bootable media) but I have a similar dilemna.  I have plenty of drives here (we're a computer store in Florida) but at present I'm scouring the net for the best approach to clone my linux drive (1Tb) to a smaller drive (250GB).

The reason I want to get the TB down to a 250GB drive (clone) is that I've heard it said that if a clone is made in pata one can simply slap the drive into just about any machine without error (and I kind of like my server machine's personalization right now and wish to bring that baby up to the front office computer).

The largest pata drive I could find around here is a 250GB....

Since dd if=/dev/sda of=/dev/sdb apparently doesn't auto-adjust I've already used gparted (what a great program!) to shrink the 1st partition down to approx. 200Gb. 

Oh wait a minute....

Hmmm....I think I just talked myself into creating an iso image of sorts for this project...(ooh, light bulb!!)

Gotta go~

---

