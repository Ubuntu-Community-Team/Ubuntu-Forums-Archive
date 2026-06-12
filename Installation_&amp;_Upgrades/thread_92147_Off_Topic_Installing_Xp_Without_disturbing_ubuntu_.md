---
title: "Off Topic: Installing Xp Without disturbing ubuntu installation"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by 18nikko on 2005-11-18
Hi,
I know this is kind of off topic but I thought I would ask. I currently have a dual
boot machine, win 98 and ubuntu. My windows installation is starting to fail, may
be a virus, though I check pretty religously. I would like to upgrade the windows partition to XP. I have to keep windows around because the kids like to play games. I know windows when installed with overwrite the master boot record. Is there a way to prevent this so I can keep grub intact? Also can NTFS be mounted from linux yet? I know that I used to be able to build a kernel that would read ntfs but writing hadn't been worked out yet.

Thanks

Nicholas

---

### Post by darth_vector on 2005-11-18
hi,

as you said, when you install xp it will overwrite the mbr. you can just reinstall grub to fix this after the installation. there may be a way of stopping this, but i havent heard of one.

as for ntfs partitions, you can mount them readonly. there is some software around that can write to an ntfs partition, but it is experimental and carries the "use at you own risk" sign over it in big, bold letters. if you want to share stuff, set up a fat32 partition.

---

### Post by missmoondog on 2005-11-18
yeah, if your system is failing anyway, may as well start over and be good to go. ntfs is read only still too.

---

### Post by 18nikko on 2005-11-18
Hi,
Yeah, I forgot to mention the floppy drive is broken. Can the ubuntu
install disk be used as a rescue disk? Otherwise how do i reinstall grub without
reinstalling ubuntu?

Thanks
Nicholas

---

### Post by darth_vector on 2005-11-18
you can reinstall grub without reinstalling ubuntu. there is a howto somewhere on how to do it. i will see if i can find it.

---

### Post by darth_vector on 2005-11-18
here it is, it uses the install cd:

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=grub+install](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=grub+install)

---

### Post by 18nikko on 2005-11-18
Thanks!
I guess you can use the breezy install disk as a rescue disk. That didn't work in hoary. Have to do some practice runs to make sure it works.

Nicholas

---

