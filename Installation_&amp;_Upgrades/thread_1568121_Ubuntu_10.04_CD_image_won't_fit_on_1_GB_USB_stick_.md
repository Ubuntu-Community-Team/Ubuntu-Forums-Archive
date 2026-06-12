---
title: "Ubuntu 10.04 CD image won't fit on 1 GB USB stick (?!)"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Objekt on 2010-09-04
I'm trying to use Unetbootin to create a bootable USB stick so I can install Ubuntu 10.04 on my netbook.  I have a CD image for the standard Ubuntu 10.04 desktop install cd (ubuntu-10.04-desktop-i386.iso).  It's only 699 MB, so it certainly should fit on a 1 GB USB stick but...Unetbootin keeps getting partway through making the bootable USB stick, then stops with an error message similar to this:

```
The directory /media/88A1-8221 is out of space. Press 'Yes' to abort installation, 'No' to ignore this error and attempt to continue installation, and 'No to All' to ignore all out-of-space errors.
```

It's impossible for the USB stick to be out of space.  The install CD is only 699 MB, so there is no possible way that the 1 GB (931.5 MB usable) USB stick could be full.  I formatted the USB stick (FAT32) beforehand to be sure there wasn't anything taking up space.  And I got that error message within seconds of starting, before Unetbootin had a chance to copy even a few files.

What's going on here?

Just in case it matters: I'm running Unetbootin (no idea what version, there's no way to tell) under Ubuntu Netbook Remix 9.10.

---

### Post by Rasa1111 on 2010-09-04
I thought one wanted at least 4GB to run liveUSB?
Preferably an 8GB.

The OS itself has to fit on the drive,
not just the iso image. 

please someone, correct me if im wrong.

---

### Post by oldfred on 2010-09-04
No the unetbootin should fit on a 1GB flash.

Only if you want a full install do you need 8GB or more. Tight fit into 4GB for full install.

If you look at the flash drive with disk utility or gparted does it show a full 1GB?

---

### Post by Rasa1111 on 2010-09-04
ahh, ok. Thanks. 

 Sometimes I find that my flash drives will show as "full" when Ive deleted alot from them. 
 I have to hit ctrl H to show hidden files, then delete the ".trash" file. 

Maybe that will work?

---

### Post by Objekt on 2010-09-04
> **oldfred said:**
> No the unetbootin should fit on a 1GB flash.

Only if you want a full install do you need 8GB or more. Tight fit into 4GB for full install.

If you look at the flash drive with disk utility or gparted does it show a full 1GB?

Yes, the full 1 GB, or 963.61 MB usable.

There aren't any hidden files, because I started by formatting the USB stick.  I checked anyway, nope, no hidden files.

I'm not trying to install Ubunu 10.04 on the USB stick.  It's not big enough, and would be horribly slow anyway.  I'm only trying to put the contents of the Ubuntu 10.04 install CD image on the stick, effectively making it an install "CD" but without wasting a CD-R.  I've done this many times with previous versions of Ubuntu, with no problems.

---

### Post by Objekt on 2010-09-05
I think the problem is that the 1 GB USB stick is broken.  I messed with it some more this morning, and couldn't get it to format.  Gparted kept locking up when I tried to unmount the stick for formatting, and I wasn't able to write any files to it while it was mounted.  I had to log out and back in to get Gparted to work again.  General shenanigans, in other words.

I reformatted the 8 GB micro SDHC card & got the Ubuntu 10.04 install CD  put on it without any problems.  I haven't tried booting from it yet, but I'm pretty sure it's going to work.  

Consider this one "solved."  Looks like it's time to throw out that 1 GB stick.

---

