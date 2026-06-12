---
title: "System won't boot following upgrade to Edgy"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by matt31415 on 2006-11-14
I have just upgraded from 6.06 to Edgy using the recommended method: gksudo "update-manager -c" and now the system won't boot.

I left the upgrade running overnight and in the morning the system seemed to have upgraded fine. Help->About said version 6.10, ran up firefox which was at version 2.0 etc.

I then tried to run synaptic and was asked for an administrative pasword which I had never set up (user password didn't work).

Running synaptic from a console using gksudo gave a "pyGTK module not found" error.

I thought that a reboot might be required so rebooted the system and ever since have not managed to get the system to start up, even in Recovery Mode.

In recovery mode the following is output:

> Running /scripts/local-premount...
[...]Attempting manual resume
[...]ReiserFS:hda1:found reiserfs format "3.6" with standard journal
[...]ReiserFS:hda1:journal params:device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[...]ReiserFS:hda1:checking transaction log (hda1)
[...]ReiserFS:hda1:Using r5 hash to sort names
Begin: Running /scripts/local-bottom...
Done.
Done.
Begin: Running /scripts/init-bottom...
Done.


The system then hangs without displaying any further output. It hasn't even got as far as starting a console I can switch to with Ctrl-Alt-1 or whatever.

I can boot off a KNOPPIX CD and have a look around but I don't have a clue what might be wrong.

Any ideas?

---

### Post by phines on 2006-11-28
Same problem.  Any solutions?

---

### Post by kdawg on 2006-11-28
Maybe boot off the 6.10 disk and do a recovery? Its worth a shot, but don't expect any data to still be there.  Boot the live cd and copy off anything you want to save first I would suggest.  I never upgrade because I always see people having too many problems with it, I always just reinstall.

---

### Post by matt31415 on 2006-11-29
I ended up burning stuff I really cared about onto DVD and then attempting to resize my main partition using QTParted off a KNOPPIX live CD to create some space to copy other data to prior to reinstalling.

QTParted crashed and left the ReiserFS partition unusable so I ended up just overwriting the whole hard drive and reinstalling - ahh well - just starting to re-rip all my audio CDs now!!

In case anyone's interested I've been looking into doing remote backups to ease the pain if it happens again and found [duplicity]("http://www.nongnu.org/duplicity/index.html") to be excellent. I'm now backing up an encrypted copy of my home folder to a load of spare webspace I've got every night.

If you haven't come across duplicity it uses rsync to only transfer changes within files to your remote backup to save bandwidth and uses GnuPG to encrypt the data. Check out this [HOWTO]("https://help.ubuntu.com/community/DuplicityBackupHowto")

---

