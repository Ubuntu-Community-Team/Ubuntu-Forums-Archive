---
title: "Dual Booting Ubuntu under Windows"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by cowboy.bebop on 2015-07-17
So I just cleared off an old HDD that I had and I would like to install Ubuntu on it, which I don't have a problem installing. It's tearing my Windows HDD apart.

Right now my present setup is

Samsung 250 SSD: Windows 7
Maxtor 160 HDD: Future Ubuntu <
Western Digital 500: Program Files
External HDD: Windows User Profile

I would like to boot unbuntu from the windows boot loader without tearing up the MBR. Not sure where to start really. I have seen white papers and articles online, include reading: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) however, it doesn't explain how to use the Windows boot loader and doesn't say much how the MBR will be written.

[[img]http://i.imgur.com/dl4QK6Wm.jpg[/img]](http://imgur.com/dl4QK6W) 

I am using oracle virtualbox to run ubuntu, but its really sluggish and I would like to utilize my hardware within ubuntu.

---

### Post by yancek on 2015-07-17
If you are using windows 7 and it is installed using MBR rather than UEFI/GPT, this should be no problem if you plan to install Ubuntu on a separate hard drive.  Simply install the Ubuntu bootloader to the master boot record of that drive.  Each hard drive has a specific location on it for this.

A default windows install is incapable of booting any Linux system.  To do that from windows you will need to manually configure/edit windows boot files and to do that you would need to be very familiar with the windows bootloader.  You could use third party software but installing the bootloader to its own drive would be simpler.

---

### Post by oldfred on 2015-07-17
The only Ubuntu install option that gives you the choice on which drive's MBR to install grub2's boot loader into is the Something Else. That is a bit more complex as you have to understand drives & partitions. Most Windows users learn "drive" as in c: drive, d: drive. But a d: drive in Windows can be either another partition on the same physical drive or another physical drive.
To avoid that confusion Linux uses sda, sdb, sdc as drives and number for partitions like sda1, sda2.

You then need to know which drive you are installing Ubuntu into, like sdc or sdd. And choose to install grub to sdc or sdd. You also have to manually create and choose a / (root) partition and swap partition. You can create partitions in advance with gparted and during install just click change to choose mount point like / or create during install. 
Default install is always / & swap which is the minimum you need. But with Something Else you can add /home or other partitions.

Several examples with lots of screen shots:
       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]
 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

[URL="https://help.ubuntu.com/community/Grub2/Installing"]
[/URL]

[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL]

---

### Post by cowboy.bebop on 2015-07-17
So what you are saying, it would be best to install Ubuntu to the HDD, but use the Windows HDD for the bootloader?

---

### Post by oldfred on 2015-07-17
Always best to keep system boot loader on same drive as system, if at all possible. 
Then in BIOS choose to boot drive with Ubuntu as grub2 is a boot manager or has a menu of all systems. Windows only manages Windows installs.
Then if grub breaks for any reason you can still change BIOS or use the one time boot key often f10 or f12 to boot another system.

Some suggest that you disconnect all drives except the drive you want Ubuntu on. Then you can use the auto install. 
But if drive is large, you may end up with a very large / (root) when a smaller / & larger /home or data partition(s) is somewhat better.
If you disconnect drives, be sure to plug Windows back in as sda, or same SATA port as it is in now. Usually drives are in SATA port physical connection order.

---

### Post by cowboy.bebop on 2015-07-17
Ok, I just wiped one of my maxtor hdd just now, preparing for an install. I usually do custom edit and set 
```

[Fri Jul 17 - 04:25:03][~][d:9+/-16][-:3+/-18]
bebop@cowboy]$ lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT

sda      8:0    0    12G  0 disk 
&#9500;&#9472;sda1   8:1    0     9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0     3G  0 part [SWAP]

sr0     11:0    1  1024M  0 rom  


```

15GB for / at the most, 3GB for swap and the rest for /home

---

### Post by oldfred on 2015-07-17
That is saying sda is 12GB, I thought you were using a 160GB drive.
I use 25GB for / (root) and have used about 14GB, but that includes /home, but not any data.

```
fred@trusy-ar:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        24G   14G  9.4G  59% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G   12K  3.9G   1% /dev
tmpfs           793M  1.5M  792M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   92K  3.9G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sda1       500M   16M  484M   4% /boot/efi
/dev/sdb5        28G  3.5G   23G  14% /mnt/backup
/dev/sdb4       385G   82G  283G  23% /mnt/data
/dev/sda6        24G   44M   23G   1% /media/fred/wily
/dev/sdb3        24G  4.3G   19G  19% /media/fred/vivid

```

---

### Post by cowboy.bebop on 2015-07-17
lol sorry bout that. That was from my virtual drive, I guess I didn't think about that at the time. My install was successfull here is my output now

```

[Fri Jul 17 - 08:29:38][~][d:10+/-13][-:1+/-10]
cowboy@bebop]$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   100M  0 part 
&#9492;&#9472;sda2   8:2    0 232.8G  0 part 
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 465.8G  0 part 
sdc      8:32   0 152.7G  0 disk 
&#9500;&#9472;sdc1   8:33   0   9.3G  0 part /
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9500;&#9472;sdc5   8:37   0   3.8G  0 part 
&#9492;&#9472;sdc6   8:38   0 139.6G  0 part /home
sdd      8:48   0 149.1G  0 disk 
&#9492;&#9472;sdd1   8:49   0 149.1G  0 part /media/cowboy/Western Dig-160GB (External)
sr0     11:0    1  1024M  0 rom  

[Fri Jul 17 - 08:29:41][~][d:10+/-13][-:1+/-10]
cowboy@bebop]$ 


```

---

