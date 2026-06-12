---
title: "fresh install of windows/ubuntu 10.10 dual boot"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by xieon on 2010-10-27
My laaptop to begin with isn't that good to begin with, only has a 60g hard drive, and 1 gig of ram.

It's been running slow, even on ubuntu, so I've decided to do a complete fresh install of both.

I want to wipe the harddrive, after backing up my files, and re-install windows, then wubi inside that, and use the 60g internal hardrive for the OS.

Few questions:
My girlfriend just bought me an external 500g hard drive, and I've been slowly backing up files.

1) Should I just copy the entire 60g harddrive onto the external? Or should I make an image of windows, in case of problems?

2)Is there a way in linux to print out to html or text a list of the packages I've installed that didn't come with 10.10, so I can install them again, without having to worry about that problem that required such a package, and o on.

Additionally if anyone can help me with any otherr information that will make this process better, please tell me, I'm open to all suggestions

---

### Post by leclerc65 on 2010-10-27
You can use Clonezilla to backup the entire 60G onto your external hard disk. It should take less than 30G, and 1/2 hour.

---

### Post by oldfred on 2010-10-27
If you like Ubuntu it may be time for a full install to separate partitions.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

You can get a list of installed apps, and on a new install it will install the most current version.

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

You also want to backup /home as that has all your user settings. If you made system wide settings in /etc then you should back up those config files or all of /etc.

---

### Post by xieon on 2010-10-28
Thanks for the two responses, I'm going to list what my plan of attack will be, and if anyone see's any problems let me know. I'll post specific questions about this process at the very bottom

Steps:
Backup/image what I currently have.
Uninstall Wubi
Do a fresh install of windows
partition drive
install Ubuntu to it's own partition.


_Questions_:
With Wubi, I first partitioned my HD, then installed ubuntu onto it's own partition. So, true, it's still wubi, but I didn't install it in the same drive as windows, as many people tell me too. If I don't use wubi, and still partition, I should be able  to mount the windows partition no prblem from linux, correct?

I don't need to uninstall windows, a new installation of windows should clear the whole HD for me correct, also, I don't need to defrag or aanything before/during this step.

---

### Post by oldfred on 2010-10-28
If you have Vista or 7 you should use windows tools to shrink the windows partition and reboot windows several times. It will want to run chkdsk to verify its new size.

You do not have to defrag. I always like to defrag, but some say it is a waste of time.

Ubuntu will read your windows NTFS partition just fine, but I do not like to use foreign systems to write. So I suggest another NTFS parititon for shared data where both systems can read & write without any issues with system partitions. I also like to keep Ubuntu system partition small and have /home or /data with all my data.

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

One suggestion on partitions, for whatever size you want or can allocate to Ubuntu.

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical (or size of RAM memory)

No separate /boot unless old computer, server, encrypted or btrfs system partition.
If lots of room add another root partition for testing/running next version. (I use 3 in rotation)

---

