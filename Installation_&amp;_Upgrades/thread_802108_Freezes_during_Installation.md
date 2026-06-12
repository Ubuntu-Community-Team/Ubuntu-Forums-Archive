---
title: "Freezes during Installation"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by somody on 2008-05-21
Hey guys.

I'm having a bit of a problem.  I used to use Ubuntu, until I got a new computer a while ago, and I just didn't re-install.  But now I've decided to use it again, do I downloaded the newest ISO, and started installing.  One thing I should probably mention is that I had no unpartitioned space on my hard drive, so I used Norton PartitionMagic to shrink a partion so I have some free space.  I selected the option to use the largest continuous free space in the Ubuntu Partitioner, and it did its business.  However, while installing, once it gets to the end of "Copying files..." and changes to "Configuring system locale...", my system freezes, and random pixels on my monitor start turning green.  My friend suggested that I use the "alternate" ISO, with the text-based installer, but I have the same problem.  What is going on?

---

### Post by wpshooter on 2008-05-21
Have you tried installing in safe graphics mode ?

---

### Post by somody on 2008-05-21
> **wpshooter said:**
> Have you tried installing in safe graphics mode ?
Nope, how do I do that?

---

### Post by wpshooter on 2008-05-21
It should be one of the menu choices on the initial Ubuntu boot screen menu.

Also, have you checked the integrity of your Ubuntu CD by running the verification function, also found on the initial Ubuntu boot screen menu ?

---

### Post by somody on 2008-05-21
> **wpshooter said:**
> It should be one of the menu choices on the initial Ubuntu boot screen menu.

Also, have you checked the integrity of your Ubuntu CD by running the verification function, also found on the initial Ubuntu boot screen menu ?
Yes, I checked the integrity of the CD, and everything was OK, but it still wouldn't install.  I tried the "alternate" CD again, but with the "xmodule=vesa" option, and I think it installed properly.  But I don't have the ubuntu-desktop package installed, and when I apt-get it, it asks for the CD.  How can I make it use the Internet?

---

### Post by wpshooter on 2008-05-21
Go into software sources and uncheck the Ubuntu CD listing.

---

### Post by somody on 2008-05-21
> **wpshooter said:**
> Go into software sources and uncheck the Ubuntu CD listing.
Well, how can I do that from just a command line?

---

### Post by dstew on 2008-05-21
> Well, how can I do that from just a command line?```
sudo nano /etc/apt/sources.list
```Find the line for the CD-ROM, and comment it out by putting a # at the front. Save the file with ctrl-X, hit return.

---

### Post by somody on 2008-05-24
For reference's sake, I'll post what's happening to me.  I managed to finish the base install from the alternate CD.  Then, I booted into the shell and used apt-get from the normal CD to get ubuntu-desktop.  There were many errors, so I had to use "dpkg --configure -a --force-all" a lot.  Once it was finally fixed, I'm having these problems: [http://ubuntuforums.org/showthread.php?p=5017016]("http://ubuntuforums.org/showthread.php?p=5017016").

---

### Post by somody on 2008-06-20
I was having the same problem with all non-XP operating systems.  My problem has been solved through experimentation.  The culprit is AMD Live and AMD Virtualization!  Disable both!

---

