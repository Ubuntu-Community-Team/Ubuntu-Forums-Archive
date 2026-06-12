---
title: "AlternateCD: Failure when installing the base system (please insert the disc labeled)"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by guarriman on 2009-03-01
Hi.

I'm trying to install Ubuntu 9.04-Alpha 5 (Alternate Install CD) on my PC:

************
AMD Semprom 3300+ 2.01 GHz
448 Mb of RAM
100 GB of disk space
************

I set up the partitions, it looks like working ok, but when installing the base system, I find this message:

********
Please insert the disc labeled 'Ubuntu 9.04 _Jaunty Jackalope_ Alpha i386 (20090227)'
********

Which CD is that? Is it not supposed that the alternate CD is the only CD I need?

Any help will be welcome. Thank you very much.

---

### Post by bapoumba on 2009-03-01
Moved to Jaunty.

---

### Post by Gina on 2009-03-01
I've had this problem in the past but A5 seems OK - I'm installing it on my old AMD K6-2 at this very moment and it's nearly finished.

Did you run the media test before running the install?  It could be a faulty CD or the CD drive.  Optical media are notoriously unreliable.

---

### Post by Sand &amp; Mercury on 2009-03-01
It really does sound like a bum CD. I've had this happen before too. Burned the image again and it worked fine.

---

### Post by guarriman on 2009-03-08
I burned the ISO twice, and checked the CD twice. But I got this error message twice:

*******
The './pool/main/x/xsane/xsane-common_0.996-1ubuntu2_all.deb' file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted
*******

Am I the first person using "Ubuntu 9.04-Alpha 5 (Alternate Install CD)"?

---

### Post by curtis on 2009-03-08
Maybe your download is corrupt?

Check the MD5 of the iso.

---

### Post by lemsx1 on 2009-04-19
Great to see that nobody bother to actually answer this question.

I downloaded 9.04 RC (today) and burned it correctly (at 1/2 the speed of my drive). Then I did the "Check disc" routine after booting from the disc. Just to make double sure that everything was fine.

Partition my disk the right way. And I get the dreaded: 

*Please insert the disc labeled: 'Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414.1)' in the drive '/cdrom/' and press enter.*

Now this is just what I needed...

Going to tty2 (CTRL+Alt+F2) shows that /cdrom has the right stuff. /target/cdrom points to media/cdrom which in turn points to cdrom0 (yes, all relative to /target).

I set the /target/cdrom symlink to /target/media/cdrom0 like:
cd /target
rm cdrom
ln -s /target/media/cdrom0 cdrom

Then go back to tty1 (CTRL+Alt+F1) and click "continue". I get an error saying that the "Install base system" step failed and I go back to tty2 (CTRL+Alt+F2), put the symlink back for /target/cdrom:

cd /target
rm cdrom
ln -s media/cdrom cdrom

And after this the Install Base System worked and the processed continued.

This is not good -- at least it worked.

---

