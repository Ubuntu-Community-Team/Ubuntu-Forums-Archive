---
title: "Fresh Install with getting Updates and Crashing"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by gargo2000 on 2007-07-03
I recently formated and started from scratch, both windows and ubuntu with dual boot.  After installing Ubuntu 6.06.1 LTS it found all 140 updates.  I proceeded to have them all installed, but once complete, it crashes everything (example I cant load the browser).  I tried rebooting and when I get to the log in screen, I type my username/pass and it tries to load but throws me back to the log in screen.  Tried logging as root and says I'm not allowed to log in here.  I removed the partition and reinstalled Ubuntu again and I got the same results.  I haven't had problems using Ubuntu before.  

Hard drive info I'm installing on if this helps:
 - C drive = 2 partitions
     - 15 gig Fat32 for Windows XP
     - 65 gig NTFS for Ubuntu
- D drive = 30 gig Fat32 (currently blank to use as personal files)

Again, it's only after I install the updates Ubuntu completely crashes.

Thanks for your help!

Gargo

---

### Post by Pumalite on 2007-07-03
If you are assigning 65 GB to Ubuntu, they cant be ntfs. Either ext3 or ext3 and ext2. Check your fdisk -l and post it so people can help you better.

---

### Post by gargo2000 on 2007-07-03
Ok, I'll start a fresh install so I can at least log in to run that command.  I'll be back in a little while....

---

### Post by gargo2000 on 2007-07-03
I tried using the FDISK command and I received the following message "Cannot open /dev/hda5".

This install is now done in EXT3 with 50gig and a linux-swap of 10gig.

---

### Post by Pumalite on 2007-07-03
Look, I'll tell you this: you  can try giving permission to that drive... sudo chmod 777 /dev/hda5.
But I doubt that's your problem. If that doesn't work, start fresh, and this time defrag your XP several times, get rid of all temp files and things you don't need. Then use Gparted to resize that partition to your needs ( 65 GB?? ) anf format ext3. Then install>?Guided>Use Largest Space Available' and let Ubuntu do it's thing.

---

### Post by NeoLithium on 2007-07-03
Hi gargo2000,
When partitioning for Linux, ensure that you, as stated above, defrag Windows several times ot make it the cleanest and smallest partition possible; then partition your hard drive into one of linux types (Ext2, Ext3, ReiserFS or XFS, etc)  Linux doesn't run on NTFS.

When doing your partition as well, a 10GB swap would be a waste of space, basically you can have that size equal to the amount of RAM you have. IE, make it 512MB or a GB, etc.  Hopefully it all goes well for you.

---

### Post by gargo2000 on 2007-07-03
Thanks for your time tonight!  I now have a happy system with all 140 updates included!

---

