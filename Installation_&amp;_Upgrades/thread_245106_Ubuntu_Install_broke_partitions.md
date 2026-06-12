---
title: "Ubuntu Install broke partitions"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by BillyBuerger on 2006-08-27
I just decided to rebuild my file server using Xubuntu.  I have three hard drives:

1 - 18GB SCSI (boot, root and swap)
2 - 300GB IDE (data, master)
3 - 40GB IDE (more data, slave)

First, I selected manual partition as the other choices seem to pick whatever drive they want.  Didn't want to take that chance.  Then I was a little concerned as it marked my 40GB data drive as root and marked for reformatting.  I made sure I double checked that I didn't have my data partitions marked for reformatting.  Even so, I got an error message on install saying something about bad sectors not fixed on hda1.  I made a note to check for errors later.  But I was a little confused why it was even doing anything with that drive as all I needed was it to be mounted.

My troubles first started as GRUB hung up on reboot.  It just said "GRUB" and that was it.  I tried re-installing a couple times with the same results.  During one of the re-installs I noticed that my 300GB drive came up with 4 partitions on it???  I only had one big one before.  Now there was 1 280GB partition and 3 8GB partitions.  WTF???  I never told it to touch that drive!  Not to mention that the formatted capacity of the drive is about 280GB.  Add 3 8GB partitions and it's over 300GB.  That's bigger than the drive.

I think I figured out part of what went wrong and why GRUB was hanging.  It didn't ask where I wanted to load GRUB.  It should have gone on the 18GB SCSI drive as that was my boot drive.  But I think it put it on my 300GB drive as it was the primary master IDE drive.  My BIOS was set to boot from the SCSI drive only.  So it was using my old boot record on the SCSI drive and not the new one that was on my IDE drive.  I removed the SCSI drive and replaced it with an 8GB IDE as the primary master drive.  Installed and boot fine.......

But now my 300GB drive is gone.  It won't mount and seems to say that it's empty.  I'm trying out some partition recovery tools to see if it can recover the partition.  Or at least try to recover the data.  It shouldn't have reformatted anything so the data should still be on there somewhere.

In hindsight, I should have disconnected my data drives during the install and then mounted them afterwards.  It just didn't occur to me that the install would have even touched them.  Let alone break them.

Anyone know why something like this happened?  Any way to avoid it in the future?

---

