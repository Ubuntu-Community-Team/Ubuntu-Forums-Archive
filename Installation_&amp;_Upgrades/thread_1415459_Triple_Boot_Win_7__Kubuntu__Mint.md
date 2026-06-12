---
title: "Triple Boot Win 7 / Kubuntu / Mint"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by lazarus99 on 2010-02-24
[FONT=Arial][SIZE=2]Hi  all,[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]This is my first  post here, I'm a new Linux user. I've been trying out Kubuntu via wubi install  on Windows 7 for a few weeks and I've decided that I cant live without it :D. I've  also tried out various livecd's and I also want to install  LinuxMint.[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]My goal is to set up  a triple boot with Windows 7, Kubuntu and LinuxMint[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]I have 2 HDD's one  320GB and one 120GB[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]The 320HDD currently  has Windows 7 and the wubi Kubuntu install. [/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]Is this all I need  to do to get the tripple boot working:[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]1) Uninstall Wubi  Kubuntu[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]2) Shrink Windows 7  and create another partition on the 340 HDD with windows disk  management[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]3) Install Kubuntu  9.10 on the new partition[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]4) Install LinuxMint  8 to the 120GB HDD[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]Do I need to muck  about with boot loaders or will the Kubuntu / Mint take care of  this?[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Is there anything I  need to be mindful of during install?[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Any tips or tricks I  should know?[/SIZE][/FONT]
  
 [FONT=Arial][SIZE=2]Thanks![/SIZE][/FONT]

---

### Post by bruno9779 on 2010-02-24
I would install kubuntu last and give a chance to grub2 to auto-detect the other OS.

Remember there is a chance that something goes wrong (MBR, bootloaders and such can be a pain), so be ready with a live CD of your choice to log in UF and ask for help. :)

---

### Post by oldfred on 2010-02-25
You do need to use the windows tools to shrink the Win7 partition, but make sure it still boots ok afterwards. Most times it wants to do filechecks or other maintenance that many think was caused by the ubuntu/grub install. If you are manually partitioning you also need swap and either /home or /data. The advantage of /data is that it can be shared with the mint install whereas /home should only be used with the same version of linux.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[URL="http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition"]
[/URL]

---

### Post by lazarus99 on 2010-02-25
Thanks guys, I've decided to go with just a dual boot for the time being, I've got windows 7 and kubuntu on separate HDD's and everything seems to be working perfectly :D

Thanks again :P

---

