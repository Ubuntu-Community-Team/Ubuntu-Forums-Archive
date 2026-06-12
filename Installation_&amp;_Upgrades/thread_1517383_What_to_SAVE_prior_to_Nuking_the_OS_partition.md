---
title: "What to SAVE prior to Nuking the OS partition"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2010-06-25
I have a dual boot XP/Ubuntu 10.04 system. (It has a little of Ubuntu Studio too, but not so you'd notice- I installed the audio package but not the whole theme, etc...)

]I was going to give Xubuntu a whirl and I thought to start from a clean slate, so I'm planning to delete the contents of /dev/sda2 where Lucid not resides.

(For the record, XP is on /dev/sda1, I have a smallish swap file after /dev/sda2, then I have a ext4 Home Partition on /dev/sda4.)

What I'm wondering is, what might be useful to archive from the 10.04 OS partition prior to wiping it clean?



TBerk

---

### Post by Windows Nerd on 2010-06-25
> **TBerk said:**
> I have a dual boot XP/Ubuntu 10.04 system. (It has a little of Ubuntu Studio too, but not so you'd notice- I installed the audio package but not the whole theme, etc...)

]I was going to give Xubuntu a whirl and I thought to start from a clean slate, so I'm planning to delete the contents of /dev/sda2 where Lucid not resides.

(For the record, XP is on /dev/sda1, I have a smallish swap file after /dev/sda2, then I have a ext4 Home Partition on /dev/sda4.)

What I'm wondering is, what might be useful to archive from the 10.04 OS partition prior to wiping it clean?



TBerk

Any media files such as videos, music, or documents you wish to save.

Possibly any configuration files in your home directory if you wish to save them if you have installed a lot of programs, or tweaked a lot of settings you wish to save.

That's all I would need to save if I was switching distros.


PS: Your Swap is sda3? Wouldn't it be sda5 if it were an extended partition (which is what Swap is usually set to)?

---

### Post by TBerk on 2010-06-25
> **Windows Nerd said:**
> Any media files such as videos, music, or documents you wish to save.

Possibly any configuration files in your home directory if you wish to save them if you have installed a lot of programs, or tweaked a lot of settings you wish to save.

That's all I would need to save if I was switching distros.


PS: Your Swap is sda3? Wouldn't it be sda5 if it were an extended partition (which is what Swap is usually set to)?

OK, but I believe *those* files; > Any media files such as videos, music, or documents you wish to save. are already in my separate HOME folder. (/dev/sda4)

Frack it. I'll let you know what happens...


TBerk

---

### Post by oldfred on 2010-06-25
Did you do any custom configurations system wide. Like unique settings for video, internet, mounting files, sources. Those would all be in /etc. If I manually change something which with each version seems to be less and less, I try to remember to make a copy and put into /home so I have those settings.

All your user settings are in /home but with a different version even those settings may not be useful. You may want to move your data to a separate partition so it is easy to share.

You can export a list of all installed applications to make it easily to reinstall.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
You can regenerate new sources file
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by TBerk on 2010-06-25
Thx Old Fred. (I've actually done this before, but in that case I just reinstalled the same version of Ubuntu into the newly cleared DIR.)

Once I verify the Xubuntu LiveCD is OK, I'm going to plunge in...


TBerk
actually I'm going to Google a bit 1st too.

---

### Post by TBerk on 2010-06-25
Well, so far so good.  I booted from the LiveCD, ran gparted to delete the old partition, (and the swap while I was at it) and just for fun I changed the order of the two- 

sda2 is now a 2G swap file and /dev/sda3 is my **/** mount point, otherwise known as the OS partition.

As I type this Synaptics Package Manager is updating about 100Megs of stuff.


TBerk

---

