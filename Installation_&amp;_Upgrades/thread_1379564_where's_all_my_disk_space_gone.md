---
title: "where's all my disk space gone?"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by poldie on 2010-01-12
I've just performed a clean install of Ubuntu 9.10 onto my 74 hard drive.  I toyed with a vm of XP but have decided to wipe than and do another vm.  I've emptied my deleted items, but I still have a load of space missing. I chose ext4.  

I've googled this sort of thing before and seen that people ask you to df - h, so I've done that, and I can see this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              66G   26G   37G  41% /
udev                  2.0G  268K  2.0G   1% /dev
none                  2.0G  116K  2.0G   1% /dev/shm
none                  2.0G  564K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                   66G   26G   37G  41% /var/lib/ureadahead/debugfs
/dev/sdb1             932G  883G   50G  95% /media/NTFS 1TB


that last entry is obviously my 1tb 2nd drive.   But I don't understand the rest of it.  Debugfs? 26gb used?  Where?

When I run the disk usage analyser it says 25gb used, 40.3 available.

---

### Post by quixote on 2010-01-13
Are you using VirtualBox?  Sometimes it can be stupid about deleted vm's.  Check how much space is being taken up by old machines under /home/your-user-name/.VirtualBox/HardDisks.  (That's a hidden directory, so either select View > Show hidden files, or hit Ctrl-h.)  Look around in all vbox's directories, just in case it's hogging space in some other file(s).

Be nice if it was this easy. :D

---

### Post by drs305 on 2010-01-13
Here's a link to a disk space troubleshooting guide I wrote a while back. It goes through various ways to locate and recover 'lost' free space.

[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

Usually it is undeleted trash or backups made to the wrong partition, sometimes large log files. They are covered and more.

---

### Post by Keith1212 on 2010-03-24
> **drs305 said:**
> Here's a link to a disk space troubleshooting guide I wrote a while back. It goes through various ways to locate and recover 'lost' free space.

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Usually it is undeleted trash or backups made to the wrong partition, sometimes large log files. They are covered and more.
Thanks for this. I thought i was going crazy losing diskspace so fast and not knowing where it is haha.

---

