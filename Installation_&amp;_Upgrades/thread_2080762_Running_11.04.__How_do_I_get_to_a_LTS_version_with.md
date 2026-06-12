---
title: "Running 11.04.  How do I get to a LTS version without disruption?"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2012-11-04
Hi!    I am  a Linux novice.     I see support has just ended for 11.04, which I'm using on my laptop.   My experience  with upgrades (going from one release to the next) has NOT been good, whether I'm upgrading from the update manager or from a CD.    So I'd like to know how to SAFELY get to an LTS version without destroying my partitions and data.  (My machine has multiple partitions and also boots into Windows through the Grub.)  

My laptop does not have particularly fast hardware, and only has 750M of RAM.  If I can minimize overhead to keep the machine running smoothly,  that would be nice.  

Suggestions?

---

### Post by oldfred on 2012-11-05
I have always been a fan of clean installs since I converted to 64 bit with 9.10. Prior to that I also did not have particularly good experiences with upgrades.

Good backups are first.

If you have a separate /home that makes it a lot easier. Do you have 20GB on hard drive for another / (root) partition. Then you could install 12.04.1 without uninstalling your 11.04. 

Otherwise you have to use manual install or Something else and overwrite your existing /. If you have made any system settings you need to also back those up from /etc and if you have installed a lot of applications you may want to make a list so you can easily reinstall. But list is just a text file and you may want to remove some. Not sure when Ubuntu converted to LibreOffice but older installs were OpenOffice and you do not need both.

My backup is just so I have what I need for a new clean install.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

Since then I found this additional info:
Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by snowpine on 2012-11-05
The absolute safest method in my experience is to set up a "dual boot" between the old version and the new version. Then you can spend a week, a month, a year, as long as you need, migrating your work over to the new version, and always have the old version available as a fallback if you need it.

Since your hardware is aging, you will probably be more satisfied with lightweight Xubuntu or Lubuntu than Ubuntu with the new Unity interface. 

No matter what, you will want complete and full backups before proceeding.

Good luck!

---

### Post by Engineeringtech on 2012-11-07
> **oldfred said:**
> I have always been a fan of clean installs since I converted to 64 bit with 9.10. Prior to that I also did not have particularly good experiences with upgrades.

Good backups are first.

If you have a separate /home that makes it a lot easier. Do you have 20GB on hard drive for another / (root) partition... 

Oldfred,

Thanks for responding.  Sorry for the delay in getting back to you.

All my data (excepting email) is either on my desktop or on a separate NTFS  partition called DATA.   Ubuntu is on a XT3 partition.    And Windows on a FAT32 partition.   I do not have any free unformatted space on my drive.  I do have an external drive I can backup my data to.  I'm not certain where to find my email store or how to back it up.

If I create a CD with an LTS version, can I simply install on top of the existing Ubuntu  partition?  Will it find the partition and will the GRUB installer find all the existing partitions?

---

### Post by oldfred on 2012-11-07
Thunderbird & Firefox are in hidden folders in your /home. You want to be sure to backup all of /home as that has all your user settings & user data.

In Nautilus you can see hidden folders with view, show hidden files.

If you do not backup to a Linux format you will lose your ownership & permissions. For just data that is not critical for for user files & system files it is important to maintain ownership & permissions as set by system.

None of the auto installs will overwrite your existing install. If you use manual install or Something Else, you can select your existing / (root) partition and install to that partition. When you chose format and to format it then overwrites that entire partition.  If you have a separate /home you also choose that, but DO NOT format that partition. It will find your existing swap automatically.

---

### Post by Engineeringtech on 2012-11-07
> **snowpine said:**
> The absolute safest method in my experience is to set up a "dual boot" between the old version and the new version. Then you can spend a week, a month, a year, as long as you need, migrating your work over to the new version, and always have the old version available as a fallback if you need it.

Since your hardware is aging, you will probably be more satisfied with lightweight Xubuntu or Lubuntu than Ubuntu with the new Unity interface. 

