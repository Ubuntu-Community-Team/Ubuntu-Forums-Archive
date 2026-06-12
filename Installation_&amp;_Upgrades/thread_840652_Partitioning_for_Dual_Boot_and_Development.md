---
title: "Partitioning for Dual Boot and Development"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by FredJones on 2008-06-25
I have a new PC with a large hard drive (300 G) onto which I installed Windows 2K. I left unallocated space and I now would like to add Linux, but I inadvertently used 4 primary partitions it seems, and thus I can't add another extended partition. Attached is a picture of how Windows sees the drive.

What I think I need to do is copy the data from my D, E and F drives onto another machine (or my external USB drive), then reboot with PartedMagic and delete those 3 partitions and then recreate them (because I want them in Windows for now) and then make a partition using all the unallocated space and make THAT one the extended partition.

Then when I install Ubuntu, I could make all the partitions I need within that extended one. I use this machine for web development, if that makes any difference.

Anyhow, does that sound like the correct approach? Is there perhaps an easier way? Maybe I can just use PMagic to change the type of the D drive? Probably not, eh? :)

Thanks!

---

### Post by Pumalite on 2008-06-25
I would save the data in F. Delete that partition and merge it with the rest of the unallocated space. Make that an extended partition and within that you can create as many logicals as you want. For Ubuntu:
10 GB fot '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
I'd use Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by FredJones on 2008-06-25
> **Pumalite said:**
> I would save the data in F. Delete that partition and merge it with the rest of the unallocated space. Make that an extended partition and within that you can create as many logicals as you want.


I can do that? I don't know a whole lot about partitioning. But you are saying that if I remove F then I could make there an extended partition? If I install Ubuntu there, then I presume I can make some data partition in a format that Windows can also read, correct?

> **Pumalite said:**
> 
 For Ubuntu:
10 GB fot '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.


I had considered using more partitions actually. :)

> **Pumalite said:**
> 
I'd use Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Yes? Is this easier/better for me than PartedMagic Live CD?

Thank you for your help!

---

### Post by Pumalite on 2008-06-25
You can have you 'data' partition within that extended one formated ext3 or ntfs. Ubuntu can read and write to ntfs. If you decided to make it ext3; I can give you a driver that would allow Windows to see it. Gparted is the best partitioner around. You don't need any more partitions than I suggested.

---

### Post by FredJones on 2008-06-25
OK, sounds good. Two more questions:

1. Your 3 partition schema put 10G in / but IIRC the default location for Apache document root is in /var/www which will be in / therefore, correct? Since I have a LOT of data there, I could either increase that 10G or set Apache to use a dir in /home instead. Correct?

2. This machine has 2G RAM. I was planning therefore to allocate 2G for /swap. FWIW this is a desktop, not a laptop. Anyhow, would you recommend 2G for /swap now for me?

Thank you.

---

### Post by Pumalite on 2008-06-25
I don't use Apache. Maybe you need a /var partition. I don't know. If you have a Desktop; 1 GB /swap is enough.

---

### Post by Pumalite on 2008-06-25
You might find this informative:
[http://www.faqs.org/docs/securing/chap3sec13.html](http://www.faqs.org/docs/securing/chap3sec13.html)

---

### Post by FredJones on 2008-06-26
Thank you very much for your help.

---

### Post by kevmitch on 2008-06-26
Whether you need more partitions than / and /home is really a matter of taste. It's totally doable to have your apache2 root in home, in fact that might even be better than in /var. /var always seemed kind of a silly place to put a web or ftp server roots to me, but again . . . matter of taste. 

I agree that 1GB of swap is fine. It will hardly get used, and you probably want it that way. If you actually start to fill up 1G of swap, you should really get more RAM. 

I also agree that you want to use gparted. You should probably even be able to use it from within the Ubuntu live cd.

---

### Post by FredJones on 2008-06-26
> **kevmitch said:**
> /var always seemed kind of a silly place to put a web or ftp server roots to me

Me too actually. :)

> **kevmitch said:**
> 
I agree that 1GB of swap is fine. It will hardly get used, and you probably want it that way. If you actually start to fill up 1G of swap, you should really get more RAM. 

I also agree that you want to use gparted. You should probably even be able to use it from within the Ubuntu live cd.

Great. Thank you!

---

### Post by Pumalite on 2008-06-26
The Gparted Live CD is a newer version, more flexible and more powerful; offering much more control:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boopt from it. It's also good to have around for all kinds of jobs

---

### Post by FredJones on 2008-06-26
Thank you. I got version 0.3.6.7 for now and I am trying to make my USD thumb drive bootable. :)

---

### Post by Pumalite on 2008-06-26
You can install 8.04 to a pen drive as if it were a hard drive. You can add Super Grub:
[http://ubuntuforums.org/showthread.php?t=647321](http://ubuntuforums.org/showthread.php?t=647321)
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

---

### Post by FredJones on 2008-06-26
Thanks. I meant GParted and I have that now--my flydrive is bootable into GParted. I must override video detect b/c my GForce isn't detected correctly, but once I do that, I get X and Gnome and all is well. Tomorrow morning I will try to repartition, after I have backed up everything.

Thank you.

---

### Post by Pumalite on 2008-06-26
Good luck.

---

### Post by FredJones on 2008-06-27
I actually had to REMOVE the D partition b/c apparently I can only have one Extended partition. So I deleted that, recreated it as a Primary, and then removed F and put there ('til the end of the disk) an Extended and then installed. I actually in the end decided to install LinuxMint, but anyhow the install went perfectly and no data from C or E was lost.

Thanks everyone!

---

### Post by Pumalite on 2008-06-27
Good luck.

---

