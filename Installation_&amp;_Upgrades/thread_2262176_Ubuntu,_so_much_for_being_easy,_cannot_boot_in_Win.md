---
title: "Ubuntu, so much for being easy, cannot boot in Windows XP and wifi is crap"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by rob115 on 2015-01-23
Ok, for the last two days all I have been doing in my spare time is reading, and mostly searching for xubuntu related problems but to no avail. 

Firsly, I'm a novice at computers. Secondly I'm new to xubunti and recently installed it after reading the step by step guides so i would have a dual boot option for Windows XP. 

The main trouble right now is that the computer automatically starts in xubuntu. I tried making a USB key for Boot-Repair and booted the computer from my USB, but it comes to an alternative MS DOS program and I don't know how to use it.

So I tried to install Boot-Repair on xubuntu, using the terminal. But it just comes to error messages. I know I haven't totally wiped my harddrive because I allocated 6gb for xubuntu and that is what it says in the file system properties. 

I did manage to get my printer working fairly easy though! That was a bonus. 

Can anyone help? 

Thanks

---

### Post by oldos2er on 2015-01-23
> **rob115 said:**
>  But it just comes to error messages. 

Please post the error messages in full.

Also please post the output from the following command: ```
sudo fdisk -l
``` which will show us how your disk(s) are partitioned.

---

### Post by rob115 on 2015-01-23
> **oldos2er said:**
> Please post the error messages in full.

Also please post the output from the following command: ```
sudo fdisk -l
``` which will show us how your disk(s) are partitioned.

Ok, I tried it again. But this time I managed to move my pc so I have a wired connection. 


Anyway, it looks like it tries to download a list of things, but then gives me this...... 

```


Reading package lists... Done
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) utopic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

WARNING: The following packages cannot be authenticated!
  libefivar0 efibootmgr libgtop2-common libgtop2-10 libgksu2-0 gksu
  syslinux-common
E: There are problems and -y was used without --force-yes
rdsnuke@rdsnuke-EP058AA-ABU-SR1705UK-GB610:~$ 

``` 

As far as how my disk is partitioned. 

```

Disk /dev/sda: 74.6 GiB, 80060424192 bytes, 156368016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1549f232

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1           2046  12578815  12576770    6G  5 Extended
/dev/sda2  *    12578895 156344579 143765685 68.6G 82 Linux swap / Solaris
/dev/sda5           2048  12578815  12576768    6G 83 Linux

Partition table entries are not in disk order.
Disk /dev/sdf: 14.9 GiB, 16008609792 bytes, 31266816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00904e60

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdf1  *     2048 31266815 31264768 14.9G  c W95 FAT32 (LBA)

rdsnuke@rdsnuke-EP058AA-ABU-SR1705UK-GB610:~$ 


```

---

### Post by yancek on 2015-01-23
> Secondly I'm new to xubunti and recently installed it after reading the  step by step guides so i would have a dual boot option for Windows XP

First, if you actually meant to have xp and xubuntu, I would suggest you find another guide.  Either the guide is bad or you were't following it because you don't have any windows partitions on your drive.  That would explain why it automatically boots Xubuntu.   Also, the partition layout, although it would work, is a bit weird.  The swap is usually 2-4GB although it can be larger or smaller.  Yours is 68GB.  The filesystem is usually 15-30GB, depending upon the size of your drives.  Yours is 6GB.  So basically you reversed things and made the swap the size you should have made the root filesystem and the root filesystem the size you should have made swap.  You don't really need more than 2-4GB for swap but it's optional. 

What command were you running to get the output from your last post?  Were you trying to do an update?

---

### Post by rob115 on 2015-01-23
I was trying to install boot repair, but I suppose since I messed up then that would be useless now?

The commands I was running were..... 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by fantab on 2015-01-23
We don't know what guide you followed but you've managed to erase the Windows and replace it with Ubuntu as yancek explains...
If I were you my 80gb HDD with only Ubuntu would like:
20gb Primary Ext4 '/' Ubuntu system files
68gb Primary Ext4 '/home' ubuntu - personal data.
2gb Primary SWAP

---

### Post by rob115 on 2015-01-24
Ok thanks for your help. I'm not too bothered about having windows as long as I can play my old games, which I've learnt I can do now. How would I do what you recommend above fantab? 


thanks.

---

### Post by yancek on 2015-01-24
You can create a system suggested by fantab above by selecting the "Something Else" option under Installation Type when you boot the install medium.  You should see a window which lists your drives/partitions if you have any.  I'd try googling for how to install Xubuntu for a tutorial, or just Ubuntu as I believe Xubuntu uses the same installer.  You could take a look at the link below.  The first part explains partitioning in Linux and further down a detailed explanation of instlling using the something else option.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by rob115 on 2015-01-24
I wish I had that guide before, thanks!

---

### Post by oldos2er on 2015-01-24
If you encounter the BADSIG error again it can be fixed with [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by yancek on 2015-01-24
> I wish I had that guide before, thanks! 		

google and duckduckgo are your friends.  Anytime you have a question, use a web search engine with "how to ?? whatever" and most of the time you will get results.  Just check the date on any site as instructions change with time and different releases.  Also, make sure it is in reference to Ubuntu if you are using Ubuntu because different distributions don't do everything the same way.

---

