---
title: "Ubuntu Lucid-Maverick upgrade fails. What should I do?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by r.osmanov on 2011-02-14
Hi there! 

Some time ago I launched the upgrade, and it had been interrupted by a network error(ISP). That's what I've got in *sources.list*:

```
$ grep ^deb /etc/apt/sources.list
deb http://uz.archive.ubuntu.com/ubuntu/ maverick main restricted
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb http://uz.archive.ubuntu.com/ubuntu/ maverick universe
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb http://uz.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb http://archive.canonical.com/ubuntu maverick partner
deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://ubuntu.uz/ubuntu/ lucid main universe
deb http://security.ubuntu.com/ubuntu/ lucid-security universe main
deb http://ubuntu.uz/ubuntu/ lucid-updates universe main
```And now I cannot figure out what namely causes the error:
```
$ sudo do-release-upgrade 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool  
Done downloading            
extracting 'maverick.tar.gz'
authenticate 'maverick.tar.gz' against 'maverick.tar.gz.gpg' 
tar: Removing leading `/' from member names

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
WARNING: Failed to read mirror file
97% [Working] 
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

``````
$ sudo tail -n 20 /var/log/dist-upgrade/main.log
2011-02-14 09:23:51,318 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' is already set to new dist
2011-02-14 09:23:51,318 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse'
2011-02-14 09:23:51,319 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' is already set to new dist
2011-02-14 09:23:51,319 DEBUG examining: 'deb http://ubuntu.uz/ubuntu/ lucid main universe'
2011-02-14 09:23:51,321 DEBUG entry 'deb http://ubuntu.uz/ubuntu/ maverick main universe' updated to new dist
2011-02-14 09:23:51,321 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu/ lucid-security universe main'
2011-02-14 09:23:51,322 DEBUG entry 'deb http://security.ubuntu.com/ubuntu/ maverick-security universe main' updated to new dist
2011-02-14 09:23:51,322 DEBUG examining: 'deb http://ubuntu.uz/ubuntu/ lucid-updates universe main'
2011-02-14 09:23:51,324 DEBUG entry 'deb http://ubuntu.uz/ubuntu/ maverick-updates universe main' updated to new dist
2011-02-14 09:23:51,342 DEBUG running doUpdate() (showErrors=True)
2011-02-14 09:28:09,746 DEBUG openCache()
2011-02-14 09:28:09,747 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-02-14 09:28:13,069 DEBUG /openCache(), new cache size 32495
2011-02-14 09:28:13,070 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-02-14 09:29:14,500 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2011-02-14 09:29:14,500 DEBUG abort called
2011-02-14 09:29:14,503 DEBUG openCache()
2011-02-14 09:29:14,504 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-02-14 09:29:19,581 DEBUG /openCache(), new cache size 33703
2011-02-14 09:29:19,582 DEBUG enabling apt cron job
``````
$ sudo tail -n 20 /var/log/dist-upgrade/apt.log 
  Considering xserver-xorg-core 78 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 78 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 15
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 78 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
Log time: 2011-02-14 10:53:02.690378

