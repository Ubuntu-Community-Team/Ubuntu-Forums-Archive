---
title: "Adding a Second Drive and looking for the best advice"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Darren870 on 2008-03-23
Im running 7.10 on my desktop on a 80 gig drive and am running out of space. I plan on adding a second 100 gb drive and was going to use this guide for installation instructions:

[http://joyrahman.wordpress.com/2008/03/04/installing-a-new-hard-drive-in-ubuntu/](http://joyrahman.wordpress.com/2008/03/04/installing-a-new-hard-drive-in-ubuntu/)

The advice i need is this. I want to be able to add more music to this drive and wondering if its possible to access this music from the /darren/music folder.

Any one have any tips on how i would go about doing this? or any advice in similar nature?

Thanks for the help!
-Darren

---

### Post by logos34 on 2008-03-24
All you need to do is create a another music dir on the 100gb and make a symlink (symbolic/soft link) pointing to it:
> 
ln --help

ln [OPTION]... TARGET... DIRECTORY

So if your new partition on the 100gb is sdb1, then:

mkdir /media/sdb1/music2

ln -s /media/sdb1/music2 /darren/music2

Or you could transfer all your music to the new drive, and make '/darren/music' a link pointing to it.

Make sure to set the ownership and permissions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(-->bottom)

---

### Post by Darren870 on 2008-03-24
cool thanks! im going to try this tomorrow. Ill report back with any issues.

---

