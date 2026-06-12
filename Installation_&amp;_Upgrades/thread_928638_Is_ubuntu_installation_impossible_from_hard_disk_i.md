---
title: "Is ubuntu installation impossible from hard disk iso ?"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by enthusiastic.sady on 2008-09-24
Asking this questions to experts since many days.
Some says to buy CD-Drives, and bootable pendrives. Can't anyone just straightly answer my question that its not possible from hard disk ? ](*,)

---

### Post by enthusiastic.sady on 2008-09-24
Asking this questions to experts since many days.
Some says to buy CD-Drives, and bootable pendrives. Can't anyone just straightly answer my question that its not possible from hard disk in a system with 128mb RAM? ](*,)

---

### Post by Dougie187 on 2008-09-24
It is not possible to install ubuntu on a hard drive when you are reading the iso from the hard drive that you want to install it. You could do either of the two options that you mention though, making a bootable pen drive, or buying a cd drive and burning a copy of your iso.

---

### Post by enthusiastic.sady on 2008-09-24
> *Thanks*  !

---

### Post by Sef on 2008-09-24
> Can't anyone just straightly answer my question that its not possible from hard disk in a system with 128mb 

I would update the ram to 512 or use a lightweight distro likePuppy Linux, Damn Small Linux, or Deli Linux,

---

### Post by tarps87 on 2008-09-24
You can do a wubi install from windows if you have windows installed. If you want to do it with no os this is not possible.
If you want to use the whole hard drive for the install this would not be possible as you would have to format/ remove the data including the iso from the hard drive.
If you post what your problem is and what you want to achieve someone can probably help.

Edit: I would suggest using a smaller Linux distro if you're using 128mb DSL will run on a system with 64mb(xbox;)) so you should be fine with that

---

### Post by enthusiastic.sady on 2008-09-24
> Just for a knowlege, dont take it else way okey,
Last few months back I copied Win Xp CD into my hard disk and booted my computer in DOS. I entered I386 directory in setup directory of windows. And when I ran winnt.exe, Lo ! I just was reading my computer harddisk and on the other hand installing windows ! Everything worked pretty fine. I am using it now. 
Is that technology remains to be created in ubuntu installer ?

---

### Post by enthusiastic.sady on 2008-09-24
> **tarps87 said:**
> You can do a wubi install from windows if you have windows installed. If you want to do it with no os this is not possible.
If you want to use the whole hard drive for the install this would not be possible as you would have to format/ remove the data including the iso from the hard drive.
If you post what your problem is and what you want to achieve someone can probably help.

Edit: I would suggest using a smaller Linux distro if you're using 128mb DSL will run on a system with 64mb(xbox;)) so you should be fine with that
Wubi could not run in less than 256mb, and I dont want DSL. I prefer Xubuntu.

---

### Post by tarps87 on 2008-09-24
Did you install it to the same partiton? What version of windows was it?
An iso is a disk image so you would not be able to browse this unless you copied the files out of the iso. Dos uses the fat32 or fat16 file system and Ubuntu will by default want to use the ext3 file system which will require formating the partiton. There may be a way using two partitions and Unix but you would need to get the Unix enviroment on to the pc. I am not experenced it this so can not help.

---

### Post by snowpine on 2008-09-24
> **enthusiastic.sady said:**
> Wubi could not run in less than 256mb, and I dont want DSL. I prefer Xubuntu.

I would not recommend Xubuntu for 128mb of ram.
Fluxbuntu is the only member of the -Buntu family that will install comfortably with that tiny amount of ram.

---

### Post by enthusiastic.sady on 2008-09-24
> Fluxbuntu is the only member of the -Buntu family that will install comfortably with that tiny amount of ram.

Fluxubuntu would be great. It's already my 1st choice but the same problem with that ubuntu family. 

I don't think if we call the Ubuntu setup intelligent enough if it cant even know from where it is being loaded into RAM 

And would try to mount the CD-ROM unnecessarily, stopping finally just because it failed to find the CD-ROM drive and letting me never to try it in the 1st step itself ? Is this wise installer ?

---

### Post by enthusiastic.sady on 2008-09-24
> **tarps87 said:**
> Did you install it to the same partiton? What version of windows was it?
An iso is a disk image so you would not be able to browse this unless you copied the files out of the iso. Dos uses the fat32 or fat16 file system and Ubuntu will by default want to use the ext3 file system which will require formating the partiton. There may be a way using two partitions and Unix but you would need to get the Unix enviroment on to the pc. I am not experenced it this so can not help.
I did not install the windows on the same partition BUT neither I want my fluxbuntu or Xubuntu to install on the same partition. 

I have left a 10GB free space just for installing linux without any partition. Once I install it, I will remove WIN XP.

[IMG]http://nandan.110mb.com/images/space.jpg[/IMG]

It is windows XP Professional 2002, SP2. But I have also done same with 2006 before. 

I am using FAT partition on C:\>

And yes where do my files need to be copied from "iso" before being used ?
I have already extracted them on the root directory of C: as it would be on CD. What can be more good place for any setup to find it. Hah Hah !

---

### Post by snowpine on 2008-09-24
> **enthusiastic.sady said:**
> Fluxubuntu would be great. It's already my 1st choice but the same problem with that ubuntu family. 

I don't think if we call the Ubuntu setup intelligent enough if it cant even know from where it is being loaded into RAM 

And would try to mount the CD-ROM unnecessarily, stopping finally just because it failed to find the CD-ROM drive and letting me never to try it in the 1st step itself ? Is this wise installer ?

Perhaps this is one reason why Fluxbuntu is still a "release candidate" a year later. :)
I love Fluxbuntu, but it is a little buggy...

---

### Post by enthusiastic.sady on 2008-09-24
Thats not problem with just Flxbuntu, but exactly the same problem with Xubuntu too. Its one of the most famous official ubuntu based distribution.

---