No matter what, you will want complete and full backups before proceeding.

Good luck!


Sounds like good advice.  DO you know what versions of Xubuntu or Lubuntu have long term security support?  I wouldn't change anything if I thought I could live without the security updates.

---

### Post by JKyleOKC on 2012-11-07
Xubuntu's LTS versions are <even-number>.04; they come out in April every two years. The latest is 12.04, which is now 12.04.1 in the repositories. It's pretty solid, although I've patched both my copies to use XFCE version 4.10, and the panel applets from 12.10 (which correct some problems in the 12.04 versions that bothered me). There's a PPA that makes most of this easy to do.

---

### Post by gordintoronto on 2012-11-08
What email program do you use? I use Evolution, and under File, there is an option, "Back up Evolution Data". I have used this, and then restored the Evolution data after a fresh installation of Evolution. (The "Back up" prompts you for a file name, if memory serves.)

If you use Thunderbird, I'm sure there is a similar capability.

I also export my bookmarks from Firefox, then restore them on the new installation.

---

### Post by isalovell on 2012-11-08
On answering your original question: I've been managing all Linux machine in our company and when we switched from Windows to Ubuntu, version 11.04 was the then stable version. Now I'm in the same predicament as yourself but I was able to do a clean and safe upgrade WITHOUT loss of any data over the Internet. You just have to make sure that you first install all available updates either from the update manager or via the terminal then you proceed with the upgrade via the update manager as you follow the prompts that'll be popping up. In-case you get stuck you can always get back at us. Cheers.

---

### Post by Engineeringtech on 2012-11-11
> **oldfred said:**
> Thunderbird & Firefox are in hidden folders in your /home. You want to be sure to backup all of /home as that has all your user settings & user data..............for user files & system files it is important to maintain ownership & permissions as set by system..............None of the auto installs will overwrite your existing install. If you use manual install or Something Else, you can select your existing / (root) partition and install to that partition. When you chose format and to format it then overwrites that entire partition.  If you have a separate /home you also choose that, but DO NOT format that partition. It will find your existing swap automatically.

Oldfred,

Thanks for the advice. I think I understand you.   I guess I goofed by not creating a separate partition for /home when I installed Ubuntu.   I think I'm going to upgrade to 12.04LTS, than ask for help installing a faster, lighter desktop shell.    Maybe when this old laptop dies, I will do things right.

---

### Post by Engineeringtech on 2012-11-11
> **JKyleOKC said:**
> Xubuntu's LTS versions are <even-number>.04; they come out in April every two years. The latest is 12.04, which is now 12.04.1 in the repositories. It's pretty solid, although I've patched both my copies to use XFCE version 4.10, and the panel applets from 12.10 (which correct some problems in the 12.04 versions that bothered me). There's a PPA that makes most of this easy to do.


Sir:
Thanks for the reply.  You're not the only person who recommended going to 12.04 and a desktop that is faster and more efficient than Unity.  I'm pretty sure this is the approach I will do.  How do I go about dumping Unity and installing XFCE?

---

### Post by Engineeringtech on 2012-11-11
> **isalovell said:**
> ......... I'm in the same predicament as yourself but I was able to do a clean and safe upgrade WITHOUT loss of any data over the Internet. You just have to make sure that you first install all available updates either from the update manager or via the terminal then you proceed with the upgrade via the update manager as you follow the prompts that'll be popping up........


Thanks.  So you got to 12.04LTS safely?   This is what I'm going to do.  I just have to find out how to install a lighterweight, faster desktop.  My laptop is getting over burdened.  I started with 9.04.

---

### Post by snowpine on 2012-11-11
> **Engineeringtech said:**
> Sir:
Thanks for the reply.  You're not the only person who recommended going to 12.04 and a desktop that is faster and more efficient than Unity.  I'm pretty sure this is the approach I will do.  How do I go about dumping Unity and installing XFCE?

You can install Xubuntu or follow either of these tutorials:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)
[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

---

