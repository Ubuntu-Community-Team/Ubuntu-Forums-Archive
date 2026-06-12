---
title: "Best way to backup Disk image and restore?"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by sam_i on 2007-02-28
Hi all,

As a fairly new person to Linux (a few months on now) im still buggering up the OS. As im about to do a major task which is likely to kill it, i would like to take a nice disk image back up for reassurance.

As i have been a good boy, i have got multiple partitions so i only really need to backup the main install partition of ubuntu, and possibly a few others. Most of these are on a reiser format (i have millions, literally, of small files :))

So is there a straight tool to do this much like norton ghost (ick) which backs up the MBR and various partitions? I have been reading around and there are various tools such as dd and methods such as "tar cvpzf mybackup.tgz / --exclude=/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys", and a few others. 
Ideally what i would like is a tool with a nice gui which i can save my settings in and then hit a button every time i desire a backup. If not a nice command would do :)

If there is a straight guide im not aware of - please direct me there thank you.

Thanks for your time and help, and i hope to help yourselves in the future :)

Sam.

---

### Post by chewearn on 2007-02-28
You can use the GParted live CD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by sam_i on 2007-02-28
hmm, isnt that the same one you can get via the package installer?

---

### Post by chewearn on 2007-02-28
It's technically the same program, but if you use the GParted from the repository, you would need to run it while in ubuntu.  In this situation, you main ubuntu partition will be locked and you will not be able to copy it.

The GParted LiveCD runs outside your ubuntu boot.  There is also a LiveUSB version, in case you prefer that.

---

### Post by sam_i on 2007-02-28
cheers for that, ill give it a go and see what happens tonight :)

---

### Post by rsambuca on 2007-02-28
The liveCD version of gParted is much more up-to-date than the one in the ubuntu repositories.  I would recommend the liveCD as it is a handy utility to have around anyways.  The newest version of gParted just came out this week.

---

