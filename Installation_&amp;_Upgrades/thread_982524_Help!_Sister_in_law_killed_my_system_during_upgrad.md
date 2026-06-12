---
title: "Help! Sister in law killed my system during upgrade to 8.10"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by pldobs on 2008-11-14
I was somewhere in the process of updating to 8.10 when my sister in law thought she was turning on my computer when in fact she turned it off.  I don't know where it was during the upgrade.  I'm guessing it was either waiting for me to confirm if I want to replace a configuration file while installing packages or it was done and waiting for me to confirm a reboot.

Now, when I try to boot up, I get:

Starting up ...
[    0.004000] Aperture beyone 4 GB.  Ignoring
[    0.640107] Kernel panic - not syncing:VFS: Unable to mount root fss on unknown-block(0,0)


If I boot to the earlier kernel from my grub menu (Ubuntu 8.10, 2.6.24.21 instead of the latest Ubuntu 8.10 2.6.27.7), I get a little farther until it complains about mu Nvidia driver and then automaatically reboots.

I have a HP pavilion a1710N with 3 Gig ram and some 64 bit dual core AMD processor.

I'm hoping not to have to do a clean install, any ideas what I can do?

---

### Post by Pumalite on 2008-11-14
Get into 'Recovery Mode' of the latest kernel and do this:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by pldobs on 2008-11-14
The recovery mode option from the grub menu gives me the same problem.  Is there a way to get into it from the live CD?

---

### Post by Pumalite on 2008-11-14
Can you get into Recovery Mode at all? What is the exact error message? Are you able to write the commands I gave you.?

---

### Post by pdwerryhouse on 2008-11-14
Your best bet is to boot off one of the Ubuntu CDs (I think it's the "alternate" CD), choose the Rescue option, and then try to make the upgrade finish manually.

If I remember correctly, it will try to mount your installation image somewhere and then you can use chroot to go in and clean up the system (eg, if it puts the image under /mnt/recover, then use chroot /mnt/recover to access it).

Once you're in, something like this might clean it up:

```
dpkg --configure -a
apt-get safe-upgrade
```

---

### Post by pldobs on 2008-11-14
Recovery mode gives me essentially the same error but it it a little more wordy.  I am unable to get to a command prompt from recovery mode or normal mode.

---

### Post by rfs1970 on 2008-11-14
Hi there,

I believe it wasn't your sister in law at all.
Unfortunately, this new version of ubuntu (8.10)
is full of bug!
[URL="http://ubuntuforums.org/showthread.php?t=963853"]
read here[/URL]

---

### Post by pldobs on 2008-11-14
Sorry, I posted the last comment before reading the post about the alternate cd.  I will try to find that cd and do as you instructed.  I'll let you know how it goes.  Thanks for all the pdwerryhouse and Pumalite!!

---

### Post by pldobs on 2008-11-14
Yikes!  I just upgraded 3 computers to 8.10.

---

### Post by iponeverything on 2008-11-14
Boot the earlier into single user.

---

### Post by infinitejones on 2008-11-14
I read the thread title too quickly and I thought it said "Sister in law killed during my system upgrade to 8.10".

Ubuntuforums can't really help you with that sort of thing...

---

### Post by pldobs on 2008-11-15
Solved!  I downloaded the alternate 8.10, went into rescue mode, mounted my root volume, ran the commands suggested by Pumalite in post #2.  It boots!  Thanks for all your help!

---

### Post by Pumalite on 2008-11-15
Glad it helped!

---

### Post by steveneddy on 2008-11-15
> **pldobs said:**
> Solved!  I downloaded the alternate 8.10, went into rescue mode, mounted my root volume, ran the commands suggested by Pumalite in post #2.  It boots!  Thanks for all your help!

SWEET!

can we mark this as solved?

---

