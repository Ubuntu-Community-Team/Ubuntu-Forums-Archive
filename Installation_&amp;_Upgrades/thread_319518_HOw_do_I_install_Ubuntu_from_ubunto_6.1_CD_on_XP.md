---
title: "HOw do I install Ubuntu from ubunto 6.1 CD on XP?"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2006-12-15
I just recieved my Ubuntu 6.1 CD PC edition.
If I boot off the CD, it simply runs Ubuntu off the CD.
How do I actually install the program on the hard drive?
I have a 40 GB drive and currently running XP with NTFS partition filling the whole drive.

---

### Post by Neobuntu on 2006-12-15
You don't.  ;)

You may install 6.10 (2006 October) from the live booted CD.

256MB RAM is recommended for live CD and then installing from live. 128MB can be done with the "alternate" non-live CD installer but then you might rather run Puppy Linux for S-P-E-E-D on really old computers. Many live CD choices come from Puppy Linux.

BACKUP anything you can't live without on XP just in case you do something silly! You do regular back ups, don't you? Really, don't fail to back up. $10 Flash drives are click and drag easy for this.  Don't remove portable drives until they stop flashing. USB 2.0 is fast and you can add USB 2.0 ports cheap.

Once live "booted", run gparted (or qtparted) and simply resize your one partition (unless there are other reinstall type partitions) to be simply half (50/50). When you then restart XP, it will recheck it's (smaller) drive. So don't panic.

This way when you simply run the install program (from live), just point it to the new blank area (partition) of the drive and let it do all; for you. It will automatically include a swap partition as well. Note that if you can plug the Internet right to the wired Ethernet port (from your router), then by all means, do so FIRST. It will then automatically upgrade (that release) for you.

When you are done, you may simply choose XP or Ubuntu at boot. This is great for hanging on to your old software and for comparison purposes. Not so great for baby sitting Windows and all the time it takes to run security programs (and still be much less secure). Surf safer; only with (k)ubuntu.

It's not like any of this is difficult (today). Everyone is respectfully different though. The thing to note is, it's far easier than installing Windows (for everyone) and anyway, a RECOMMENDED clean install of Windows, negates notions of pre-installed (pre-infected)  somehow being better.

P.S. If you have a second computer, put Kubuntu on the newest one and use the older one for Windows. No resizing necessary.

---

### Post by ibanez on 2006-12-15
or you could run it as a virtual machine using vmware server  or equivelent

---

