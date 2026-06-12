---
title: "How? Installing Ubuntu Over fedora 21 without messing Windows 7 64"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by Andre_Lopes on 2015-05-08
Hi ubuntu community!
I currently have this setup :

1 SSD 120 GB
1 HD 500 GB
1 HD 250 GB

Windows is on SSD
Fedora is on SSD (Boot and lvm) and on 500 HD LVM

Screenshots attached[ATTACH=CONFIG]261826[/ATTACH][ATTACH=CONFIG]261827[/ATTACH][ATTACH=CONFIG]261828[/ATTACH]


The objective was to use fedora to development but i decided to move to Ubuntu due to stability issues and another dev issues as well.
Anyway,

I want to put Ubuntu Partially on SSD to speed start up and rest on HDD.


Now... Im using GRUB.


So the question is :

How i install Ubuntu over these fedora partitions without ruining windows partition?
Also, how i set ubuntu partitions to speed its startup by using SSD ?

Obs : Fedora made several GRUB Entries : Fedora 21 version bla bla and version bla bla 2 and rescue center.
I dont know if that will be erased when i install ubuntu, so just saying.


Thanks in advance.

PS: Im not a pro on Linux, so please excuse my questions.

---

### Post by ajgreeny on 2015-05-08
In normal circumstances you can just choose "Something Else" at the partitioning stage of installing Ubuntu and with that you can setup your new Ubuntu partitions to overwrite all the Fedora partitions.

However, your Fedora installation is using LVM and I do not know anything about that and how it might impinge on what I have said above; LVM is something I tried a long time ago and gave up on as I did not understand then how to manage it, and I still do not know now.  There is an option in the installer to use LVM and that may mean you can just choose to use those LVM partitions in your new Ubuntu install, but I will have to leave that for others to advise you.

---

### Post by Andre_Lopes on 2015-05-08
it seems LVM is needed because of the SSD?

---

### Post by sudodus on 2015-05-08
Welcome to the Ubuntu Forums :-)

1. The installation will be safer and easier, if you disconnect / remove the disk with Windows while you are installing Ubuntu.

2. Do you want to overwrite Fedora completely? - In that case it is easy - just give the whole disk to Ubuntu.

3. You can use LVM, but the standard with Ubuntu is not to use LVM, and SSDs can be partitioned in the same way as a hard disk drive.

---

