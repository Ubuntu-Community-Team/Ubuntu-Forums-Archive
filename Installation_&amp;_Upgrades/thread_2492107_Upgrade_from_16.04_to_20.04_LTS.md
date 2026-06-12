---
title: "Upgrade from 16.04 to 20.04 LTS"
date: 2023-10-30
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2023-10-30
I have  a multi device dual boot system with Ubuntu 16:04 and windows 10 (both in UEFI mode)
want to upgrade to 20:04 LTS keeping the below arch intact.

when i do *sudo apt upgrade* its asking me to first get uptodate on all the pending updates, and updates arent installing i guess since the 16:04 is not supported now.
whats the best way to go ahead.

```
abc@xyz:~$ sudo parted -ls
Model: ATA WDC WD2500AAKX-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ntfs


Model: ATA ST3500418AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA Samsung SSD 750 (scsi)
Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  117GB  117GB   primary   ext4            boot
 2      117GB   120GB  3477MB  extended
 5      117GB   120GB  3477MB  logical   linux-swap(v1)


Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  473MB   472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   578MB   105MB   fat32        EFI system partition          boot, esp
 3      578MB   595MB   16.8MB               Microsoft reserved partition  msftres
 4      595MB   105GB   104GB   ntfs         Basic data partition          msftdata
 5      105GB   1000GB  895GB   ntfs         Basic data partition          msftdata
```

---

### Post by Bashing-om on 2023-10-30
Agorichlyn9 ; Uh Huh

Yeah - the 16.04 repo no longer exist >> gotta go with the old-releases repo.
Please see:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
for the tutorial.
The path is from 16.04 to 18.04 and then finally to 20.04. A lot of bandwidth.

[INDENT]can be done[/INDENT]

---

### Post by Rubi1200 on 2023-10-30
You can, in theory, choose to upgrade from one LTS to the next and then again to the desired one. 

Be aware, though, that this may cause all kinds of problems. We have seen such upgrades go wrong many times here.

Best option? Backup all important data and do a fresh install of 22.04

---

### Post by MAFoElffen on 2023-10-30
But he needs to upgrade to the latest updates first (via the old-releases repo). Backup everything... Then attempt whatever path he chooses to take from there.

To make that far a jump, with the time and risk involved, a safer option wold be to "do a migration" directly to 20.04.

---

### Post by richlyn9 on 2023-10-31
Is my source list correct to go?

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) Xenial main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) Xenial-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) Xenial-security main restricted universe multiverse

---

### Post by Bashing-om on 2023-10-31
richlyn9

Looks good to me :D

---

### Post by guiverc on 2023-10-31
Be aware that [Ubuntu 16.04 is not EOL, only EOSS]("https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/").

That means *mirrors* are free to drop support, but the main archive is not yet moved to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)  (*if you look you'll note its not there*).

I *release-upgraded* a 16.04 (*xenial*) support system earlier this year, and for me I had to do nothing but use normal *release-upgrade* procedures, as [18.04 had not then reached its EOSS - it has now however]("https://fridge.ubuntu.com/2023/06/17/extended-security-maintenance-for-ubuntu-18-04-lts-began-on-may-31-2023/") (*I ensure I did it before end May 2023*).

It still may work for you, providing you've applied all security fixes. How easy this is for you, however can also vary on your *geolocation*. For me as of a few months ago, my machine certificates were still valid, however I've seen reports of others having problems because they needed newer certificates which were only available via upgrades if they applied ESM. Thus depending on where you are in the world, ESM maybe required (*release-upgrades are only supported to fully supported releases; 18.04 is no longer being in ESM as is 16.04; thus its supported if you have ESM enabled now; 18.04 to 20.04 doesn't require ESM as 20.04 isn't yet in ESM*)

The only reason I upgraded my 16.04 Desktop system via *release-upgrade*, was to prove it was still possible for a support question; however my intention with that install was to perform a *non-destructive* re-install of a supported release, as this can be done in a fraction of the time (*about 1/10th as long*), without loss of files, and in my case would have had all my *manually installed* applications auto-re-install too.  If you're talking about a Server system, a *non-destructive* re-install may not be possible (*you risk losing some server app configs!*); also too if you've loads of 3rd party packages (*esp. if packaged in a way that didn't consider the release-upgrade process in order to get the latest packages too*) some of those may need to be manually installed post-re-install.

---

### Post by richlyn9 on 2023-10-31
i was able to install security updates  without change the sources but there are others that are giving an error

```
abc@xyz:~$ sudo apt update
[sudo] password for xyz: 
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease [15.4 kB]
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Ign:3 http://download.opensuse.org/repositories/home:/selmf/xUbuntu_16.10  InRelease
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:5 http://in.archive.ubuntu.com/ubuntu xenial InRelease               
Err:6 http://download.opensuse.org/repositories/home:/selmf/xUbuntu_16.10  Release
  404  Not Found [IP: 195.135.221.134 80]
Hit:7 http://in.archive.ubuntu.com/ubuntu xenial-updates InRelease      
Hit:8 http://in.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:9 https://deb.torproject.org/torproject.org xenial InRelease [3,533 B]
Err:9 https://deb.torproject.org/torproject.org xenial InRelease
  The following signatures were invalid: KEYEXPIRED 1659680828  KEYEXPIRED 1659680828  KEYEXPIRED 1606112837  KEYEXPIRED 1606112837  KEYEXPIRED 1659680828  KEYEXPIRED 1659680828  KEYEXPIRED 1606112837  KEYEXPIRED 1659680828  KEYEXPIRED 1659680828  KEYEXPIRED 1606112837
Reading package lists... Done
E: The repository 'http://download.opensuse.org/repositories/home:/selmf/xUbuntu_16.10  Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://deb.torproject.org/torproject.org xenial InRelease: The following signatures were invalid: KEYEXPIRED 1659680828  KEYEXPIRED 1659680828  KEYEXPIRED 1606112837  KEYEXPIRED 1606112837  KEYEXPIRED 1659680828  KEYEXPIRED 1659680828  KEYEXPIRED 1606112837  KEYEXPIRED 1659680828  KEYEXPIRED 1659680828  KEYEXPIRED 1606112837
```

---

### Post by MAFoElffen on 2023-10-31
But those errors are all on PPA's and external repo's. You need to disable those anyways before a release upgrade...

If they do not update adding them back in after the release upgrade, then you try to reinstall those, just like normal, for any release upgrade.

I see those as another example of why you need to stay current on updates and supported release versions.

---

### Post by richlyn9 on 2023-10-31
I disabled the other software links and refreshed my system.
I got a pop up to upgrade from the software manager and went ahead

---

### Post by richlyn9 on 2023-10-31
16:04 to 18:04 done

i did get the below option

```
New version of configuration file /etc/default/grub is available, but the version installed currently has been locally modified
```

what specifics do i need to look in the comparison to make an nformed choice
if i choose the update managers version will it keep my system arch/config as same as mentioned in the first post?

---

### Post by yancek on 2023-10-31
With regard to the /etc/default/grub file, that may mean that os-prober is now disabled by default but I don't know for certain the reason for the message.  It indicates you or another user modified that file so make a backup of it and rename it if you decide you want it back.  Y

---

### Post by richlyn9 on 2023-10-31
Thanks all for your assistance in solving this I am now upgraded to 20:04 LTS

---

### Post by Bashing-om on 2023-10-31
richlyn9;

Yay .. You are now qualified :P

[INDENT]all in this, together [/INDENT]

---

