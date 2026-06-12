---
title: "Breezy install over Hedgehog - /home questions"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by cfraz on 2006-05-13
I just installed breezy on an existing Ubuntu 4.10/XP dual boot box. Everything seemed to work fine, with one exception.  The /home directory did not end up like I had planned. During the partition step, I kept 3 existing partitions: XP, fat32 for linux-to-Xp transfer, and /home.  I told the partition program to mount home as /home (at least I thought that's what I did!).

After installation, I found a new /home (with my new, empty user account) on root, while the old /home was on /media/hda6/home.  Here is my /etc/fstab:

proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs defaults        0       1
/dev/hda2       /boot           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda6     reiserfs defaults        0       2
/dev/hda6       /media/hda7     vfat    defaults        0       0
/dev/hda8       /stor           reiserfs defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I want my home directory on hda5, since it has more room than hda7. So here is my question:

Can I simply edit fstab to mount hda5 on /home to make that my new home directory?  (And if so, what is the command to force a reread of fstab?)

Related question: are there any known issues wiith old configuration files in home/whatever/ breaking apps like firefox, thunderbird, etc. when the new versions are run?

Apologies in advance if this post appears twice - the forum software didn't like me trying to submit a post just after registering for the first time.

---

### Post by aysiu on 2006-05-13
Make sure you have a live CD in case you screw things up.

Then, make sure you back up your /etc/fstab so you can easily fix things with the live CD: ```
sudo cp /etc/fstab /etc/fstab_backup
``` Then, edit the /etc/fstab ```
sudo nano /etc/fstab
``` and replace this line ```
/dev/hda5 /media/hda6 reiserfs defaults 0 2
``` with this one ```
/dev/hda5 /home reiserfs defaults 0 2
``` Save (Control-X), confirm (y), and exit (Enter). Then reboot.

If it works, great.

If it doesn't work, reboot with the live CD and paste these commands into the terminal: ```
sudo mkdir /recovery
sudo mount -t reiserfs /dev/hda7 /recovery
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
``` and reboot again.

---

### Post by cfraz on 2006-05-13
Thanks, aysiu.  The new mount point works fine.  Firefox even picked up my old bookmarks.

---

