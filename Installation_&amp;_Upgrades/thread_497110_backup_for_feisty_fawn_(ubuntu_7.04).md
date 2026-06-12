---
title: "backup for feisty fawn (ubuntu 7.04)"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Recca on 2007-07-09
Hi! i'm a new user in this forums. umm, i don't know whether this question has been ask before or not, and i dont  know where to ask it, so i'm asking it here.. 

umm, i'm afraid after doing some experiments (e.g: installling softwares for my ubuntu) my linux going unstable, so i'm curious about how to make it revertable? (without re-installing the ubuntu itself) does anyone here can help me? thx ^^ what i'm searching is a software/method that similarly working like 'restore point for ms windowsXP' ... thx b4 ^^

---

### Post by Herman on 2007-07-10
Hello Recca, :)
Ubuntu doesn't have any 'System Restore' utility. 
We don't need one.
There are all kinds better ways of doing things.

We are not handicapped by the legal restrictions that hobbles users of certian other operating systems. Ubuntu is free after all, so we can have as many copies of it as we like, in the same computer and in other computers too if we have more than one.  Just install another copy of Ubuntu behind the old one and [mount ]("http://users.bigpond.net.au/hermanzone/p10.htm")the disabled system in the new install and copy your files from the old to the new. Then delete the old partition if you want. Or re-install Ubuntu there and  triple-boot, and use one copy of Ubuntu for having fun with. 
I have a 'good' Ubuntu operating system with most of my files in it that I'm a little bit careful with, (but not too careful). I have several other Ubuntu installs that I use for experimenting with. If they get 'hosed', I just delete the partition and re-install. It only takes half an hour to re-install Ubuntu. :)

Ubuntu is much easier to back up and re-install than a certain other common operating system too. It can take days to get that other system back to some semblance of normality after a re-install, but with Ubuntu it only takes about half an hour. There's only one CD, and you don't have to fill out endless on-line forms and reboot after you install every single item of added software.
I use a backup and a re-install script to do a lot of the boring stuff like keeping my emails backed up. My evolution stuff gets automatically backed up every day by crontab settings.  When I re-install, my restore script restores my addressbook, calendar, emial, memos and tasks as fast as you can blink. If you want to see how I do that, I have explained it all in this web-page, [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm")
I guess maybe a developer could easily add a GUI to an scheme like that and make it easy for beginners to use. People wouldn't need to learn anything then though. It wouldn't be as much fun if everything was done for us. It shouldn't be too hard for you to see how I do it on that web page. If you would like to try that let me know if you have trouble and I'll fix the web-page and try to make it easier for others. :)

Another great way to do things is to make a complete backup of the entire operating system and all added software when it's working the way we like, is to use Partimage. aysiu has the best tutorial on Partimage, here, [Use PartImage]("http://www.psychocats.net/ubuntu/partimage"). After a little practice with Partimage, it takes me about ten or fifteen minutes to back up a whole operating system, and about ten minutes to restore one again.
Here's aysiu's [Backing up Ubuntu]("http://www.psychocats.net/ubuntu/backup") too. :)

I'm sure there's lots of other ways of doing the same types of things that others might know of and use. 

Regards, Herman :)

---

### Post by luvr on 2007-07-10
Whenever I want to backup my Ubuntu (or any other Linux, for that matter) installation in such a way that I can easily restore it should the need arise, I will fire up the [System Rescue CD]("http://www.sysresccd.org/Download.en.php")--which is mentioned in one of the links that **Herman** provided in the above post. It allows you to create a partition image, using the PartImage program (also mentioned above). It can write its output file to any partition on either one of the internal hard disks (fast), or an external (e.g., USB) disk (slower, but very handy if there's no space on the internal disks). Great tool!

---

### Post by f1uxam on 2007-07-13
I'm inclined to use PartImage to backup Feisty (64-bit) to an external 750 Gb drive that's currently 2/3 NTFS and 1/3 non-journaled HFS+ (my Feisty can read and write just fine to both, so I'd hitherto seen no need for a native Linux file system). Obviously, I have computers running Win and Mac Tiger.
But, for a PartImage backup, would it be safer to create an Ext3 partition on the external drive?  Currently, NTFS is first; if an Ext3 partition were to be created, should it be after HFS+ ?
BTW, I think GParted is awesome!

---

### Post by rillip on 2007-07-13
Location on the disk shouldn't really matter.  If you're going to make a partition copy, it should be the same FS as you are using on your live install.

---

### Post by JawsThemeSwimming428 on 2007-07-25
Herman,

    The first link in your above post is inactive. I would like to use your walkthrough, can you send me a link?

---

### Post by Herman on 2007-07-26
Sure, JawsThemeSwimming428, :)
Here's another link that's almost the same, [http://users.bigpond.net.au/hermanzone/p10.htm#Filesystem_mounting_basics](http://users.bigpond.net.au/hermanzone/p10.htm#Filesystem_mounting_basics)

  I hope you find that web page easy to understand. If you have any questions please feel welcome to ask me and if it's something I don't know I'll try to find out for you. If it's something I left out or didn't explain well I'll try to fix it somehow so it will be better in the future. 
Regards, Herman   :)

---

