---
title: "Will the install erase my /home?"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by PenguinLust on 2011-06-08
I just began the install process for 11.04 and what I'm trying to do is use a set of partitions that already have Linux file systems on them. I've not set what will be the root partition to be formatted. The install program promises that "/etc, /lib, /usr, /var, ..." will be deleted. That "..." is what I'm concerned about. I don't care if it deletes everything else, but I want to keep my /home. Will I?

---

### Post by oldfred on 2011-06-09
You have to tell it to mount your /home as part of the install, but be sure not to format it.  You also then select / (root) and what format to format it to. It finds an existing swap automatically. If you have other partitions you need to mount them & format also. But if standard desktop you really only need /, swap & /home.

---

### Post by doas777 on 2011-06-09
> **PenguinLust said:**
> I just began the install process for 11.04 and what I'm trying to do is use a set of partitions that already have Linux file systems on them. I've not set what will be the root partition to be formatted. The install program promises that "/etc, /lib, /usr, /var, ..." will be deleted. That "..." is what I'm concerned about. I don't care if it deletes everything else, but I want to keep my /home. Will I?
depends on whether you have a seperate home partition. if you do proceed as oldfred suggests. if not, yes it will either delete you home or fail to format /, which is also a bad idea.
in that case, backup your home to another drive. then when you are setting up, create a seperate home and copy the files over to it via live CD before first login.

---

### Post by PenguinLust on 2011-06-09
Why this talk about formatting? I'm not formatting anything. /Home is on the same partition as the root, so how do I protect /home?

---

### Post by doas777 on 2011-06-09
it is a bad idea to install a new version ontop of an existing / directory without formatting (or at least deleting all the files in / except /home). natty is a very experimental release, and is very differant from what came before. left over files may confuse or even render inoperable your new install. thats my advice. take it if thou wilt. 

back up your home to another partition, perform your install, and copy it back before first login.

---

### Post by PenguinLust on 2011-06-09
Ugh: very experimental. Perhaps I should go w/an older one? The previous release is LTS, isn't it? Could I trust my /home not to be erased then?

---

### Post by garvinrick4 on 2011-06-09
> Ugh: very experimental. Perhaps I should go w/an older one? The previous  release is LTS, isn't it? Could I trust my /home not to be erased then?If your /home is not in a seperate partition it will erase it with new install of any version. 
So when you set up the install you have now did you specify a seperate /home at the time
of installation? 
 Always keep a backup of your /home to be safe. Is no different from any other Operating System, keep backups.

---

### Post by oldfred on 2011-06-09
While you should be backing up all of /home and a few other things normally, a new install is a good time to create a separate /home. Move all your /home from inside your root partition to a new partition. Then when you reinstall mount the new /home as part of it. You in effect only have to do the first few steps of the attached instructions. All three are essentially the same, just using different commands for the copy. See if one seems more clear and use it.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

