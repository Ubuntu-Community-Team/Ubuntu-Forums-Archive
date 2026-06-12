---
title: "wipe everything clean"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by blackmail on 2010-10-18
Hi all, I wanna do a fresh installation of the new Ubuntu that is out and i would like to wipe clean all the data, mainly I would only want to leave the music and other stuff (that are my personal files in the /home), but i want to delete all the configuration files from the /home dir, How could that be done when i am reinstalling the system? I suppose that the formatting of my / partition is also good to do, before i reinstall the new Ubuntu.
The current version is 10.04, and my partitions are as follows (fdisk -l)

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496    7  HPFS/NTFS
/dev/sda2            3648       38913   283274145    5  Extended
/dev/sda5            3648        4863     9767488+  83  Linux
/dev/sda6            4864        5349     3903763+  82  Linux swap
/dev/sda7            5350       38913   269602798+  83  Linux

My root is sda5 and my home is sda7. sda1 is unused and so is sda2
Hope this helps in helping me :D

---

### Post by TBABill on 2010-10-18
Basically it sounds like you need to move the files you want to retain to either another partition or an external drive. Since you don't want to save configs or anything, just transfer the files somewhere NOT on the partition where you will be installing (and not onto your swap partition), then install and transfer the files back. I would format the partition you are overwriting when you install if I were doing my own.

---

### Post by rrashkin on 2010-10-18
I just use a flash drive and copy off all of Documents and any special directories (in my case, 'python') and then copy them back after a clean install.

---

### Post by sikander3786 on 2010-10-18
All the config files are hidden inside home directory. Press Ctrl + H to see them. All the directories starting with '.' are some type of config file directories. You can safely delete all of them, reinstall and new files will be produced. 

Said that, backing up important data before reinstallation is always a safer approach.

From the installer, choose manual partitioning and choose sda7's mount point as /home. Make sure it is not selected for a format during install.

---

### Post by blackmail on 2010-10-19
Well then i should be able to smack these files from the Live CD.
I can get around in terminal mainly but the thing is that i wanted to hear some other opinions. I can't transfer my files that easly since there is quite some space used up for my music and other stuff

---