### Post by Andre_Lopes on 2015-05-08
[COLOR=#000000]1. The installation will be safer and easier, if you disconnect / remove the disk with Windows while you are installing Ubuntu.
Cant Fedora and windows share SSD to boot

[/COLOR][COLOR=#000000]2. Do you want to overwrite Fedora completely? - In that case it is easy - just give the whole disk to Ubuntu.
Yes, what about windows?


[/COLOR]

---

### Post by sudodus on 2015-05-08
1. Yes they can ([COLOR=#000000]Fedora and windows can share the SSD to boot[/COLOR]). You can have several operating systems in the same drive. But then it is more complicated and risky to do the installation. ***So you need a good backup before you start***. And you should follow the recommendation of ajgreeny in post #2, use 'Something else' at the partitioning window. Ubuntu can also be in that drive, completely inside it, or with some partition in another drive.

I was thinking that you have three different drives, one SSD and two HDDs. That would make it possible to keep the systems in different drives. So if you have Windows in the SSD drive (where it is now), it would be cleaner to have Ubuntu in one of the HHDs. But if you want Ubuntu in the SSD because of speed, it might be worth the extra effort to install it like that.

2. It seems you want to keep Windows. It is a good idea, at least for a substantial period of time, maybe years.

-o-

You can keep Fedora and install Ubuntu somewhere else, or you can install Ubuntu where you have Fedora now (and overwrite Fedora). The Fedora partition (9 GB) is somewhat small, but it is possible to use it, when you have a separate home partition.

Ubuntu also uses grub, and you can decide where to install it (the bootloader to the head of the drive, and the /boot directory where you want it, you seem to prefer a separate /boot partition, which is possible but not standard for Ubuntu).

Edit: I suggest that you make and use a ***swap*** partition too.

---

### Post by Andre_Lopes on 2015-05-11
Well i gave a last try to fedora 21 but it seems it wanted to keep crashing.
So right now im removing GRUB and removing fedora partitions...
So my question now, is :

Im going to install Ubuntu 14.10 Unicorn

I have the 120 SSD
I have the 500 GB HDD

I want to partition the ubuntu to make it boot fast, using a partition of the SSD.
And i want the programs to go to some partition on the 500 GB HDD

How should i do it? I mean how i config the partitions manually? 

Thanks :)

---

### Post by oldfred on 2015-05-11
I also so not know LVM. But you need to remove that.

Then you can use gparted to create partitions that you want and then use Something Else to use & format those partitions.

I put / including /home on the SSD in a 25GB partition and have large data partitions on HDD. I think link the standard folders like Music, Documents etc back into /home. I do a little with python and I have another folder for those files that I also link back into /home. Then system files that are used a lot including your user settings are on fast drive and data which is not used as much is on slower drive.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
      
 [URL="http://askubuntu.com/questions/461394/how-to-partition-ssdhdd"]http://askubuntu.com/questions/461394/how-to-partition-ssdhdd

      [/URL]
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

    [URL="http://askubuntu.com/questions/461394/how-to-partition-ssdhdd"]
[/URL]

---

### Post by sudodus on 2015-05-11
You must choose between

1. Having all of Ubuntu in the SSD.
2. Having the root partition with programs and other system files in the SSD, and personal files and tweaks, the home partition, in the HDD.
3. Having all of Ubuntu in the HDD.

It would be complicated (and very non-standard) to have the programs in another partition than the root partition. And it is usually no problem. Linux programs share a lot of library programs, so they are not as big as the corresponding Windows programs, where many application programs contain everything in their own program files. If you still want the programs, or should we say some programs, in a separate partition, you need help from someone with more experience than I.

---

### Post by Andre_Lopes on 2015-05-11
I see. Well guys i will have a look at this tonight, i have to go to the uni right now.

Anyway, i was able to remove grub and delete fedora partitions.

So this is what i have now :[ATTACH=CONFIG]261939[/ATTACH]

---

### Post by oldfred on 2015-05-11
Use Windows to shrink the NTFS partition to make unallocated space. And reboot immediately so it can run chkdsk and repair to its new size.
Then you can use gparted on live installer to create partitions or create them as part of install with Something Else.

---

### Post by Andre_Lopes on 2015-05-12
I installed all in the 2nd HDD and it crashed.
Im not sure whats going on.

---

### Post by sudodus on 2015-05-13
Please describe with more details

- which version of Ubuntu you installed
- how you installed it
- how it crashed (describe what happened, and happens when you try to boot)

and please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

More details makes it easier to help.

---

### Post by Andre_Lopes on 2015-05-13
Ubuntu 14.10
Installed on the 2nd. HDD 500 GB on a 3 gb partition
First it crashed randomly when i was just opening the terminal
Then few hours later it ried updating it and it crashed on the middle of the process.


This paste that i posted a few days before removing fedora provides all info :

[http://paste.fedoraproject.org/220455/12870381/](http://paste.fedoraproject.org/220455/12870381/)

---

### Post by Bashing-om on 2015-05-13
Andre_Lopes; Hello;

Allow me to poke my nose into this in order to move this along.
> 
Installed on the 2nd. HDD 500 GB on a 3 gb partition

[color=red]IF[/color] 3 gigs is all that you have allocated for the ubuntu install, do not think it will fly. I seem to recall that 5 gigs is the absolute minimum - and that leaves no room to install anything else .
Maybe now show us the current situation in a form we expect:
```

sudo fdisk -lu
sudo blkid

```
And we see what we are going to do.

[INDENT][INDENT][INDENT]it can still happen
[/INDENT][/INDENT][/INDENT]

---

