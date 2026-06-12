---
title: "New disk install, then .. dead"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by winewood on 2010-07-15
Greetings. 
I HAD a fully working MythTV box. I went out and bought a new 2TB hard drive.
I used the following commands:
 
sudo mkfs -T jfs /dev/sdb1 : this made it ext2 .. oops
 
so I ran: tune2fs -j /dev/sdb1
to give it journaling like ext3
 
then I added it to the fstab with the UUID instead of /dev/sdb1 (i dont remember the uuid )
/dev/sdb1 /mythmedia ext2 0 2
 
sudo mount -a 
 
it mounted and was happy.
 
Booted, and it worked fine. I copied my Mythvideos to the new mount and it actually was running. I then booted and I get teh following.
 
/dev/sdb1 primary superblock features different from backup, check forced
init: ureadahead-other main process (876) terminated with status 4
/dev/sdb1: Journal inode is not in use, but conains data. Cleared.
 
Then the system hangs.
 
I disconnected the new drive.. booted.. then hung again.
 
Any suggestions?

---

### Post by gr4nf on 2010-07-15
It sounds like your formatting didn't work as it was supposed to. If you have backups of the files, i would use gparted (if you have it) or some other partition manager to reformat the drive as ext4, as that is the modern standard, and then try putting it back in fstab.

---

### Post by winewood on 2010-07-15
I think thats exactly what I need to do.
 
I just cant get to a prompt to do it...??  I have tried recovery mode from the Grub but it wont boot there either.
 
I thought, oh, its just a bad format, so when I unplugged the 2nd (new) drive, it should have gone away right?  Now even the 1st wont boot up.  This makes no sense.  I tried putting the install disc in and booting, but I have no idea how to get it to a prompt that works to fix the entry or re-format that disk.

---

