---
title: "Ubuntu installer is not seeing my partitions at all"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by manishk on 2007-06-12
Hi,

I had a dual boot (XP and Dapper). 

Then I reinstalled XP and wanted to install Feisty over Dapper...but the installer sees my harddisk as one chunk of unallocated space!!:(

I have three partitions on my 120GB harddisk that Windows can see...1 NTFS and 2 FAT32, plus 1 ext3 and 2 gigs as linux-swap.

Any solutions?? Pls help

---

### Post by tyk on 2007-06-12
didja restart into xp after installation was complete? or didja boot up with the feisty cd immediately after?
xp requires a couple of proprietary restarts, incl the ones after driver installations. my guess is ur using a SATA hdd. so let xp completely complete its installation process. you might even want to defrag the drives once.
if this dont help, do check the feisty installation cd for defects.
cheers

---

### Post by Pumalite on 2007-06-12
> **tyk said:**
> didja restart into xp after installation was complete? or didja boot up with the feisty cd immediately after?
xp requires a couple of proprietary restarts, incl the ones after driver installations. my guess is ur using a SATA hdd. so let xp completely complete its installation process. you might even want to defrag the drives once.
if this dont help, do check the feisty installation cd for defects.
cheers

I would first pack Windblows with several defrags and erase all temp file. I would then use Gparted to do the rest of the dirty work. Then install Ubuntu.

---

### Post by manishk on 2007-06-13
> **tyk said:**
> didja restart into xp after installation was complete? or didja boot up with the feisty cd immediately after?
xp requires a couple of proprietary restarts, incl the ones after driver installations. my guess is ur using a SATA hdd. so let xp completely complete its installation process. you might even want to defrag the drives once.
if this dont help, do check the feisty installation cd for defects.
cheers

Well, XP got its necessary restarts. Even the ones after the driver installations. 

And yes, I am using a SATA HDD. Does that matter?? 

I just defraged the drives...have to check the CD yet.

BTW, Its only that the installer is not recognising the partitions...when I run the Live CD I can access all my partitions through Nautilus.

---

### Post by manishk on 2007-06-13
> **Pumalite said:**
> I would first pack Windblows..

What is Windblows?? A little more detail please

---

### Post by lemonwonder on 2007-06-13
I may be wrong but I believe its the term for windows that anti-windows people use.

WIND -- BLOWS!!

As to say: Windows blows!

HTH :)

---

### Post by tyk on 2007-06-14
> **manishk said:**
> 

BTW, Its only that the installer is not recognising the partitions...when I run the Live CD I can access all my partitions through Nautilus.

hmm.. that is strange. your partitioner on the cd could be the culprit here. do you have any other partitioning tool? like from any other distro? and can you possibly partition from the live cd? then try installation.

alldabest.

---

### Post by manishk on 2007-08-31
I'm sorry for such a late reply.

I just formatted my entire hard disk.

Now, I got the same error with one of my friends laptop. Like in the previous case I had very recently created some new partitions using GParted...I deleted those new partitions from Win's Disk Managment tool and rebooted with the Live CD and everything was fine again.

---

