---
title: "Recommended disk partitions for Ubuntu 11/Win7 dual boot?"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by _Cathy_ on 2011-06-23
Hi there. 

I'm currently installing Ubuntu 11.04 on a new laptop which already had Windows 7 installed
Im just wondering what would be the best way to partition the hard drive in order to do this? I am running the ubuntu installer at the moment, and am a bit confused as to which each partition corresponds to, as they are all just labeled** /dev/sda** followed by 1, 2, 3 or 4 

Can anyone recommend suitable partitions for this situation? 

thanks a lot :)

---

### Post by Frogs Hair on 2011-06-23
Here is a guide that may help . I use the Windows disk utility to create space for Ubuntu , but it can be done with the Ubuntu disc as well . [http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/](http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-11-04-natty-narwhal/)

---

### Post by YesWeCan on 2011-06-23
> **_Cathy_ said:**
> Hi there. 

I'm currently installing Ubuntu 11.04 on a new laptop which already had Windows 7 installed
Im just wondering what would be the best way to partition the hard drive in order to do this? I am running the ubuntu installer at the moment, and am a bit confused as to which each partition corresponds to, as they are all just labeled** /dev/sda** followed by 1, 2, 3 or 4 

Can anyone recommend suitable partitions for this situation? 

thanks a lot :)
It's prudent to use windows to do Windows things. So I would boot Windows and use it's utility to shrink it's partition and create an unused space on the disk for Ubuntu. A defrag may give you more space if you need it.
Then install Ubuntu to the free space (no numbers to remember :) ). The boot-loader boot-code will go to /dev/sda (probably 'a' if you only have one disk) and will destroy your Windows boot-code so if you delete Ubuntu you won't be able to boot Windows; this can be easily restored using a Windows CD, however.
The Ubuntu OS only needs a few GB of disk space. Allow 10GB + user data space. Make the swap partition as big as your RAM (enables hibernation).
You will be able to read from and write to your Windows partition using Ubuntu.

---

### Post by oldfred on 2011-06-23
Most win7 systems have all 4 primary partitions used.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by _Cathy_ on 2011-06-24
What would you recommend as suitable partitions? 
 
Would would be a suitable size for all the differnet partitions?

---

### Post by oldfred on 2011-06-24
If you then only have the one extended to use, all your Linux partitions will have to be logical inside the extended. If you use manual install you can create /home and control sizes of partitions. The auto install just divides things up.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

---

### Post by _Cathy_ on 2011-06-24
Hi, thanks for the responce
 
please, bear with me though, im new to this!
 
This is what it looks like atm: 
[IMG]http://img19.imageshack.us/img19/7853/currentparions.png[/IMG]
 
I assuming C: is windows? Im not sure what the HP_TOOLS bit is at the end - do i need that? 
 
Would you recommend shrinking the windows partition and creating another partition for ubuntu in the space that creates? 
Im guessing i also need another /home partition so i can access files from both windows and ubuntu? is that right? 
 
thanks

---

### Post by oldfred on 2011-06-24
You have to decide what partition to delete. See post #4. Do not create partitions with windows as it may convert to dynamic which can be a real problem.

Be sure to create the vendor recovery disks whether you  delete the recovery partition or the HP tools partition. The HP tools is small so it is easy to backup also. you also want to in windows create a repairCD. You should have repairCds or liveCDs for the current version of every operating system installed. 

Make your own repairCD:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


Your shared NTFS is not another /home, just another data partition. I label mine shared and create a mount point /mnt/shared and mount it as /mnt/shared. Then I link folder from that into my /home. When you get there we can help set that up, but best to plan for another partition now.

---

### Post by _Cathy_ on 2011-06-25
Ive just created a repair disk for windows. Is is also possible to make a repair disk for the other partitions? 
I already have a live CD for ubuntu

---

### Post by oldfred on 2011-06-25
You still should do backups. The repair disk is just to run fixes if there are problems and cannot boot to a recovery mode of some sort. 

Some like image backups as that lets them restore system to the last saved version. I am not good about backing up as often as I should especially if it is a big task. With Ubuntu it is easy to reinstall system and restore /home or your data & user settings. So I regularly backup user settings & my data, most of which for me is not in /home, but not Ubuntu. With windows it is much harder to separate data from system and the image reinstall restores you to as purchased. You then have to rescrub the cruft, do many updates, and reinstall all the apps you have added. All those  updates take many reboots also. So with windows a image of the system is often the best backup.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

