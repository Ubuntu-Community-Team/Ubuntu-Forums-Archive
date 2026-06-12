---
title: "/var out of space"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by Thulemanden on 2005-09-07
Gave Ubuntu a fair chance, but during installation it failed.

Ubuntu reported /var was out of space. Now, I have a 30GB harddisk and Ubuntu was supposed to wipe it out and conquer the disk.

So why did Ubuntu fail, and how can it be installed?

---

### Post by jabb0 on 2005-09-07
did you compare the checksum on your download.

I didnt have to do this, but i gues that was just lucky.
From what i can gather you should check that first, it will tell you if you have got a dud download.

---

### Post by Thulemanden on 2005-09-07
[QUOTE=jabb0]did you compare the checksum on your download.

I didnt have to do this, but i gues that was just lucky.
From what i can gather you should check that first, it will tell you if you have got a dud download.[/QUOTE]

I guess I can await for the cd-discs I ordered a few days ago.

---

### Post by Thulemanden on 2005-09-12
2nd try, this time kUbuntu.

That means a new download and a new burning of the ISO.

However I got the same error /var out of space. This time I rebooted with the cd in place and booted to the hard disk. Somehow kUbuntu resumed installing packages and did this  to the bitter end.

Rebooting and everything was fine. This is a 30GB disk, so there was plenty of space for Ubuntu to grab some /var.

Weird, not?   ](*,)

---

### Post by skoal on 2005-09-12
Post back here the exact *partitioning* scheme you are using.  Hard to tell what you are doing with that 30 gig'er unless you provide concrete numbers from fdisk, live CD parted, rough general partition estimates, or whatever...

hda1 - fat32 (5 GB)
hda2 - /boot (100MB)
hda3 - swap (512MB)
hda4...

...you get the idea.  Throw us a bone here, something to actually chew on.

\\//_

---

### Post by Thulemanden on 2005-09-12
It was installed to the 13GB slave hd, MEPIS is hidden on the master, but not in Grub.

qtparted says this for Slave/kUbuntu Hoary:

hdb1 ex3 12.04GB
hdb2 extended 556.94mb
hdb3 swap 556.91mb

---

### Post by skoal on 2005-09-12
Alright, sir.  Now we're cooking with gas...

But, how did we get from 30 gig's to 13 now (and it's a slave, hard drive b)?  I'm getting lost.  

1. If you go through the installation, you should eventually be prompted to remove the CD and reboot, right?  Do you even get that far? 

2. If we have two drives now, can you please provide the mount points and partition scheme for both drives?  

Best guess : It's quite possible you might be mounting a /var partition that Mepis set up on hda (during the Ubuntu install).  It's hard to tell since you didn't provide that info (partitions & mount points for each drive)...

\\//_

---

