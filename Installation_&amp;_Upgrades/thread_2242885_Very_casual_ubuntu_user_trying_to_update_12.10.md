---
title: "Very casual ubuntu user trying to update 12.10"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by penkovlotrgw on 2014-09-04
hey guys I installed ubuntu and was happily using it for a while but have a dualboot with windows 7 and spend all my time on steam so i've been using that partition for about half a year or more. just came back to my ubuntu partition and my wifi stick wasnt working, so i plugged in ethernet and am now having problems installing updates, getting this message:

```

W:Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, W:Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

i'm not entirely sure what i did when i last left of ubuntu but it was working then. I had just installed gnome shells i think.

anyways thanks for any help you can give me

---

### Post by nerdtron on 2014-09-04
You didn't do anything wrong.
Ubuntu 12.10 has reached end-of-life and repositories for it are already closed. 
You need to upgrade to a newer version.

EDIT: None LTS (Long Term Support) releases like 12.10 are only supported for 18 months since it release. The current version 14.04 is supported for 5 years.

---

### Post by coffeecat on 2014-09-04
12.10 passed end-of-life in April 2014. The 12.10 repositories are closed which is why you are getting 404s.

It is theoretically possible to upgrade to the current supported 14.04, but it would mean upgrading via the also end-of-life 13.04 and 13.10 versions. Such a lengthy upgrade process would most likely end in tears, so the best advice has to be back up your data and make a fresh installation of the current 14.04.1, which is LTS (long-term support) and supported until April 2019.

---

### Post by grahammechanical on 2014-09-04
And remember, Ubuntu 12.10 was the last Interim release to get 18 months support. Ubuntu 13.04 and 13.10 only had 9 months support. Install 14.04.1 and do not upgrade to 15.04 and 15.10 because they also will only have 9 months support.

Regards

---

### Post by penkovlotrgw on 2014-09-04
if i have 2 partitions how do i go about installing 14.10? will wiping 12 and installing 14 immediately wipe windows 7 also? or will it just write 14 to the partition and leave the rest of the disk untouched.
 


also, why would my usb/wifi stick suddenly not work anymore? is that linked to the end of life support?

---

### Post by coffeecat on 2014-09-04
Do not install 14.10 - that is the current development version. You need to install 14.04, preferably the recent updated 14.04.1 point release.

Be careful with the 14.04 installer which in certain circumstances may erase your Windows installation, but I'll leave others to advise on this point as I have no recent experience of this. The best way in your case would be to use the "something else" option in the installer. Post details of your partition layout by posting the output of these two terminal commands and people will be able to help you further:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by penkovlotrgw on 2014-09-04
```
Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
240 heads, 63 sectors/track, 129201 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000247cf


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848  1339117567   669455360    7  HPFS/NTFS/exFAT
/dev/sda3      1339119614  1953521663   307201025    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5      1894932480  1953521663    29294592   82  Linux swap / Solaris
/dev/sda6      1339119616  1894932479   277906432   83  Linux



```


here it is. this is slightly off topic because its the reason i'm now looking to upgrade, but can i resolve my wireless problem (netgear ma111 card) or is it linked to the ended support and i should upgrade to regain functionality?

---

### Post by Dennis N on 2014-09-04
> **penkovlotrgw said:**
> if i have 2 partitions how do i go about installing 14.10? will wiping 12 and installing 14 immediately wipe windows 7 also? or will it just write 14 to the partition and leave the rest of the disk untouched...also, why would my usb/wifi stick suddenly not work anymore? is that linked to the end of life support?

On first "Installation type" page, select "something else". On next page, select the linux OS partition you want to replace (which must be sda6 from your last post), click the "change" button, choose "use as ext4 journalling file system", then choose mount point as /. Format partition = yes. 

This way, only sda6 will be used for your install. Windows stays. Bottom of same page: Grub should be installed to sda.

Continue the installation.
-----------------
Your wireless is not being affected by the system being out of support. Something else going on with that.

---

### Post by kansasnoob on 2014-09-04
> **penkovlotrgw said:**
> here it is. this is slightly off topic because its the reason i'm now looking to upgrade, but can i resolve my wireless problem (netgear ma111 card) or is it linked to the ended support and i should upgrade to regain functionality?

First things first, since you'll need to reinstall this is the installer bug you need to be aware of:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

IMHO the only ***safe*** way to use the installer ATM is to choose Something else as the installation option which will give you full control over what gets erased and what gets saved. Speaking of what gets saved, do you have anything in 12.10 that you want to save? If so speak now!

Second that last output looks like it may be truncated as "sudo parted -l" shows no partition info. Or it could be due to this error in what appears to be the output of "sudo fdisk -l":

> **[COLOR="#FF0000"]Partition 3 does not start on physical sector boundary.[/COLOR]**

We need to get to the bottom of that before doing anything else, although if you have nothing in 12.10 that you wish to save we could just delete all of the Ubuntu partitions and start over if Gparted will play along. But Gparted may not play along :(

Would you please post a screenshot of Gparted?

And also post the output of these commands from 12.10 using code tags:

```
sudo fdisk -lu
```

```
df -H
```

Then be a bit patient while one of us does some math ;)

---

### Post by penkovlotrgw on 2014-09-06
i can't post a screenshot because last time i was upstairs and plugged into the Ethernet as my netgear ma111 usb stick doesn't work (the real reason why i'm even think about upgrading os, to install the right drivers on the ruddy thing) its too much work at the moment to move the computer back upstairs. partition 3 might be 11 mbs that didnt make it into any of the other partitions. thats just a guess. really what i need is to get the usb stick working again and get internet, then change partions

---