```Well, I see that something wrong in xserver-xorg*. I tried 
```
$ sudo dpkg-reconfigure --force xserver-xorg
```But it does nothing.

Should I reinstall xserver-xorg, remove maverick deb entries from /etc/apt/sources.list, or do something else?

Regards.

---

### Post by zvacet on 2011-02-14
See if you have ubuntu-desktop package installed.If you don´t have it install it.It is meta package but you need it for upgrades.Open your source list and make lucid lines look like

#deb [http://ubuntu.uz/ubuntu/](http://ubuntu.uz/ubuntu/) lucid main universe
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main
#deb [http://ubuntu.uz/ubuntu/](http://ubuntu.uz/ubuntu/) lucid-updates universe main

or remove them.You can also try to switch to main server from Ubuntu software center>repositories>select main.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by kansasnoob on 2011-02-14
Please post the full output of these four commands:

```
ls /etc/apt
cat /etc/apt/sources.list
cat /etc/apt/sources.list.save
ls /var/log/dist-upgrade
```

---

### Post by kansasnoob on 2011-02-14
zvacet's post made me think of something. Is this a server system or a desktop system?

---

### Post by r.osmanov on 2011-02-14
> **zvacet said:**
> See if you have ubuntu-desktop package installed.If you don´t have it install it.It is meta package but you need it for upgrades.Open your source list and make lucid lines look like

#deb [http://ubuntu.uz/ubuntu/](http://ubuntu.uz/ubuntu/) lucid main universe
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security universe main
#deb [http://ubuntu.uz/ubuntu/](http://ubuntu.uz/ubuntu/) lucid-updates universe main

or remove them.You can also try to switch to main server from Ubuntu software center>repositories>select main.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

*ubuntu-desktop* package is installed. Well, I'd comment out Lucid entries from source list, update and upgrade all. 

I cannot do this right now... But I'll try this, and post here how it goes.

Thank you.

---

### Post by r.osmanov on 2011-02-14
> **kansasnoob said:**
> Please post the full output of these four commands:

```
ls /etc/apt
cat /etc/apt/sources.list
cat /etc/apt/sources.list.save
ls /var/log/dist-upgrade
```

> **kansasnoob said:**
> zvacet's post made me think of something. Is this a server system or a desktop system?

Thank you for the reply. 

Unfortunately, I cannot post all of these right now... But I've attached likely most significant logs from */var/log/dist-upgrade* in the post above. However, I'll do this, and post how it goes as soon, as I be back to the machine.

Regards.

EDIT: Almost forgot, it is a desktop system.

---

### Post by kansasnoob on 2011-02-14
I'm going to be unavailable for a while due to 10.04.2 upgrade testing, but just so anyone reading this knows what I was thinking:

Some of the info provided indicates that the upgrade process was interrupted early in the process. So I was thinking if "/etc/apt/sources.list.save" still looks all Lucid/10.04 then it would be best to rename the "sources.list" and copy the "sources.list.save" to replace it **[COLOR="Red"]something like this[/COLOR]**:

sudo mv /etc/apt/sources.list /etc/apt/sources.list_OLD
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list

Then, to purge the old .debs, update the cache, etc, run:

sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a

Then follow the correct procedure (depending on whether this is a server or desktop version of Ubuntu):

> To upgrade from Ubuntu 10.04 LTS on a desktop system, press Alt+F2 and type in "update-manager" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.10' is available. Click Upgrade and follow the on-screen instructions.

To upgrade from Ubuntu 10.04 LTS on a server system: install the update-manager-core package if it is not already installed; edit /etc/update-manager/release-upgrades and set Prompt=normal; launch the upgrade tool with the command sudo do-release-upgrade; and follow the on-screen instructions. 

Complete upgrade instructions here:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

NOTE: I highlighted "something like this" because this is largely guessing without more info.

---

### Post by kansasnoob on 2011-02-14
> **r.osmanov said:**
> Thank you for the reply. 

Unfortunately, I cannot post all of these right now... But I've attached likely most significant logs from */var/log/dist-upgrade* in the post above. However, I'll do this, and post how it goes as soon, as I be back to the machine.

Regards.

EDIT: Almost forgot, it is a desktop system.

I was posting while you were posting. I just had many interruptions.

I really need to complete some Hardy testing and then get on with this upgrade testing so it could be a while before you hear from me again.

---

### Post by r.osmanov on 2011-02-14
> **kansasnoob said:**
> Please post the full output of these four commands:

```
ls /etc/apt
cat /etc/apt/sources.list
cat /etc/apt/sources.list.save
ls /var/log/dist-upgrade
```

```
ruslan@mega-038: ~ $ ls /etc/apt
apt.conf.d                                              sources.list.save.before_restore_2009-10-09_09.50.00.577188
preferences.d                                           sources.list.save.before_restore_2009-10-09_12.55.23.581882
secring.gpg                                             sources.list.save.before_restore_2009-10-10_11.07.15.359468
sources.list                                            trustdb.gpg
sources.list~                                           trustdb.gpg.before_restore_2009-10-09_09.50.00.577188
sources.list.before_restore_2009-10-09_12.55.23.581882  trustdb.gpg.before_restore_2009-10-10_11.07.15.359468
sources.list.before_restore_2009-10-10_11.07.15.359468  trusted.gpg
sources.list.d                                          trusted.gpg~
sources.list.distUpgrade                                trusted.gpg.before_restore_2009-10-09_09.50.00.577188
sources.list.save                                       trusted.gpg.d
ruslan@mega-038: ~ $ cat /etc/apt/sources.list
# added by the release upgrader
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://uz.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://uz.archive.ubuntu.com/ubuntu/ maverick universe
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://uz.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://uz.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://uz.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
#VirtualBox
# deb http://download.virtualbox.org/virtualbox/debian karmic non-free # disabled on upgrade to karmic

