---
title: "Can't write.. fat32 problem?"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by thejaz on 2005-08-06
Hi, I just downloaded Kubuntu (Ubuntu/kubuntu - the problem is the same regardless of the DE) and installed it.

I have 2 hard drives, identical, 80 gigs each. Before installation, my frst hard drive was completely formatted NTFS and my second, unformatted. During paritioning, this is what I did.
Disk 1: NTFS 80 gig do not use
Disk 2: 
primary EXT3 bootable 8 gig '/'
primary swap 500 meg
primary FAT32 70 gig '/home'

the base paths, i left default - i think that my problem is that I shouldn't have made the FAT32 parition be the home partition. anyway, as you can see, what I was trying to do was create a bi-operating system computer which had plenty of room for installing kubuntu and any extras, a hefty swap partition and plenty of room for sharing between both windows and linux.

ok so everything went smoothly after that until i encountered user setup. i entered a full name / username / password about 5 times before i gave up, thinking I would just do it later because it was being buggy. The installation finished fine and I rebooted, but found I couldn't login to KDE as anything (Wrong username/password),- it wouldn't even let me log in to root when I specified the right password (Root logins not allowed), so I put it into console mode and had a poke around using my less-than-adequate linux skills. all i found was that when i tried to add a user, it said 'Operation failed' at the point of creating a home directory. i tried using '--no-create-home' and it worked. i got back into KDE and logged in, but about 4 erros came up - the last one saying that there was no write access to /home, so KDE was quitting.

Windows can see the new 70 gig partition fine - but is my problem that linux can't actually use fat32? because i thought that fat32 was a common filesystem between both operating systems.

any help is greatly greatly appreciated, i'm desperate to get out of the confines of windows.

thanks,

---

### Post by lol on 2005-08-07
Linux can read and write on a FAT32 partition without any problem. But... using FAT32 for your home is probably not a good idea!

Your problem certainly comes from the fact that a FAT32 filesystem does not use a Unix like permission system to control access to the files. What you should do is to create a small ext3 partition for /home, and create a link from your FAT32 partition to /home/docs, for example.

This way, all the Linux configuration files will be on a Ext3 filesystem, and it will still be easy to save your documents on the FAT32 filesystem.

---

