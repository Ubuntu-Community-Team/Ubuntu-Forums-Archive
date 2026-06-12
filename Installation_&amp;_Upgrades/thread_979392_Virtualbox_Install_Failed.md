---
title: "Virtualbox Install Failed"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2008-11-11
I just downloaded the Virtualbox .deb from Sun for 8.10 AMD64 (I assume this is the 64-bit version even though I'm running on Intel), however the package installer gives me the following error:  "Error:  conflicts with the installed package 'virtualbox-ose'.

I have not downloaded or installed virtualbox before.  Does it now come with Ubuntu?  What do I do to fix this?
Download/

---

### Post by sirebral on 2008-11-11
You downloaded the 64 bit version.  Are you running a 64 bit OS?  If not then you need the x86 version.

---

### Post by HDTimeshifter on 2008-11-12
Yes, 64-bit Ubuntu.  That's why I downloaded the 64-bit version.

It's rather confusing why they name all the 64-bit software AMD when we are looking for 64-bit software that should run on Intel as well.

I opened Synaptic Package Manager and removed all Virtualbox OSE components, then reinstalled the .deb from the other package manager and it seemed to install ok.  I have no idea where the Virtualbox OSE came from, unless it's now bundled with Ubuntu 8.10.  I want USB support in Sun's .deb, and not the OSE version.

I can't get the floppy drive to mount.  After checking the Mount Floppy Drive box, nothing shows up in the drop-down box.  I need to boot from floppy since my XP CD is not bootable...

---

