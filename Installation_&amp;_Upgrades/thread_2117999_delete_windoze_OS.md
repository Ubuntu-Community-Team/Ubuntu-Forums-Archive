---
title: "delete windoze OS"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2013-02-20
Presently I have a dual boot set up, which works just fine except that I don't use windows anymore. 
So how do I remove it and the partition, or should I just delete the Windows OS and use the partition as storage?:KS

---

### Post by dino99 on 2013-02-20
format the windows partition

and dont forget to run :

sudo grub-install /dev/sda
sudo update-grub

then its up to you to use that free space as you want/need

---

### Post by mayagrafix on 2013-02-20
[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/GpartedScreen2_zpsdd8801f5.png[/IMG]

Format the ntsf partition to what protocol?

and what is this for?
 
> sudo grub-install /dev/sda
sudo update-grub

Is there any problem with reformatting and the Windows boot manager? (or GRUB2)

Thanks for your help -:KS

---

### Post by dino99 on 2013-02-20
here is a standard install

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: simply erase it, or format as you want for now, you will reformat as it need when you will use it.

---

### Post by oldfred on 2013-02-20
I normally suggest smaller system partitions and larger data partitions. Do not use Windows tools for Linux. You can just use gparted to reformat to ext4 or whatever you want.

You can just use it as data or move /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    If a ext4 data partition you will have to manage ownership & permissions. Often best with permanent mount in fstab.

       Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

