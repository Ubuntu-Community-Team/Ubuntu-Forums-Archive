---
title: "Trying to install 12.04LTS"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by brent1975 on 2013-01-07
I have been using ubuntu server edition for some time now and works really well for what I need it to do in the home. The other night I thought about it and decided to try and switch over my windows desktop to Ubuntu 12.04 and see how well I like the desktop version. I don't play many games on my rig anymore so thought I would take advantage of a speedier system and a little more freedom to do what I would like to my system. Well all was well I downloaded the 64bit vs and burned it to a cd rebooted my system and up came ubuntu start screen. The issue is when I get to the part where I have to choose a drive. It shows I dont have a drive at all. Something is weird about this. I went into windows and rand a check c: /f to make sure it was okay. I checked the bios for what ever reason to verify it was there... "clearly it was there I was able to boot into windows right? " So I have done a little digging on good ol google and appears that alot of folks are having the same issue....  my bios is up to date. I have switched my bios setting for the drive to AHCI or what ever it is and still the same effect. I have tried different versions of ubuntu and still the same result. and before anyone asks... I do not have a usb thumb drive. I have never had a need for 1 and I don't plan on buying one. I have never had these problems installing the server version of ubuntu so I am am confused as to the problem.

Currently I am running windows 7 64 Home Premium and starts and works fine. 

Any advice as to what I can try would be great.


Note:

I also ran sudo sfdisk -lus
Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 1953122303 1952915456   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
It appears ubuntu does see the two NTFS partitions.

[COLOR=Navy][/COLOR]

---

### Post by brent1975 on 2013-01-07
> **brent1975 said:**
> I have been using ubuntu server edition for some time now and works really well for what I need it to do in the home. The other night I thought about it and decided to try and switch over my windows desktop to Ubuntu 12.04 and see how well I like the desktop version. I don't play many games on my rig anymore so thought I would take advantage of a speedier system and a little more freedom to do what I would like to my system. Well all was well I downloaded the 64bit vs and burned it to a cd rebooted my system and up came ubuntu start screen. The issue is when I get to the part where I have to choose a drive. It shows I dont have a drive at all. Something is weird about this. I went into windows and rand a check c: /f to make sure it was okay. I checked the bios for what ever reason to verify it was there... "clearly it was there I was able to boot into windows right? " So I have done a little digging on good ol google and appears that alot of folks are having the same issue....  my bios is up to date. I have switched my bios setting for the drive to AHCI or what ever it is and still the same effect. I have tried different versions of ubuntu and still the same result. and before anyone asks... I do not have a usb thumb drive. I have never had a need for 1 and I don't plan on buying one. I have never had these problems installing the server version of ubuntu so I am am confused as to the problem.

Currently I am running windows 7 64 Home Premium and starts and works fine. 

Any advice as to what I can try would be great.


Note:

I also ran sudo sfdisk -lus
Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 1953122303 1952915456   7  HPFS/NTFS
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
It appears ubuntu does see the two NTFS partitions.



After doing some more reading on this i came across the fix.


```
sudo dmraid -E -r /dev/sda
```
```
sudo apt-get remove dmraid
```

---