#deb http://ubuntu.uz/ubuntu/ lucid main universe
#deb http://security.ubuntu.com/ubuntu/ lucid-security universe main
#deb http://ubuntu.uz/ubuntu/ lucid-updates universe main
ruslan@mega-038: ~ $ cat /etc/apt/sources.list.save
# added by the release upgrader
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100427.1)]/ lucid main restricted
# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://uz.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://uz.archive.ubuntu.com/ubuntu/ maverick universe
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://uz.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://uz.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://uz.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://uz.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
# deb http://security.ubuntu.com/ubuntu maverick-security multiverse
#VirtualBox
# deb http://download.virtualbox.org/virtualbox/debian karmic non-free # disabled on upgrade to karmic

deb http://ubuntu.uz/ubuntu/ lucid main universe
deb http://security.ubuntu.com/ubuntu/ lucid-security universe main
deb http://ubuntu.uz/ubuntu/ lucid-updates universe main
ruslan@mega-038: ~ $ ls /var/log/dist-upgrade
20091009-1001  20101101-1418  20110201-0920  20110205-1010  20110214-0853  20110214-1051  lspci.txt         system_state.tar.gz
20091231-0920  20101103-0956  20110204-1629  20110212-1130  20110214-0901  20110214-1052  main.log
20100511-0834  20101111-1615  20110204-1631  20110214-0821  20110214-0923  apt.log        main.log.partial

