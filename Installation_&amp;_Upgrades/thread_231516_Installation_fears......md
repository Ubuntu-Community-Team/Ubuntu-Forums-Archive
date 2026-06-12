---
title: "Installation fears....."
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by pranavm on 2006-08-07
got my cd of ubuntu 6.06 through shipit today..i have never used any linux os..just have some questions about dual booting ubuntu and Win XP home..coz i really want to keep win xp..

i have a 40 gb hard disk,with 2 partitions first one of 35 gb where Win xp is installed and a second one of 2 gb 

how do i go about the installation,, i tried it the first time and did not know how to go about the installation and partition of drives,,got scared of proceeding further than the 6th step(prepare disk space) coz i was scared of losing windows,,,

what should i do at this step and further,,any tutorials ??

:???:

---

### Post by louis_nichols on 2006-08-07
maybe [this link]("https://help.ubuntu.com/community/WindowsDualBoot") will help you. I'm afraid you can't really fit ubuntu in 2 gigs. maybe give it a couple of gigs more. you won't be left with a lot of space for storage, though, and linux can't reliably write to ntfs, yet. so you have to keep these in mind.

---

### Post by dauber on 2006-08-07
I'm a complete newbie to x86-based Linux. (I previously ran Debian on my AmigaOne, which is PowerPC.) Seriously, I found Ubuntu installation to be *incredibly* easy. But you may have seen my  previous post; no dual-boot for me, unfortunately! As long as you know which partition, you're fine. I seem to remember that the install shows you all the partitions, complete with their sizes, so that way you'll know.

---

### Post by confused57 on 2006-08-07
I recommend you use the Desktop Live CD for awhile, maybe even a week or so to get used to Linux & seeing that everything works, like your internet connection, browsing, etc.
Here's an excellent tutorial(in fact some excellent information throughout the site):
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

Also, here's an excellent site for dualbooting:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
The actual installation screenshots for the 2nd link is using the alternate cd...but, there is a lot of good information throughtout the site.

Just read posts, howto's, stickys,etc in this forum and when you're ready to install, you'll be able to formulate a plan before you begin the actual installation.

As mentioned earlier, 2 Gb is too small for Ubuntu...you might want to use Gparted to delete the 2 Gb partition and to resize the Windows partition.  You'll probably need at least 5-6 Gb for installing Ubuntu.
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

If you decide on dualbooting, defragment your Windows partition a couple of times before beginning...back up all your important files that you don't want to lose.

---

### Post by Klaidas on 2006-08-07
First, backup your data. You never know what might happen :)
As for tutorials, this is a really good one: [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by pranavm on 2006-08-07
thanks guys..will try resizing the partitions

---

### Post by pranavm on 2006-08-08
can i use partition magic for resizing the partition or do i have to use gparted to do that//


btw my hard drives are  fat32 not ntfs...

---

### Post by anasofiapaixao on 2006-08-08
Just a warning: in case you have a toshiba laptop, the little brat will have you needing to erase your entire hdd (well, I haven't tried testdisk to rewrite the table), because of the "existence" of a fake called "recovery" partition that will mess your entire partition table... and while windows will boot, Linux won't (same happened on a different toshiba model with fedora core 3).

Well... you can use partition magic but I'd say use gparted. The most important philosophy when it comes to linux is DON'T TRUST WINDOWS. While any linux distro has all interest in multi platform interaction, windows doesn't...

As everyone said the recommended partition size but not the minimum... If you are *really* into a hdd space dilemma, put your ubuntu partition with 3.5GB. I just made a fresh install, with updates, restricted formats support, (but removed ekiga, evolution, and gnome-games/gnome-games-data, which I don't use and total about 60 megs) and it's 3.18 GB large... with 334 MB of apt-get cache, so it should effectively be less than 3GB after cache cleaned.

By the way, BEFORE doing apt-get clean to wipe you cache, don't forget to back up (to a cd or something) the folder /var/cache/apt/archive, because when you mess up your installation (and we always do at first) you only have to copy it back to the due folder without having to download 300MB in updates from the internet all over again...

---

