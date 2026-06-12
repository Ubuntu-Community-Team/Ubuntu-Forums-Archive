---
title: "Do I need to unmount and remount a partition?"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by jimwsea on 2010-02-17
I recently installed a dual-boot Ubuntu/XP setup.  The last partition created on the hard disk, for files to be shared by both systems, is called "shared files".  It does not show up under "Places".  I used the disk utility and discovered that the two other ntfs partitions that do show up under "Places" are mounted at "/media/win".  However, the "shared files" partition is shown to be mounted at "/windows".

When I first set the partitions, I believe I did not mount the other two partitions, and chose "/windows" for the "shared files" partition.  [seemed logical but what do I know -- I'm new at this]

How do I get the "shared files" partition to show up under "Places"?
Do I need to unmount from "/windows"?
...if so, do I leave it unmounted, or remount under something else?
Will this require backing up the data?
What is the method?

---

### Post by mikewhatever on 2010-02-17
You probably just need to remount it under /media/, /media/windows or /media/storage being the mount point. If these mount points were created during the installation, you'll need to edit /etc/fstab, changing the mount points to your liking.

---

### Post by jimwsea on 2010-02-18
I used terminal to **type **
**sudo passwd root**
entered a password
**su root**
entered password -- got to root@......
[B]gedit /etc/fstab

[/B]I got into fstab and changed the mount point to "media/storage.  Saved and rebooted.   The partition shows up in "Places", but I get the following message..

[B]Unable to mount Shared Files
Error mounting: mount exited with edit code 1:helper
failed with:
mount: only root can mount /dev/sda10 on media/storage[/B]

Don't know what that means or what to do next.

Also, I type "exit" in the terminal before closing, otherwise my hard disk light will go on for over 10 minutes and if I try to close I will get a message box telling me there is a process running.  What process would take that long?

---

### Post by mikewhatever on 2010-02-18
It doesn't look like you don't know what you are doing, yet you should probably post the contents of your fstab for review.

---

### Post by jimwsea on 2010-02-18
You are correct.  I installed a test drive disk a few weeks ago.  I decided I liked it and started a dual-boot system from scratch last weekend.  Most things are working and I hope that there are only a few tweaks left to smooth out the system.  Thanks for your help so far. 

Here's the fstab text


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=ee93e28c-67d2-421b-bd78-f0dbecd7d55a /               ext4    
errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=a5f3fc08-7741-41d9-b968-f8626ace53e9 /boot           ext4   
 defaults        0       2
# /home was on /dev/sda9 during installation
UUID=5ae9c856-589f-4351-831a-7ea4862d724c /home           ext4   
defaults        0       2
# /windows was on /dev/sda10 during installation
UUID=FC104AFD104ABF00 /media/storage                ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by jimwsea on 2010-02-20
Any response?

---

### Post by Morbius1 on 2010-02-20
There's only one more piece of information that's missing:

Please post the output of the following command:

Open **Terminal**
Type **sudo blkid -c /dev/null**

---

### Post by gadolinio on 2010-02-20
Sorry if i'm missng something, but: can you see the content of your "shared" particion? (regardless its appearence in the Places menu). If you can browse it, you can simply add it to the Places menu. When you're in that partition, go to Bookmarks (in the file browser's menu) --> add bookmark, or press Ctrl+D. Either way you'll have it added as a new bookmark and it will appear in the Places menu.
Regarding the partition management, I use disk manager, an application that lets you configure your partitions, their mountpoints, driver, etc. It can be downloaded from [http://packages.ubuntu.com/search?disk-manager](http://packages.ubuntu.com/search?disk-manager). Click "intrepidW, then go to the bottom of the page, click "all" under architecture, and select any location to download it from. Then install the package and execute it from system-->administration-->disk manager.
Hope you find this useful...

---

### Post by jimwsea on 2010-02-24
I found my shared partition.  Earlier, i was looking in "Places" and in "Disk Utility.  I looked again last night (been out of town for a few days) in the file system and found it, then placed an icon in the panel for easy access.

Guess its part of the learning process.  thanks for all your responses.

---

