---
title: "Manual Partition HELP"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2009-12-14
I got the partition and everything correct, I just don't understand one thing. The mount point. What's that? I tried leaving it blank, but got an error and could not continue. It gives me a few choices. Which do I want? I'm guessing the top one.
 
Choices:
/
/boot
/home
/temp
/usr
/var
/svr
/opt
/usr/local

---

### Post by raymondh on 2009-12-14
> **kakashi_12 said:**
> I got the partition and everything correct, I just don't understand one thing. The mount point. What's that? I tried leaving it blank, but got an error and could not continue. It gives me a few choices. Which do I want? I'm guessing the top one.
 
Choices:
/
/boot
/home
/temp
/usr
/var
/svr
/opt
/usr/local

You'll need root ... known as / .... which is in windows speak, C: drive

Here's a link on the linux filesystem hierchy

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by kakashi_12 on 2009-12-14
ok, that's what i thought. yup, i know it's the equivelant of "C". I have been reading on other threads and see that I need to create a "Swap" partition as well. Is that right? Would it be a logical partition too?
 
The one i created for install is a primary.

---

### Post by raymondh on 2009-12-14
> **kakashi_12 said:**
> ok, that's what i thought. yup, i know it's the equivelant of "C". I have been reading on other threads and see that I need to create a "Swap" partition as well. Is that right? Would it be a logical partition too?
 
The one i created for install is a primary.

Some more learnings :)

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

SWAP ... do so.  You'll never know when you'll need it.

How much space are you planning to give Ubuntu ?  You might want  to consider separating your /home (where your settings, docs, config files, etc. reside) from root (/).  That way, should you need to re-install, you just reinstall over root and keep your /home intact and ready to be used again.  If you plan to give Ubuntu more than 30gb .... consider separating root from /home.  If less, just keep everything within root.

What type of partition will depend on what you currently have in the HD.  You're limited to 4 primary partitions (or 3 primary + 1 extended).  The nice thing about an extended is that you can create as much LOGICAL partitions within it as you wish.

My reco:

Swap - 1x maximum installable RAM
root - 10gb / does not matter whether primary or logical / ext4 or ext3
/home - as much as you can /logical or primary / ext 3

---

### Post by kakashi_12 on 2009-12-14
Thanks so much for your help. I have 40 GB left for Linux. The other 55 GB was for Win install (which is done already).

---

### Post by raymondh on 2009-12-14
> **kakashi_12 said:**
> Thanks so much for your help. I have 40 GB left for Linux.

How many current partition do you have in your HD (without installing Ubuntu yet)?

If able

swap = 2 GB 
root = 10gb
/home= the rest

Remember tha ubuntu does not care whether it resides in a primary parition or in a logical partition.  Windows does.

If you want, post a screenshot (gparted) of your HD in your next reply and we can both come up with a small guide/how-to.

---

### Post by kakashi_12 on 2009-12-15
i only had one other os installed, one partition. win xp. thanks for the info about logical w/ linux. that's educational :) . Sorry, too late, I already installed Linux. Thanks for your help though.

---

### Post by raymondh on 2009-12-15
You're welcome.  Happy ubuntu-ing :)

---

