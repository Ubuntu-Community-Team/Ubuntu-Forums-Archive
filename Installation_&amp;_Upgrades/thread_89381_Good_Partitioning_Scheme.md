---
title: "Good Partitioning Scheme"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by adamb10 on 2005-11-12
Whats a good partitioning scheme?  I got a 60GB hard drive devoted to ubuntu.

---

### Post by trash on 2005-11-12
for myself and clients I do:

15gb windows
15gb ubuntu
the rest is a shared fat32 for files and backups

---

### Post by adamb10 on 2005-11-12
I mean do I need a home partition and stuff.  :p

---

### Post by trash on 2005-11-12
as far as i know you do and it will created for you during the install... you could also put /home on a seperate partition so reinstalling is painless

edit: sorry i saw '1 cup of ubuntu' and thought it was your fisrt post.

---

### Post by adamb10 on 2005-11-12
Ubuntu defaults to a swap and a big root partition.  How big should the home partition be?  Remember I have a 60GB hard drive devoted to Linux.

---

### Post by trash on 2005-11-12
15 gb is plenty big for root and swap think depending on what you want to install, so you can make your home as big as the rest of the remaining space if you want

---

### Post by adamb10 on 2005-11-12
I'll do 40GB root and 18GB home.  Good?

---

### Post by Kuolio on 2005-11-12
I'd say 8gb to / <root>

and then, if you have windows, save some 8gb for it

then rest of the space I'd put up /home and if you have windows you should make a fat32 partition that is accessible for both OS's

So, if you dont have windows, then 8gb root "/" and rest for "/home", it really makes recovery install milliontimes easyer. Oh, and be sure to install big programs, i.e. games, that let you to choose where they want to be installed, to your biggest partition (/home would be the place in my scheme) if you decide to go with small root partition.

---

### Post by adamb10 on 2005-11-12
I have Windows installed on my 120GB Hard Drive.  I have 2 hard drives.

---

### Post by SickTwist on 2005-11-12
If you have two drives and you intend to use the secondary/slave drive for Ubuntu,  I suggest you make the entire 60 GB drive an extended partition and create all the other partitions within it as logical partitions (this will screw up the drive letters less in Windows).

**6 GB ReiserFS for /**  (Ubuntu uses about 2 GB after a default install so this is plenty of space)
**6 GB unused partition** for future distro testing (not necessary but will make it easier in the future if you want to try something new or use the latest testing release of Ubuntu)
**swap partition** (make it 2x size of RAM but no greater than 2 GB)
**Remaining space formatted as ReiserFS for /home** (/home on separate partition will make future installs much easier).

In your original question you did not mention Windows and that changes things a bit. If you need to be able to read/write common data between both Linux and Windows you should have at least one partition formatted as FAT32. If you already have a FAT32 partition on your Windows drive then you don't need to do anything extra. If not, you may want to create an additional partition (do NOT format / or /home as FAT32) on the Linux drive formatted as FAT32.

---

### Post by adamb10 on 2005-11-12
[QUOTE=SickTwist]If you have two drives and you intend to use the secondary/slave drive for Ubuntu,  I suggest you make the entire 60 GB drive an extended partition and create all the other partitions within it as logical partitions (this will screw up the drive letters less in Windows).

**6 GB ReiserFS for /**  (Ubuntu uses about 2 GB after a default install so this is plenty of space)
**6 GB unused partition** for future distro testing (not necessary but will make it easier in the future if you want to try something new or use the latest testing release of Ubuntu)
**swap partition** (make it 2x size of RAM but no greater than 2 GB)
**Remaining space formatted as ReiserFS for /home** (/home on separate partition will make future installs much easier).

In your original question you did not mention Windows and that changes things a bit. If you need to be able to read/write common data between both Linux and Windows you should have at least one partition formatted as FAT32. If you already have a FAT32 partition on your Windows drive then you don't need to do anything extra. If not, you may want to create an additional partition (do NOT format / or /home as FAT32) on the Linux drive formatted as FAT32.[/QUOTE]

This may be the idiot talking but why does home partitions make future installs easier/painless? :confused:

---

### Post by thechitowncubs on 2005-11-12
[QUOTE=adamb10]This may be the idiot talking but why does home partitions make future installs easier/painless? :confused:[/QUOTE]
so that when you reinstall it keeps all your old settings and files

but... thats only if you are doing a clean sweep of ubuntu

---

### Post by metoo on 2005-11-12
Why not 512 MB swap (won't be used anyhow)...
10GB / root
10GB / (spare or root for future)
39.5 GB /home (and data...)

This way, if you later upgrade or want to try another distro, you have a test partition or install in the 2nd partition and then use the 1st one as a spare.
In the mean time you can use the 2nd 10GB as temp, spare or whatsoever.

---

### Post by SickTwist on 2005-11-12
[QUOTE=metoo]Why not 512 MB swap (won't be used anyhow)...
10GB / root
10GB / (spare or root for future)
39.5 GB /home (and data...)

This way, if you later upgrade or want to try another distro, you have a test partition or install in the 2nd partition and then use the 1st one as a spare.
In the mean time you can use the 2nd 10GB as temp, spare or whatsoever.[/QUOTE]

That's basically what I said, you just changed the order and sizes a bit. 10 GB would work for root, it just seems a bit excessive. Like I said, a full Breezy install only requires about 2 GB for /. I have installed numerous additional programs and my Breezy install is still only using about 3 GB of space for / (my /home is on another partition).

As far as the swap partition not being used, it still doesn't hurt much to have one even if it takes 1 GB. It will come in handy if a program starts gobbling up memory (like Firefox, OpenOffice, or Java apps).

---

### Post by SickTwist on 2005-11-12
[QUOTE=adamb10]This may be the idiot talking but why does home partitions make future installs easier/painless? :confused:[/QUOTE]

Think about how many things you have tweaked since you installed Ubuntu (screensaver, desktop background, themes, Firefox settings and extensions, panels, e-mail, etc.) *All* of these things are stored in your home directory (in hidden files and hidden directories). In fact, that is where all programs store one's customized settings and other data like window sizes/positions.

If you ever decide to reinstall Ubuntu or to install another distro, the / partition can be wiped clean and formatted without altering /home if they are stored on different partitions. If you were to mount the home partition on /home after a fresh install, all of your settings would be the same when you log in.

If you want to experiment between multiple distros, they could all use the same home partition so that your preferences are the same between distros (the only problem arises if the distros use different versions of the same program *and* those versions read/write their settings differently).

For these reasons, I would wager that it is almost always better to have /home separate (if one has the technical know-how to set it up that way).

---

### Post by Treebeard on 2005-11-12
10 GB /
10 GB /var
30,5 GB /home
512 MB swap

I set a seperate /var partition because some logs or cache could grow seriously after some time..

---

### Post by yesplease on 2005-11-12
I will add to the confusion :)  with

5 GB / Ubuntu is just over 2GB
1 GB swap (to be on the safe side, though 512MB may be enough, if you have 1GB of RAM swap will be rarely used))
remainder /home

use good old safe ext3 

reserving space for other distro's seems wastefull to me unless you want to experiment with that

---

### Post by c4pp4 on 2005-11-12
[Linux Partition HOWTO]("http://en.tldp.org/HOWTO/Partition/index.html")

---

