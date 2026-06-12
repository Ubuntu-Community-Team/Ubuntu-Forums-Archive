---
title: "New Install, partition problem (fat32)"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by Holdstrong on 2008-03-19
1 computer, 2 SATA drives.

I have XP installed on one, I am attempting to install Ubuntu on the other.  Will use GRUB to boot.

The plan is to have a large FAT32 partition on the Ubuntu drive so that I share files back and forth.  I tried to set it up so that I would have a 20GB ext3 mounted at /. 3GB swap, and about 200+GB for the FAT32 mounted at /data.

Here is the summary that is displayed toward the end of setup:

The following partitions are going to be formatted:
 partition #1 of SCSI2 (0,0,0) (sda) as ext3
 partition #2 of SCSI2 (0,0,0) (sda) as swap
 partition #3 of SCSI2 (0,0,0) (sda) as fat32


And here is the error message I get when it runs:

The attempt to mount a file system with type vfat in SCSI2 (0,0,0), partition #3 (sda) at /data failed.

You may resume partitioning from the partitioning menu.


Ideas?

ps:  As an aside, I have been pretty surprised at how little basic information is easily available for Ubuntu installations.  It took me several nights and lots of forum searching just to find installation partition examples, advice and best practices.  This is pretty basic information, ie:  how big should your swap be, and it isn't nearly as easy to find as it should be.

---

### Post by Pumalite on 2008-03-19
1 GB of /swap is enough. As for the fat32 partition; you don't need it. It's an obsolete format. Choose ntfs, which can be read and written to from Ubuntu or ext3, which can be dealt with with a special driver from Windows.

---

### Post by Holdstrong on 2008-03-19
Thanks for the reply.

I don't seem to recall seeing an option to format as ntfs from within the Ubuntu installer.  I saw ext2, ext3, swap, fat16, fat32, and some others... including, donotuse.  But I didn't see an NTFS option.

Also, during my hours of searching for this information over the past couple of nights I found lots of posts stating NTFS support was flakey and could cause problems.  Is this no longer the case?

And by driver, do you mean a driver for windows to allow it to use the NTFS partition on the Ubuntu disk?

---

### Post by Pumalite on 2008-03-19
The driver for Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
But ntfs-3g in Ubuntu works great. (for ntfs)
I'm not a Windows user and have been many a moons since I formatted ntfs. Maybe you could do it from your XP. I don't know. If I were you I'd use ext3.

---

### Post by Holdstrong on 2008-03-19
Hmmm, interesting.  Something to play with another time.

But I think for now I would rather keep this as simple as possible (without having to play with drivers or third party programs).

All I need is to be able to partition part of this Linux drive in such a way that XP can read and write to it natively.  Quite literally, I just want a place to be able to share a few documents back and forth between the two OS's

---

### Post by Pumalite on 2008-03-19
Godspeed.

---

### Post by Holdstrong on 2008-03-19
Well....  I was able to do what I was trying to on a smaller HD (40 GB).  Maybe there is a VFAT partion size limitation?  Beats me.

The only way I could get this to work on a 200+ GB drive is by installing Linux using 2 partitions.  An ext3 root partition and a swap partition.  Then the empty space had to be formatted NTFS in XP.  NTFS was not an option in the Ubuntu installer.

This method does cause some funkiness.  If I create a *.txt doc in the ntfs share in XP it shows up in Ubuntu fine, but if I then alter it in Ubuntu... the alteration shows up in XP, but it comes with a shadow file of some type.

Dunno.  I hate to say it but the last time I tried to play around with Linux was 5 years ago (Red Hat) and once again I've gained a whole new appreciation for Windows and the support information available to it.

---

### Post by Pumalite on 2008-03-19
Every new OS has a learning curve. It cannot be learnt overnight. Here are some links to help you:
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

### Post by Holdstrong on 2008-03-19
I appreciate the links and the help.  I really do.

I installed Vista and Mac OS for the first time last week... I had never touched a Mac before, and it was my first run at Vista.  I didn't have to spend 2 nights looking for answers and eventually register on a forum and ask a question about a very simple, very basic installation problem.

I'm just not sure this is a learning curve problem so much as it is an information gap and communication problem.  I'm willing to learn something new, I'm not willing to chase my tail  to do so.

Thanks again for the help and the tip about formatting from XP - and for putting up with my rant.  ;)

---

