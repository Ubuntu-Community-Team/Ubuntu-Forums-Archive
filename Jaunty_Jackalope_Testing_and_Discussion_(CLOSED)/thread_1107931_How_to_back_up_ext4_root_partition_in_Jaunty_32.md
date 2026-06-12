---
title: "How to back up ext4 root partition in Jaunty_32?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by george1984 on 2009-03-27
I have installed / as ext4, but left /home untouched as ext3 on my second drive (hardy on the first)
                                                                      Partimage apparently does not support ext4.

Not having root partition backed up makes me nervous.

Are there simple dd commands that will back up and restore that will work as an interim measure?

ext4 root is on sdb1 (20Gb) and could be copied to sda2 (home ext3 400Gb)

                 Regards

---

### Post by Anthon on 2009-03-27
dd if=/dev/sdb1 of=/home/BACKUP/sbd1.dump bs=64M

---

### Post by LowSky on 2009-03-27
Im pretty sure ext4 partitions can be mounted as ext3, but I dont know the process as it such a new format.  Maybe someone else does

---

### Post by george1984 on 2009-03-27
> **Anthon said:**
> dd if=/dev/sdb1 of=/home/BACKUP/sbd1.dump bs=64M

Backup Successful!....See my initial mistake below


george@MrGrumpy-01:~$ sudo dd if=/dev/sdb1 of=/home/BACKUP/sbd1.dump bs=64M
[sudo] password for george: 
dd: opening `/home/BACKUP/sbd1.dump': No such file or directory
george@MrGrumpy-01:~$ sudo dd if=/dev/sdb1 of=/home/george/BACKUP/sbd1.dump bs=64M
297+1 records in
297+1 records out
19995655680 bytes (20 GB) copied, 583.383 s, 34.3 MB/s
george@MrGrumpy-01:~$ 


Can I ask for the dd code to restore "sdb1.dump" to /dev/sdb1? just to be certain. Bit more dangerous going this way.

                    Regards

---

### Post by Crandom on 2009-03-27
Yes it is more dangerous this way. Provided you haven't changed the partition size or the partition type (which is fine, as you're using an entire disk), just swap the if= and of= statements. **BE WARNED**; this will **overwrite everything** on sbd1:
```
sudo dd if=/home/george/BACKUP/sbd1.dump of=/dev/sdb1 bs=64M
```

---

### Post by george1984 on 2009-03-27
> **Crandom said:**
> Yes it is more dangerous this way. Provided you haven't changed the partition size or the partition type (which is fine, as you're using an entire disk), just swap the if= and of= statements. **BE WARNED**; this will **overwrite everything** on sbd1:
```
sudo dd if=/home/george/BACKUP/sbd1.dump of=/dev/sdb1 bs=64M
```

This is what I did...

george@MrGrumpy-01:~$ sudo dd if=/home/george/BACKUP/sbd1.dump of=/dev/sdb1 bs=64M
[sudo] password for george: 
297+1 records in
297+1 records out
19995655680 bytes (20 GB) copied, 506.037 s, 39.5 MB/s
george@MrGrumpy-01:~$ 


Reboot into Jaunty drive and.....Test overwrite successful!

    Thanks for the help everybody. Just can't relax if the root partition is not backed up.

                         Bye

---

### Post by habtool on 2009-04-07
FYI:

On a fully updated beta jaunty 9.04, I have now managed to backup a ext4 partition with a tool called fsarchiver, its similar to partimage, but only CLI. (partimage is cool, but does not yet support ext4 and is currently dormant as a project)

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
static binary:
[http://sourceforge.net/project/showfiles.php?group_id=244682&package_id=299271](http://sourceforge.net/project/showfiles.php?group_id=244682&package_id=299271)

For me it did not restore grub to the root partition, info here:
[http://www.fsarchiver.org/forums/viewtopic.php?p=2266#2266](http://www.fsarchiver.org/forums/viewtopic.php?p=2266#2266)

Hope this helps
Habtool

---

