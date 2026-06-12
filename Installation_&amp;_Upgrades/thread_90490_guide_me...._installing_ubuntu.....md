---
title: "guide me.... installing ubuntu...."
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by bigpoppa on 2005-11-15
im currenlty using winXP as my operating system, i tried installing ubuntu yesterday, and it went perfectly fine, the os, but i can't run my XP anymore...

its says something about autchek007 - not found and it reboots my pc back to grub...

btw, i used partition magic to make a linux ext2 partition and a swap partition... but since i was a noob i had trouble about the partition section of the setup for ubuntu....

any tips about this? 

so what i did was erase my linux completely and install winxp again..

can you guys give me safe ways to install linux and make a new partition again.via winxp..

and i can not play mp3's with ubuntu, too.... but i love the interface ;)

---

### Post by peterp on 2005-11-15
Hi

I done it few times by my self but it is too much to write so I was looking on internet to find nice (full of pictures) description how to install ubuntu on system where already is win xp and found this:

[http://forums.overclockers.co.uk/showthread.php?s=&threadid=17343592](http://forums.overclockers.co.uk/showthread.php?s=&threadid=17343592)

and maybe this can help too:

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

I recommend you to use reiserfs file system with notail mount option in that point of instalation: [http://forums.overclockers.co.uk/showthread.php?postid=3930127#post3930127](http://forums.overclockers.co.uk/showthread.php?postid=3930127#post3930127)

It is fastest file system from all given possibilities for instaling ubuntu.

If you want resize win xp partition to make a space for ubuntu then I recommend you first defragment drive with O O defrag (I used version 8.0) use complete/name defrag method and then resize partition with partition pagic (I used version 8.05) but there is also plenty of others tool.

peter

---

### Post by peterp on 2005-11-15
I forget about that mp3 play thing so I suggest you to run Automatix script
described here:
[http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)
[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563) 

it install for you near everything you need.

peter

---

### Post by bigpoppa on 2005-11-16
thanks man, phew i had a hard time finding my post .... threads here spawn like mushrooms

---

### Post by yesplease on 2005-11-16
You can find your post with search (advanced), choose the user name box.

Next time when you cant find XP dont unsinstall it, it is probably not necessary.

When you install Ubuntu I would recommend ext3, it is better than ext2 and safe because it has been tested for many years.

---

### Post by xmastree on 2005-11-16
[QUOTE=bigpoppa]thanks man, phew i had a hard time finding my post ....[/QUOTE]On the menu on the left hand side, go to **Edit Options**.  Under **Messaging & Notification** is an option to automatically subscribe to any threads you've posted in. Check that, then just go to User CP (top left) to see your posts.
:cool:

---

### Post by Toon_84 on 2005-11-16
hi,

i've also some troubles with installing ubuntu....the partitions!

i have two hd who work in raid0 configuration and i made some free space (unallocated,with partitionmagic) but the installer of Ubuntu don't recognize the different partitions and the free space!

what should i do?

thanks

---