```

---

### Post by r.osmanov on 2011-02-14
> **kansasnoob said:**
> ...
sudo mv /etc/apt/sources.list /etc/apt/sources.list_OLD
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list

Then, to purge the old .debs, update the cache, etc, run:

sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a

Then follow the correct procedure (depending on whether this is a server or desktop version of Ubuntu)...

After the first two commands /etc/apt/sources.list still contained both lucid and maverick sources. I replaced all "maverick" words by "lucid" and removed duplicates from the file. 
The next commands have cleaned debs and made the system look like Lucid. 

I've updated & upgraded Lucid packages successfully. In Update Manager everything is clean, and "Upgrade" button suggests to upgrade to Maverick. Pressing the button results the same message:
[INDENT]Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
[/INDENT]I post output of commands:
```
ls /etc/apt
cat /etc/apt/sources.list
cat /etc/apt/sources.list.save
ls /var/log/dist-upgrade
```
in [upgrade.txt]("http://ubuntuforums.org/attachment.php?attachmentid=183511&stc=1&d=1297744239").

---

### Post by kansasnoob on 2011-02-15
I'll be busy for a few hours yet, just wanted to let you know you're not forgotten. I would like to get a better look at your overall installation so if you'd be so kind please post the output of the following:

```
df -H
```

```
sudo parted -l
```

BTW that's intentionally a capital H, and that's a lower case L at the end of the latter command.

I need to more closely parse your existing sources.list but I notice the "uz" locale, where is "uz"? I'm wondering if there might be a problem with that particular server.

---

### Post by r.osmanov on 2011-02-15
> **kansasnoob said:**
> I'll be busy for a few hours yet, just wanted to let you know you're not forgotten. I would like to get a better look at your overall installation so if you'd be so kind please post the output of the following:

```
df -H
``````
sudo parted -l
```BTW that's intentionally a capital H, and that's a lower case L at the end of the latter command.

I need to more closely parse your existing sources.list but I notice the "uz" locale, where is "uz"? I'm wondering if there might be a problem with that particular server.

kansasnoob, thank you for helping me. 
```
ruslan@mega-038: ~ $ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb8               68G    21G    44G  32% /
none                   1.1G   300k   1.1G   1% /dev
none                   1.1G   259k   1.1G   1% /dev/shm
none                   1.1G   373k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda1               40G   8.0G    30G  22% /backup
/dev/sdb6              3.0G    98M   2.8G   4% /tmp
/dev/sdb5              293M    87M   192M  32% /boot
/dev/sdb7               37G    14G    21G  41% /home
ruslan@mega-038: ~ $ sudo parted -l
Model: ATA WDC WD800BB-55JH (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.0GB  40.0GB  primary  ext4


Model: ATA SAMSUNG HD161HJ (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 2      32.3kB  160GB   160GB   extended
10      96.8kB  1439MB  1439MB  logical   linux-swap(v1)
 5      1439MB  1752MB  313MB   logical   ext2            boot
 6      32.0GB  35.0GB  3002MB  logical   ext3
 7      35.0GB  72.1GB  37.1GB  logical   ext3
 8      87.0GB  156GB   68.5GB  logical   ext3
 9      156GB   160GB   4499MB  logical   linux-swap(v1)
```

"uz" is.. Uzbekistan:) But it is just a mirror. Do you suggest to switch to another, e.g. main, server? How do I make it from command line(I'm currently on another machine, and connect there via SSH)?

---

### Post by kansasnoob on 2011-02-15
> **r.osmanov said:**
> kansasnoob, thank you for helping me. 
```
ruslan@mega-038: ~ $ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb8               68G    21G    44G  32% /
none                   1.1G   300k   1.1G   1% /dev
none                   1.1G   259k   1.1G   1% /dev/shm
none                   1.1G   373k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda1               40G   8.0G    30G  22% /backup
/dev/sdb6              3.0G    98M   2.8G   4% /tmp
/dev/sdb5              293M    87M   192M  32% /boot
/dev/sdb7               37G    14G    21G  41% /home
ruslan@mega-038: ~ $ sudo parted -l
Model: ATA WDC WD800BB-55JH (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.0GB  40.0GB  primary  ext4


Model: ATA SAMSUNG HD161HJ (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 2      32.3kB  160GB   160GB   extended
10      96.8kB  1439MB  1439MB  logical   linux-swap(v1)
 5      1439MB  1752MB  313MB   logical   ext2            boot
 6      32.0GB  35.0GB  3002MB  logical   ext3
 7      35.0GB  72.1GB  37.1GB  logical   ext3
 8      87.0GB  156GB   68.5GB  logical   ext3
 9      156GB   160GB   4499MB  logical   linux-swap(v1)
```

"uz" is.. Uzbekistan:) But it is just a mirror. Do you suggest to switch to another, e.g. main, server? How do I make it from command line(I'm currently on another machine, and connect there via SSH)?

Give me a bit, I don't care where you live. I'm just thinking that changing mirrors might help but I still need to parse that sources.list :D

Also, when the upgrade process is interrupted things get crazy. That is, even if I provided you a replacement Maverick sources.list and you ran "apt-get dist-upgrade" you would be more likely to encounter problems.

That and I can see this is a hi-mileage install, looks like it's been upgraded since at least Jaunty. Please be patient and I'll get back to this ASAP.

---

### Post by r.osmanov on 2011-02-16
Changed mirror to [http://ftp.chg.ru](http://ftp.chg.ru)
Still the same issue. 

One guy suggested making two separate systems with a common /home partition, and flip-flop between them each upgrade. But this idea doesn't appeal to me.

---

### Post by kansasnoob on 2011-02-16
> **r.osmanov said:**
> Changed mirror to [http://ftp.chg.ru](http://ftp.chg.ru)
Still the same issue. 

One guy suggested making two separate systems with a common /home partition, and flip-flop between them each upgrade. But this idea doesn't appeal to me.

You don't really need to share a /home to transfer data from one OS to another. That's why I asked for some of the info I did.

I wonder why you can only access this box via ssh?

And if Lucid is working well why upgrade to Maverick?

Regardless the upgrade mechanism does a lot of things besides upgrading packages so I'd be reluctant to just replace the Maverick sources.list with another. I think it would be safer to replace the sources.list with a Lucid sources.list, where it's using the main server, and then running "apt-get clean" again. Then start the upgrade process properly again.

Regardless here's a Maverick default sources.list using the main server:

```
lance@lance-desktop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb-src http://archive.canonical.com/ubuntu maverick partner

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
lance@lance-desktop:~$ 

```

---

### Post by r.osmanov on 2011-02-17
Got it :D
Replaced sources.list by the default one(for Maverick) and made:
```
$ sudo apt-get clean
$ sudo apt-get autoremove
$ sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Than you!

---

