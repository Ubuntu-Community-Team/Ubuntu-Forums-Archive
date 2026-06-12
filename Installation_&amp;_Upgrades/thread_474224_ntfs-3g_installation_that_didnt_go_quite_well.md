---
title: "ntfs-3g installation that didnt go quite well"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by haden9 on 2007-06-14
Hello everyone, I was trying to install the ntfs-3g, an application that would allow windows and ubuntu interact with each other thru ntfs. What happened sadly was now Windows VIsta wont load at all, it shows the loading screen but after that it hangs at a black screen and goes no further. Could you plz help out a newbie lol thanks!!!! :popcorn:

Btw here is something you will find useful I think!


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4129    33166161    7  HPFS/NTFS
/dev/sda2            4130        8472    34885147+   f  W95 Ext'd (LBA)
/dev/sda3            8473        8599     1020127+  82  Linux swap / Solaris
/dev/sda4            8600        9729     9076725   83  Linux
/dev/sda5            4130        8472    34885116    7  HPFS/NTFS

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=bbc73752-b602-4d90-8a8d-06f50b8da66d / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=BA28552A2854E6C3 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=D890895B908940CC /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=9cdbbb98-1cf6-45fe-bc34-9930c1b14a43 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by haden9 on 2007-06-16
I decided to re-install Ubuntu, somebody provided me with a good guide to help me install 7.04 so I guess there is no need to answer this post anymore, thanks anyways everyone!!!:popcorn:

---

### Post by Pumalite on 2007-06-16
> **haden9 said:**
> I decided to re-install Ubuntu, somebody provided me with a good guide to help me install 7.04 so I guess there is no need to answer this post anymore, thanks anyways everyone!!!:popcorn:

Could you share your solution with the forum in case it might help someone else in the future?

---

### Post by haden9 on 2007-06-17
> **Pumalite said:**
> Could you share your solution with the forum in case it might help someone else in the future?

I apologize Pumalite, but I actually didn't find a solution to this problem so that why I decided to re-install again everything (Ubuntu and windows) and to let everyone know so that they would look for an answer to my previous problem which was windows not loading (would get stuck on a black screen after showing the message "loading windows") after trying to modify the fstab file. I hope this answers your post.

thanks!,
haden9

---

### Post by Pumalite on 2007-06-17
> **haden9 said:**
> I apologize Pumalite, but I actually didn't find a solution to this problem so that why I decided to re-install again everything (Ubuntu and windows) and to let everyone know so that they would look for an answer to my previous problem which was windows not loading (would get stuck on a black screen after showing the message "loading windows") after trying to modify the fstab file. I hope this answers your post.

thanks!,
haden9

Good. We need to help each other. Thank you.

---

