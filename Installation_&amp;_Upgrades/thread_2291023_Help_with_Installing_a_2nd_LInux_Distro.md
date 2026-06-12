---
title: "Help with Installing a 2nd LInux Distro"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by james139 on 2015-08-17
Hi, I've got Ubuntu up and running and would like to install a second distro. Can I create another partition with my home directory (and any others I should move with it?) in and then share it between the distros? I googled it, but quite a few tutorials only show you how to do it during installation.

Also, do I have to do this with a live disk? I installed gparted but it won't let me do anything to the system disk while it's mounted, and I can't unmount it obviously. Any pointers would be great.

---

### Post by grahammechanical on 2015-08-17
It is up to you but I would not have 2 Linux distributions using the same partition for /home. I imagine there would be a great risk of configuration file conflict. I have a separate partition for my data. Each Linux installation has /home as a folder in the OS partition but each installation can access the data partition. In this way my data is safe if I ever need to re-install.

It is possible to give each installation its own partition for /home. But that is not the way I work. And yes, we modify partitions using Gparted in a Live session.

Regards.

---

### Post by Bucky Ball on 2015-08-17
Yes, best to create a /data partition and share that with the installs. What I do is install each OS with its /home directory inside / (and this will be done by default if you don't create a /home directory, you don't need to tell it to do that). 

Once installed, I delete everything in the /home directory (not lost & found or hidden files/folders of course) and create symlinks to folders on the /data partitions I have created for sharing data, e.g. create /Documents, /Videos, etc. on the /data partition. 

Going this way, no redundancy. Whichever OS you use, all the data files are the same. Change them in one, changes for all. To create symlink see [this]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979") link.

(PS: There are no issues with using the same /home for two installs the way you first described, and there is provision to do that. Choose 'Something Else' during the second install and mark the /home partition to 'Use' but NOT ticked to format. The install will then presume this is the /home partition and create appropriate user settings in *_their own folder named after the new user_* in the /home partition. The new user settings can't get mixed up with old user's, as suggested, because they are in two separate folders in /home, one called 'user1' and the other 'user2', for instance.

This is how I used to do it and it works fine, but it is messy. If you need to reinstall it can be a bit of a headache and the two installs will use and create their own folders so it can create redundancy and get confusing. Used to be the way the majority of users went but not so any more. A separate data partition with /home in / seems to be more regular now.)

---

### Post by lliseil on 2015-12-17
One can safely share *some* application profiles between the distros, on top of the pure docs/multimedia files.

Correct me if I'm wrong but any major application with the _same version_ plus useful data like: browser (eg Firefox since it is updated on every main distro incl. LTS), email client (very good idea to not duplicate them, unless it's a full IMAP-no-filters-no-add-ons profile), maybe LibreOffice (at least dictionaries). If any doubt on the update timing, use the LT version (eg. Firefox ESR) which should add some garanty.

I'm installing a Linuxes dual boot for an old man and it's true that sharing it's full $HOME between two different distros would NOT help him. Even when the two distros aren't rolling-updates like Mageia and *buntu.

---

