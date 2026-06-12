---
title: "Installing Ubuntu 12.04 SSD+HDD - Clevo P370em"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by ricak on 2013-05-10
[FONT=arial][COLOR=#333333]Hello Everyone![/COLOR]

[COLOR=#333333]I have this Clevo P370EM laptop with "the paid OS" at the moment, but I am going to try it with Ubuntu.[/COLOR]
[COLOR=#333333]I have a 120gb ssd and a 500gb hdd. So I'm wondering if I have to do some special steps when installing the OS. I'm asking this, because when I installed W7 in it, I installed Users folder (my documents, musics,pictures, videos) in the HDD and for SSD would just be the OS and software.. games would be in the HDD. So, to do this for W7 I had to follow several steps during the instalation in order for the SSD to be preserved.
It will be just Ubuntu. No W, no dual boot.[/COLOR]
[COLOR=#333333]Other thing is the drivers. In Clevo website there are no drivers for Linux.... does anyone of you have Ubuntu in this laptop?[/COLOR]

[COLOR=#333333]my specs are:[/COLOR]
[COLOR=#333333]i7 3630[/COLOR]
[COLOR=#333333]8gb ram[/COLOR]
[COLOR=#333333]ssd 120gb samsung 840[/COLOR]
[COLOR=#333333]hdd 500gb wd scorpio black[/COLOR]
[COLOR=#333333]amd ati 7970m[/COLOR]
[/FONT][COLOR=#333333][FONT=HelveticaNeue-Light][FONT=arial]Bigfoot killer n 1202

Do you think it will work out of the box?
Do I need to do any particular configuration? Would there be any tutorial for this procedure?

Thank you for any tip and advice everyone![/FONT]
[/FONT][/COLOR]

---

### Post by 2F4U on 2013-05-10
It is not clear to me from your post if you want to keep Windows or completely replace it. What about the existing data? Would you create a backup and put it back after the installation? In general, a two-disk setup won't be performed automatically. You need to think about partitioning before attempting to install, much like you did with Windows.

---

### Post by ricak on 2013-05-10
> **2F4U said:**
> It is not clear to me from your post if you want to keep Windows or completely replace it. What about the existing data? Would you create a backup and put it back after the installation? In general, a two-disk setup won't be performed automatically. You need to think about partitioning before attempting to install, much like you did with Windows.


> **_[COLOR=#333333][FONT=arial]It will be just Ubuntu. No W, no dual boot.[/FONT][/COLOR]_**
"W" would stand for windows ;)

so No windows! No dual boot! Just Ubuntu!
I will delete windows completely... my documents and files that I want to keep I'll back them up in a pen or portable hdd

---

### Post by oldfred on 2013-05-10
With my 64GB SSD, it created two / (root) partitions. One current install and one for next install. I then have all data on rotating drive. 

I always partition in advance and now use gpt partitioning as Ubuntu will boot from gpt with either UEFI or BIOS. Only if installing Windows is the issue of Windows only boots from gpt with UEFI. 

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G   10G   17G  39% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           791M  1.1M  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  140K  2.0G   1% /run/shm
/dev/sdc2       100G   34G   67G  34% /mnt/shared
/dev/sdc6        97G   49G   43G  54% /mnt/data
/dev/sdd4        28G  4.8G   22G  19% /media/Quantal

```

I do not know about AMD, there was a while back an issue of support on the very new 7000 series cards from AMD's linux driver.
This may have changed:
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

---

