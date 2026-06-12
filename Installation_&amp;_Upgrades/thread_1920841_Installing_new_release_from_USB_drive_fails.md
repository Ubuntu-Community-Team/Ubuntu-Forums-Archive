---
title: "Installing new release from USB drive fails"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by quadproc on 2012-02-05
To install a new release, I downloaded the release to my first hard disk, made a USB drive of the .iso file using the startup disk creator and md5summed it.  Before installing it, I tried it out and everything seemed to work OK.  When I tried to install it, I got an error message relating to partitioning (I had prepartitioned the disk to make a new partition for this install).  After telling the installer to ignore this error I received a new error regarding timezone.  Skipping that error was futile - I was stuck in a loop of errors.

It appears that installing from the USB drive does not work even though running from it does.

The system here is (briefly) 4 SATA drives, 6 GB RAM, ASUS P6T SE motherboard, lots of older releases installed and working OK.

Does anyone know what is going on? How to work around the errors?  Thanks.

quadproc

---

### Post by Paddy Landau on 2012-02-06
It may help if you told us the specific error regarding the partition.

Some people find errors with a Live USB, so try burning to CD in case that helps.

EDIT: What version of Ubuntu did you download?

---

### Post by quadproc on 2012-02-06
Sorry, I don't remember the error numbers that I saw and I did not write them down.  I have seen this same problem for at least a year and I have seen it on both Ubuntu 10.10 and Mint Linux 12.

This problem is apparently not related to partitioning - the Ubuntu installer is apparently deciding which installation method to use ("alongside", "use entire disk", etc>) when the first error is reported.  I don't really care that the partitioner doesn't work because I had previously created a partition for the new installation and I was going to use the "advanced" option.  But when the partitioner doesn't work then the error from it seems to throw a wrench into the works.

I was planning to evaluate several distributions and I thought that I could avoid the long times and waste of material resulting from making CDs.  All of the CDs that I have tried worked fine for doing installations.

quadproc

---

### Post by Paddy Landau on 2012-02-07
> **quadproc said:**
> I was planning to evaluate several distributions and I thought that I could avoid the long times and waste of material resulting from making CDs.  All of the CDs that I have tried worked fine for doing installations.
It sounds to me that you may have a problem relating to how your computer reads USB's. I have not come across your problem before.

To try to resolve this, we really need to know exactly what is going on -- the steps taken just before the error, and the specific error. Unfortunately, the vague description you have given could be anything from a hardware failure to user error to an undiscovered bug.

---

### Post by quadproc on 2012-02-07
I believe that I have determined where the problem is even though I do not know why it exists.

I repeated the experiment of copying the .iso file to a USB flash drive with one change: I used a different USB flash drive (different both in manufacturer and in size).  This time, the subsequent installation worked.

The drive that worked is a Kingston drive.  I have never used that brand before.

The drives that do not work are SanDisk.  Yes, more than one of them had the same problem.  Even though the .iso file's md5sum checked out OK on the flash drive, it still would not work correctly and the installation software would report errors related to tasks such as setting the time zone and setting up the partition editor.  Because a program such as md5sum works by reading the memory's data sequentially, but in normal operation the computer reads instructions non-sequentially at least some of the time, and the computer alternates between data and instructions, I suspect that the defective flash drives are getting confused by the non-sequential access.

I suspect that additionally the error handling software in the installation process is somewhat deficient.  It would have been useful for the computer to report what it was trying to do when it did not succeed.  But, since errors of this sort are very hard to induce for testing, such errors probably were not well tested.

In any event I am now running an OS that was copied from a downloaded disk file to a USB flash drive with that flash drive subsequently used to do an installation of the OS back onto the hard disk.

Thanks for your patience.

quadproc

---

### Post by Paddy Landau on 2012-02-08
I'm glad you have it solved. It is curious that one make of USB drive works, while another one does not.

---

