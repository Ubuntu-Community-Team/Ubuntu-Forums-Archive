---
title: "Max hard drive space i may require"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by Winalways on 2010-03-20
Hello everybody!

I have been using Ubuntu 9.10 since 3 months now. Now am planning to upgrade to Ubuntu 10.04 beta release. I have Windows installed in a 60 GB partition and Linux in a 30 GB partition in 500 GB and 160 GB hard drives respectively(both on the same machine). I was wondering if I should install my new ubuntu in 60 GB partition. I wanted to know that in future if i install many application software in my ubuntu will it go beyond 30 GB in any case. In case of Windows it is possible to install software in another partition say D drive. Is it possible to do such a thing in ubuntu also? If it can be done I plan to remain with my same partition sizes i.e, 60 GB windows and 30 GB linux. Please guide me in this regard.

---

### Post by ronnielsen1 on 2010-03-20
>  I wanted to know that in future if i install many application software  in my ubuntu will it go beyond 30 GB in any case
Mine does

Most people start off dual booting. A lot of people (including me) find themselves using linux more and more until Windows is just taking up space. Personally I don't use Windows any more. Some people go back to it and quit using linux.

>  In case of Windows it is possible to install software in another  partition say D drive. Is it possible to do such a thing in ubuntu also?

It's not hard to use gparted to increase the size of your Ubuntu install

---

### Post by ultimatelinux on 2010-03-20
some third party applications can be installed on the other harddrive/partition.

---

### Post by srs5694 on 2010-03-20
Linux itself is likely to consume 5-15GB, although extreme installations can go smaller or larger than that. Many people use much more space in big files -- MP3 music collections, digital photos, videos, backups of system software, etc. In most cases, such files are stored in the /home directory or in some other partition that's mounted in odd locations. Thus, the answer to the question of how big to make any given Linux partition depends on how the system is partitioned and how it's used. Many new Ubuntu users create one big partition for everything but swap. This is simple, but it can also lead to problems when upgrading, since user data is on the same partition as the OS itself. Personally, I'd recommend devoting at least 10GB, and preferably 30GB, to the OS as a root (/) partition, or possibly root (/) and /usr (with about 2GB in root and the rest in /usr); then add a /home partition that's big enough for your expected user files. My view isn't universally held, though.

Another, albeit more advanced, option is to use logical volume management (LVM). In this system, one or more LVM partitions are created, and you then create logical volumes within the LVM to hold your filesystems. This adds complexity, but the advantage is that logical volumes can be manipulated much like files, vs. partitions which are very inflexible (partitions must be contiguous). Unfortunately, the Ubuntu desktop installers don't support LVM, so you'll need to use an alternate installer to use LVM with Ubuntu. Overall, it's probably too much hassle for the average Ubuntu newbie, but I thought I'd mention it if you're up for more of a challenge.

I disagree with ronnielsen1 about partition resizing. This forum is filled with posts from people who have trouble with resizing their partitions. One post a couple of days ago was from somebody who was quite miffed at the community for giving him the advice that partition resizing was easy. It's true that if you're familiar with the tools and everything goes smoothly, it's not really that hard; but many people aren't familiar with the tools, and problems often do crop up. Furthermore, it's not safe. Power outages and other problems can completely trash a filesystem when you're resizing or moving it. It can also take hours to complete some operations. IMHO, it's far better to size your partitions appropriately to begin with. On modern hard disks, it's not difficult to allocate enough space for Linux. (Large user files can complicate matters, particularly in a multi-boot configuration, though.)

---

### Post by sleepee on 2010-03-21
thanks for that informative post srs5694.  i'm actually thinking of wiping out my ubuntu install and triple-booting (maybe quad-booting.. if that's possible??) and i was looking for some tips and insight into this..
plus i made the noob mistake of throwing everything into the / partition and didn't realize about the advantage of having a separate /home partition, so this is some good info for me to get it right this second time around...

but im a little confused as to what you meant here:

> **srs5694 said:**
> Personally, I'd recommend devoting at least 10GB, and preferably 30GB, to the OS as a root (/) partition, or possibly root (/) and /usr (with about 2GB in root and the rest in /usr); then add a /home partition that's big enough for your expected user files. My view isn't universally held, though.


did you say have a 30GB partition for root, but have only 2GB in root, and the rest (28GB) in /usr????

i must be understanding wrong, because my root (/) is currently at 10GB, excluding /usr, /home, and /media.  and my /usr by itself is at 5GB currently.
i'm sure there's something i'm not getting..
btw (noobie question), is the /usr for programs???  or are programs stored somewhere else?
sorry if these were dumb questions.. still learning my way around linux...

---

### Post by ronnielsen1 on 2010-03-21
>  Personally, I'd recommend devoting at least 10GB, and preferably 30GB,  to the OS as a root (/) partition, or possibly root (/) and /usr (with  about 2GB in root and the rest in /usr); then add a /home partition  that's big enough for your expected user files. My view isn't  universally held, though.

When I first started using linux I went with a recommendation like this and quickly ran out of room since (excluding personal files) everything wants to install to /usr or /opt. It depends on how you use your computer and what you imstall. 

> I disagree with ronnielsen1 about partition resizing. This forum is  filled with posts from people who have trouble with resizing their  partitions. One post a couple of days ago was from somebody who was  quite miffed at the community for giving him the advice that partition  resizing was easy. It's true that if you're familiar with the tools and  everything goes smoothly, it's not really that hard; but many people  aren't familiar with the tools, and problems often do crop up.  Furthermore, it's not safe. Power outages and other problems can  completely trash a filesystem when you're resizing or moving it.

Personally, I didn't find it hard but wasn't thinking about power outages (and I work as an electrician)

As far as saving /home, another distro has had this feature for years allowing you to save /home on a reinstall or upgrade with the click of a button. It works flawlessly. Now I know this is possible to do in Ubuntu (not nearly as easy) but out of curiosity why doesn't ubuntu include this feature?

---

### Post by ronnielsen1 on 2010-03-21
OK, Ubuntu 10.04 imports settings from /home as long as you're using the same partitions :D

---

