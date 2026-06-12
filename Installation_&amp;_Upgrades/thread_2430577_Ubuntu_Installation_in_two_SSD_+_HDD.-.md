---
title: "Ubuntu Installation in two SSD + HDD.-"
date: 2019-11-04
forum: Installation &amp; Upgrades
---

### Post by germanloco on 2019-11-04
Hello!  I would like to do a question about ubuntu installation in two SSD + HDD.-

Is worthy an a installation in two SSD on these way? :


SSD 1 
/EFI Boot
/Root

SSD 2
/Home (for Steam games installations) (not Media Files)

HDD 
Storage Media files but no in /HOME and Transmision downloads.-
/Swap 

wich was the best way for that?

my idea is to put the media files in HDD for not use SSD, and the swap partition also in HDD.


i want to use Only SSD disks to system (SSD 1 - ubuntu) and steam games (SSD 2) and the swap partition and the media files in HDD and the Transmision's download on HDD for not "harm" the SSD.-


have sense?


Thanks!!!

---

### Post by CatKiller on 2019-11-04
If those are the drives that you have already then, yes, that is a sensible way to use them.

---

### Post by germanloco on 2019-11-04
[SIZE=2]Thanks for answer![/SIZE]

[SIZE=2]How do I create a MEDIA disk so that in file managers (like nautilius) what is shown in Pictures, Music, Documents is what is in the HDD and not in /home(SSD)?[/SIZE]

[SIZE=2]I hope it is understood![/SIZE]
[SIZE=2]
[/SIZE]

---

### Post by oldfred on 2019-11-04
I keep /home inside / (root) on my SSD.
But have all data in a data partition in HDD linked back into /home, so normal locations look like standard install. Just links instead of actual folders.
You can have links from second SSD & HDD, also. 
I have /home in / on SSD only so the mostly hidden user configuration files also load faster. Since two SSD, it probably does not matter.
Is one SSD faster than other?

New installs now use swap file, not swap partition. If over 4GB of RAM, you may not use swap, anyway. And you really do not want to use swap as it is orders of magnitude slower than RAM. My old laptop with 1.5GB of RAM would use swap if I loaded more than a couple of apps at once. Very slow then.

All similar threads with some discussion:
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

[https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) & 
[https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk](https://askubuntu.com/questions/1058756/installing-all-applications-on-a-ssd-disk-and-putting-all-files-on-hdd-disk)

---

### Post by germanloco on 2019-11-04
Thanks Olfred!!! This is what i want to do!!

I will read that posts!

---

### Post by CatKiller on 2019-11-04
> **germanloco said:**
> [SIZE=2]Thanks for answer![/SIZE]

[SIZE=2]How do I create a MEDIA disk so that in file managers (like nautilius) what is shown in Pictures, Music, Documents is what is in the HDD and not in /home(SSD)?[/SIZE]

[SIZE=2]I hope it is understood![/SIZE]
[SIZE=2]
[/SIZE]

Oldfred has already provided a lot of the details in those links, and the way I would approach that is to mount the HDD somewhere out of the way, under /mnt and then use symbolic links.

It doesn't matter what you call it: /mnt/data or /mnt/hdd if you're feeling conventional, /mnt/bitfatpileofspinningrust if you're feeling more whimsical. Just something that you'll remember what it is. Create a directory in /mnt of your chosen name, and that will become the mount point for your HDD. You *could* have separate partitions for different types of data, but I don't see any point in doing that for flat data. A big chunk of storage organised in directories will be fine.

You mount filesystems with the mount command, and unmount them with the umount command (note that it *isn't* **un**mount). Automatic mounting at boot time is defined by the /etc/fstab (filesystem table) file. You just put an entry in there for your data partition, and specify that you want it mounted at your new mount point, and stick in whatever other options you need. Refer to the partition by its UUID - the /dev/sd*whatever* designations can vary between boots.

Once you've got your hdd mounting properly, whack in some symlinks from your user folders to where the storage is. They'll just redirect writes to those files/folders to wherever the symlink points to. If it's just a one-user, or essentially one user because you're sharing data, you can link ~/Pictures to /mnt/bitfatpileofspinningrust/Pictures, ~/Videos to /mnt/bitfatpileofspinningrust/Videos, and so on. If it's a multi-user system you can link /home/user1/Pictures to /mnt/bitfatpileofspinningrust/Pictures/user1, and /home/user2/Pictures to /mnt/bitfatpileofspinningrust/Pictures/user2, and so on.

Once it's all set up you won't really need to think about it again.

Don't forget to take regular backups.

---

### Post by germanloco on 2019-11-06
If I start the system installation from scratch and in the partition options I do the Media partition in ext4 format, is it necessary to do all the procedure for the disk to mount every time I start the system?

Thanks!

---

### Post by CatKiller on 2019-11-06
I can't remember if the installer lets you set arbitrary mount points or not. If it does, then it should handle the fstab entry for you, yes. You'd still need to make your own symlinks, though. 

Don't be tempted to set the mount point as /media, though, even though that's likely to be an option if there's a dropdown list; that is where *removable* storage is traditionally mounted and may well show on your desktop, which isn't what you want.

fstab is pretty straightforward, though. It's just a text file with an entry per line. It just looks scary because UUIDs are long strings of random characters.

---

### Post by germanloco on 2019-11-06
Ok! I Will try with fstab..

Thanks!

---

### Post by CatKiller on 2019-11-06
There's a lot of information available about how fstab works, some of which oldfred has already linked to, as well as the fstab manpage. The worst thing that's likely to happen if you get it wrong is that the partition just doesn't mount.

If you get stuck just post back with where you've got to and people will be happy to help.

---

### Post by germanloco on 2019-11-15
[SIZE=3]Hello!!!!
I did everything I read from the Oldfred links and it worked fine!

Thank you so much!!![/SIZE]

---

### Post by oldfred on 2019-11-15
Glad it worked.
You can changed to solved.

---

