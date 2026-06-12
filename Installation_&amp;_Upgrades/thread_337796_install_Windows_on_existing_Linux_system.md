---
title: "install Windows on existing Linux system"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Brian Boyko on 2007-01-13
If I had to, I could reformat my entire hard drive, but I'd rather not. 

I have an Ubuntu 6.10 Edgy install, taking up my entire 250 G hard drive

I would like to 

A) Non-destructively repartition the hard drive.
B) Install Windows to have a dual boot system.

Additionally all my data IS backed up so I can reformat the entire drive.  I'm looking for a solution that is simpler than reinstalling and reconfiguring all of Linux to do so (I've got Beryl on here, my printer was a pain to set up, etc, etc.)

---

### Post by sn0m on 2007-01-13
Hi 
I am quite interested at the above issue. I have dual boot already but made the mistake of giving too much of space to windows and kinda of running out on ubuntu. I would like to reinstall windows on a much smaller space and on fat 32 file system, sincwe i can write from ubuntu on it. I was just wandering that if i install win xp, will it change the boot ladder and will i not be able to find ubuntu anymore, as i know this dodgy windows has some dirty tricks up the sleeve.
thnaks
koli

---

### Post by raul_ on 2007-01-13
> **sn0m said:**
> Hi 
I am quite interested at the above issue. I have dual boot already but made the mistake of giving too much of space to windows and kinda of running out on ubuntu. I would like to reinstall windows on a much smaller space and on fat 32 file system, sincwe i can write from ubuntu on it. I was just wandering that if i install win xp, will it change the boot ladder and will i not be able to find ubuntu anymore, as i know this dodgy windows has some dirty tricks up the sleeve.
thnaks
koli

You have other ways of doing that:

See the how-to's on writing to NTFS systems
Use GParted to resize the partitions you want (you have to run it from the Live CD

---

### Post by raul_ on 2007-01-13
> **Brian Boyko said:**
> If I had to, I could reformat my entire hard drive, but I'd rather not. 

I have an Ubuntu 6.10 Edgy install, taking up my entire 250 G hard drive

I would like to 

A) Non-destructively repartition the hard drive.
B) Install Windows to have a dual boot system.

Additionally all my data IS backed up so I can reformat the entire drive.  I'm looking for a solution that is simpler than reinstalling and reconfiguring all of Linux to do so (I've got Beryl on here, my printer was a pain to set up, etc, etc.)

again, i think you can create another partition with GParted (you have to run it from the Live CD), install windows in the new partition, and then reinstall GRUB 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Post if you have any doubts

---

### Post by louieb on 2007-01-13
In the How To section of this forum there are a couple of threads  on backup and restore. I was having hard disk problems on one PC. I found it easy enough to backup to an external USB drive, reformat my hard drive and restore Ubuntu to exactly the way it was before.

---

### Post by Brian Boyko on 2007-01-13
> **raul_ said:**
> again, i think you can create another partition with GParted (you have to run it from the Live CD), install windows in the new partition, and then reinstall GRUB 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Post if you have any doubts

Will GParted non-destructively repartion?  And if so, will XP install in a partition that is not the first one on the drive?

---

### Post by raul_ on 2007-01-13
About GParted, yes
About Windows, i really don't know because i never installed windows since i have Ubuntu =\ you'll have to do a little searching but i think Windows will respect your drive's partitioning. the only "destruction" it does is writing over the grub loader, so you'll have to reinstall it

---

