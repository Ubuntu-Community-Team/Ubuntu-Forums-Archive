---
title: "Transfer Ubuntu to another Hard Disk ?"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by suffer1989 on 2009-12-02
Hey, here is the situation, i wanna transfer my old ubuntu installation, onto my new hard disk drive, so that all the programs, settings and themes are exactly the same. Im running ubuntu 8.10 of a live CD, and i also have it installed to my new laptop Hdd. My old laptop HDD is connected to my laptop via USB. 






[IMG]http://img694.imageshack.us/img694/7414/drawing.png[/IMG]


> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c49a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6847    54998496   83  Linux
/dev/sda2            6848        7220     2996122+   5  Extended
/dev/sda3            7221       28107   167774827+   7  HPFS/NTFS
/dev/sda5            6848        7220     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3881d423

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12930   103860193+   7  HPFS/NTFS
/dev/sdb3           12931       17909    39993817+   f  W95 Ext'd (LBA)
/dev/sdb4           17910       19457    12434310    b  W95 FAT32
/dev/sdb5           12931       17287    34997571   83  Linux
/dev/sdb6           17288       17909     4996183+  82  Linux swap / Solaris


---

### Post by presence1960 on 2009-12-02
[clonezilla]("http://clonezilla.org/")

---

### Post by wojox on 2009-12-02
+1 clonezilla

+1 for the flow chart. :D

---

### Post by u.b.u.n.t.u on 2009-12-02
A linux migration tool, though I don't know any by name.

A HDD imaging software perhaps clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

Seagate provide a free badged version of True Image called DiscWizard which is quite excellent, though windows based. It may be worthwhile to check your HDD manufacturer website to see if they have anything for linux.

---

### Post by suffer1989 on 2009-12-02
Are there any walkthroughs using clonezilla ?

---

### Post by suffer1989 on 2009-12-03
MAJOR BUMP : WOOHOO, it works.... One more thing though ... i had on my old HDD, a 106GB NTFS partition that used to mount on startup "/dev/sdb1 * 1 12930 103860193+ 7 HPFS/NTFS" ??

I have made a new 160GB NTFS partition on my new HDD, how do i get that to mount on startup ?

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c49a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6847    54998496   83  Linux
/dev/sda2            6848        7220     2996122+   5  Extended
/dev/sda3            7221       28107   167774827+   7  HPFS/NTFS
/dev/sda5            6848        7220     2996091   82  Linux swap / Solaris


---

### Post by suffer1989 on 2009-12-03
Bump... ?

---

### Post by u.b.u.n.t.u on 2009-12-03
> **suffer1989 said:**
> I have made a new 160GB NTFS partition on my new HDD, how do i get that to mount on startup ?

Edit GRUB (boot loader) within Ubuntu 9.10, via Start Up Manager. You will likely need to install it via synaptic. Search for "startupmanager".

As for the bump, normally a 24 hour wait is the etiquette.

I subscribe to my posts and have up to like a dozen different posts I am trying to troubleshoot, and I work my way through the list, hence a delay at times.

A bump under 24 hours would be like "help my other computer is on fire!" ;)

---

### Post by suffer1989 on 2009-12-03
Sorry, i dont usually bump so fast....

Anyways... 

Im trying to recover the stuff from my old hard disk, but am getting worried ...

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c49a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6847    54998496   83  Linux
/dev/sda2            6848        7220     2996122+   5  Extended
/dev/sda3            7221       28107   167774827+   7  HPFS/NTFS
/dev/sda5            6848        7220     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3881d423

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *           1       12930   103860193+   7  HPFS/NTFS**
/dev/sdb3           12931       17909    39993817+   f  W95 Ext'd (LBA)
/dev/sdb4           17910       19457    12434310    b  W95 FAT32
/dev/sdb5           12931       17287    34997571   83  Linux
/dev/sdb6           17288       17909     4996183+  82  Linux swap / Solaris


I am trying to remove stuff from the highlighted partition but, when i plug in my HDD, i cant open/mount that partition...

---

### Post by u.b.u.n.t.u on 2009-12-03
You are trying to access data on a NTFS partition but unable to access it. Is that correct?

You mentioned that you plugged in the HDD. How? Usb, firewire, ribbon?

Are you trying to mount the NTFS partition from within Ubuntu 9.10?

You have a 500GB HDD and 160 GB HDD. If I read this correctly, Ubuntu 9.10 is installed on the 500GB HDD and you want to access, but can't, the 160GB HDD, specifically the NTFS partition. Is that correct?

---

### Post by suffer1989 on 2009-12-03
Ubuntu 8.10 was installed Fresh on my 500GB Hdd, but the customised install was on the 160 GB Hdd. As for the NTFS partition not being abled to be mounted, i rebooted and it was all good. 

A few non critical issues are :
1 - When my PC boots up, the ubuntu bar moves left and right, but normally, when the bar is to expand from left to right, all i see is text, displaying the boot process rather than a graphical loader. How can i restore the graphical bar ?

2 - I used partimage to make a image of my old ubuntu partition, then loaded the image to the bigger partition on my new HDD. However i cant utilise all the space...

[IMG]http://img130.imageshack.us/img130/8321/screenshotxo.png[/IMG]

---

### Post by suffer1989 on 2009-12-03
The partition problem is solved, for others, you simply shrink it to the original partition image size, then extend it.

Working on the Boot screen....

---

### Post by suffer1989 on 2009-12-03
UPDATE  : Resising the partition using gparted off a live CD, did the trick... still, any have any idea on the loader ? The OS loads fine just instead of a graphical bar, theres text instead.

I tried [this ]("http://ubuntuforums.org/showpost.php?p=4815372&postcount=4") but no luck ...

EDIT : for future refrence, and anyone else who may need it, trying [this]("http://ubuntuforums.org/showpost.php?p=4962455&postcount=7"), sorted out my boot screen issues. Im all set now. Thanks for everybodys help !

---

### Post by u.b.u.n.t.u on 2009-12-03
It is morning here, Melbourne Australian, well 06:20 hours now, and I just saw your posts.

So everything is sorted. Good, work!

---

