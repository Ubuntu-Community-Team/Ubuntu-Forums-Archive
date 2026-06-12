---
title: "Ready to install second HD, but some concerns"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by blackbird3216 on 2011-07-10
I took out this 120gb HD from an old computer which I recycled. I took out the SATA cable and an IDE cable just in case I would need them for the installation. 

This would work great as a backup HD for my current 320gb HD. I have never had a backup HD, so I don't know how it works. I have numbered my concerns to make for easy reference. 

1. First, however, is one concern I forgot to address. When I looked up the documentation for my computer (Inspirion 530), it mentions that 
"NOTE: For additional drives, extra screws are not shipped during initial purchase of the computer, but are shipped with the additional drives."

This is terrible! Had I known, I would have taken out some screws from the old computer, but now it is gone, and I don't know what kind of screws I need. I don't even know where to buy them. 

2. In terms of installing the new HD, I read that all I need to do is connect the SATA cable and the power, and then boot up to BIOS, where I would "activate" my drive. Then, Ubuntu should be able to identify it immediately. 

Since I am thinking about doing a fresh install to 10.04, I am thinking about formatting this new drive to ext4, and then backing up my important documents/pictures/music onto this second drive. 

Finally, I would boot up to the 10.04 live disc, and simply do a fresh install onto the 320gb HD, knowing that my files are backed up on the 120gb one. 

Would this procedure work fine, or would Ubuntu have trouble identifying the HD? 

3. My final concern is regarding automatic backups. Assuming that I am able to install the HD perfectly, and get a fresh install of 10.04, I want a program or mechanism to help me backup on a regular basis. I know that Mac users have a convenient program called "Time Machine" but there is no such counterpart for Linux. I also know that there are some command-line utilities that I can use, but I would like to stick with a GUI. Any suggestions?

---

### Post by oldfred on 2011-07-10
I have a coffee cup full of screws, but then I save everything.I would think any computer store would have screws. I think one of the computer tool kits I bought even came with more screws. You might be able to take one from your hard drive & one from your DVD and get by with two.

If drive is partitioned & formated then you will be able to see the partitions with Nautilus. But you may want to permanently mount those partitions or reformat and resize. You may not want NTFS if backing up unless you use compressed files, you may lose permissions & ownership in NTFS.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)
[https://wiki.ubuntu.com/TimeVault](https://wiki.ubuntu.com/TimeVault)
[http://flyback-project.org/](http://flyback-project.org/)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

I just plan on a reinstall if I every have a major crash, so I use rsync to copy /home and some of my /data partitions to a backup partition. And periodically backup important files to DVD. But I have Ubuntu on two drives and XP on the third, so I assume I can boot something.

---

### Post by Theredbaron1834 on 2011-07-10
Plus, and while I don't rec this, you don't really need screws. I have a 2.5 drive just sitting in my computer case. Not safe, not good, not what you want to do. But, while you wait for screws, it is doable. But don't leave it like that. You can get screws for cheap on ebay.

---

### Post by blackbird3216 on 2011-07-14
Hmm. I was thinking about replacing the screws from the expansion cards, with regular screws, so that I have some screws for the HD. Is that a good idea? I mean, there is nothing plugged into the expansion ports, so it would not affect anything.

---

### Post by blackbird3216 on 2011-07-15
up

---

