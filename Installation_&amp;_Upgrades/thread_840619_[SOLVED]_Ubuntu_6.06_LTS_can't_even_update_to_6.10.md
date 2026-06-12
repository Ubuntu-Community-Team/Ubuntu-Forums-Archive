---
title: "[SOLVED] Ubuntu 6.06 LTS can't even update to 6.10"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by psbh on 2008-06-25
Hi, I've installed and got a Ubuntu 6.06 LTS running at a remote site. It will not update to any later version of Ubuntu than a beta of Ubuntu 8.04 -- at that time in April, using the console commands.

I've tried everything from apt-get -u dist-upgrade to apt-get -o Debug::pkgProblemResolver=yes dist-upgrade. No luck, at all.

Now, not even the updates of the 6.06 LTS will update in the Update Manager.

Could it any way be the Raid 1-disks causing the problem. I've never experienced this before.

Any suggestions -- before I give the logs a good hard look and maybe even a fresh install?

//psbh

---

### Post by Rocket2DMn on 2008-06-26
Edgy Eft (6.10) is no longer supported, so there aren't even repositories for it anymore, which is why can't upgrade.  You will need to do a LTS to LTS dist upgrade to get to Hardy Heron.  However, I suggest just doing a fresh install if possible, it will be a lot cleaner, and probably faster.

---

### Post by hamdy on 2008-06-26
ummmm . i had the same problem with 6.10 edgy
but unfortunately , i dont know how to make a live CD , i have the .iso of the ubuntu 7.10 ...
so if u can help either telling me how to upgrade from 6.10 ( which seems impossible now )
or by telling how to make a live CD and then actually how to use it  without missing with the hard disk partitions as i am running windos XP as well...

i ll be very thankful ..

thanks in advance :)

---

### Post by avtolle on 2008-06-26
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso) for information on burning a cd. Personal experience compels me to add to the excellent discussion therein contained, in addition thereto and not in limitation thereof, that one should burn at a slow speed (4x) to a CD-R (especially if the hardware is, shall we say, a bit mature) after checking the md5sum of the iso (to be done before burning as an image). Then, after burning, upon boot, select the option to check the CD for defects (option 4, IIRC). Good luck.

---

### Post by Rocket2DMn on 2008-06-26
You can't direct upgrade from 6.10 to 7.10 or 8.04, you have to go from one to the other, ex: 6.10->7.04->7.10->8.04
While this is possible, it is not advisable since it will take forever and is likely to break some stuff along the way.  I suggest doing a clean install on your machine - this will require you to do manual partitioning so that you can keep your Windows partition intact, then overwrite your existing root ext3 formatted partition (/).  You can keep your existing swap partition.  
You should get your hands on the .iso for 8.04 Hardy Heron since this is the latest stable release of Ubuntu - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
To burn the .iso to a disk as an image, see here - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

You will need to backup all your important files (like music, pictures, videos, etc) on an external hard drive, which is always a good investment if you don't already have one.

---

### Post by psbh on 2008-06-27
Hi, Rocket2DMn et al! As I expected a full install will be the only viable option. 

It's early days yet on that Ubuntu 6.06 LTS-server. So, hopefully I'll be able to move the HOME-directory elsewhere and start off with a clean slate. But, I must say, it brings me all the way back to the days when we used floppy discs large as dinner tablets and Digital 'mini'-computers, large as refrigerators -- we didn't have displays though, only punch-cards.

Thank's everyone.

//psbh

---

