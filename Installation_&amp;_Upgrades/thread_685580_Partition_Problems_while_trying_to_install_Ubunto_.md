---
title: "Partition Problems while trying to install Ubunto 7.10 - NTFS Crap"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Deafable on 2008-02-02
Hi,
Ill do it briefly,
I'm a XP user, who wants to install ubuntu as his primary and only OS.
In XP I had 3 partitions 
c: NTFS 30 GB ~
d: NTFS 130 GB ~
e: NTFS 160 GB 

All i want is to install ubuntu on c: (to format it and install any linux FS).
and i have many important data on d: and e: so i have to keep them in NTFS.

no matter what option i choose on the Partitioner it wont allow me to install!
every option says "Failed".

im very new to Linux and i don't understand in all those JFS, XFS ext3 and such
and i cant figure what to put on Mount Point..

i Want:
c: JFS\EXT3\XFS and such (linux Partition)
d: NTFS - My Data from My windows experience
e: NTFS - My Data from My windows experience

Please! Help! 

P.S - Attached 2 Pictures. 1. of the partitioner and my partitions overall, 2, the problem that occurs no matter which FS i choose or which Mount Point i Set.

---

### Post by zvacet on 2008-02-02
You see message at the bottom left wich telling you what to do.Try to edit partition and then take ~10(I think that is enough) for root 2GB for  swap and rest for home(I belive separate  home is very usefull thing).You must select wich one is root,home...and they are in ext3 format.Other option is to delete partition and have unallocated space on wich you will install Ubuntu.For more details on installling read [this](http://www.psychocats.net/ubuntu/installing).

---

### Post by Deafable on 2008-02-02
still doesn't work..
the problem is that i dont have xp as a OS so i wont need that DUAL BOOT thing,
all i want is to install Ubuntu and see my 2 NTFS partitions through it and not lose all my data

I'm starting to give up on the Linux thing,, maybe ill just go back to the good known XP.

please, any more ideas? I'm running out of tolerance with this,,,
plz help me ASAP as tomorrow i need to go back to the army and who knows when ill come home again

10x

---

### Post by zvacet on 2008-02-02
> the problem is that i dont have xp as a OS so i wont need that DUAL BOOT thing,

Yes,you do,because you want to keep your NTFS partitions with data on it.Follow third option(manual way) and split unallocated space in partitions.After that you have to highlight one at the time and select mountpoint for that partition.That way you will decide how large will your root,home and swap be.You can see all of this on the link I post to you.You can also download [Gparted](http://gparted.sourceforge.net/) and resize and create new partitions with it.Look at [this](https://help.ubuntu.com/community/HowtoPartition).

---

### Post by Pumalite on 2008-02-02
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete the XP partition. In the space left;make the following partitions:
10 GB for '/'
1 GB for /swap (in laptops /swap must be equal to RAM if you want hibernation)
The rest for home.
Install Ubuntu; go Manual and use the partitions already prepared.
Ubuntu comes with ntfs-3g enabled, which enables you to read and write to ntfs partitions.

---

### Post by Deafable on 2008-02-06
still doesn't work it just won't let me install and I can't seem to find gparted other then source code pz its driving me nuts!!!!!!!!!!!!!!&#1505;

---

### Post by zvacet on 2008-02-06
[Here](http://gparted.sourceforge.net/) it is.Download live CD,burn it on disc and boot from it.

---

### Post by dhysk on 2008-02-06
I've had a simular problem with xp an other linux distors before.  What i had found out was that if you creat 3 partitions with the xp disc during install, the part with the blue screen at the begging, xp actually creates one primary partition with the other 2 located under it.  Becuase of this you cant get rid of the primary partition without getting rid of the other 2.  The only option would be to try to resize sda1 and format.  Although im not to sure if you can creat more than 4 partitions.

The way you would know if this is the problem is you will see a tree directory in qtparted when you look at the partition table.  fdisk always showed it as seperate primary partions but that didnt seam to be the case

---

### Post by bwtranch on 2008-02-06
I use fdisk and use the following scheme:

/dev/sda1        boot       +64M
/dev/sda2        swap      +512M
/dev/sda3        root        the rest

You can go on with this and use more partitions and extended. Of course if you have IDE it's /dev/hda. Create a filesystem for each and mountpoints. The best docs for this are on [www.gentoo.org](www.gentoo.org) 

BTW, I guess what you mean by "home" is root.

---

### Post by zvacet on 2008-02-07
> BTW, I guess what you mean by "home" is root.

You are wrong.Read [this](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) for explanation,and [this](http://www.psychocats.net/ubuntu/separatehome) if you want to make one.

---

### Post by Deafable on 2008-02-07
wait.. ubuntu = losing all my data( i have no way to backup 200GB) ???
:\
i guess thats the end of linux for me..

---

### Post by zvacet on 2008-02-07
> wait.. ubuntu = losing all my data

How that happened if you delete just one NTFS partition with Gparted live CD?

---

### Post by Deafable on 2008-02-09
ok
everything work for now
i managed to install using Gparted (amazing tool)..
10x all for all the help

---

### Post by Pumalite on 2008-02-09
Good luck.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

