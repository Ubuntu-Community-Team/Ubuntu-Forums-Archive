---
title: "(xubuntu) Help solving package problem please"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by gregg3 on 2016-04-26
Newbie here. I recently upgraded from Xubuntu 15.10 to Xubuntu 16.04. After the upgrade the computer takes at least 40 minutes to come on. I got an error message telling me to run apt-get so I ran ```
apt-get update
``` (_not_ ```
sudo apt-get update
```). This is what it showed:

```
gregg@LG:~/Desktop$ apt-get update
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
gregg@LG:~/Desktop$
``` 

That is all I did. I did not answer the 'are you root?' question or run ```
sudo apt-get update
``` . Trying to find a solution I found all these apt-get commands (see screenshot) but honestly I don't know which one of them to use or if I should use any of them at all or if this problem requires an entirely different solution.

Any help will be greatly appreciated. (Even if I have to do a fresh install or whatever.)  Thank you.

---

### Post by kansasnoob on 2016-04-26
To run apt you must be root, so you need to use sudo :)

---

### Post by Bashing-om on 2016-04-26
gregg3; Hello :

Ninja'd ^^. You are making a system change, and "you" as the system administrator must authorize the changes.

If problems persist, post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

You should boot up on a matter of seconds .. 
Once you are fully updated .. then
[INDENT][INDENT]we start looking for where the problem lies
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-26
> **kansasnoob said:**
> To run apt you must be root, so you need to use sudo :)

Thanks Kansas.

---

### Post by gregg3 on 2016-04-26
> **Bashing-om said:**
> gregg3; Hello :

Ninja'd ^^. You are making a system change, and "you" as the system administrator must authorize the changes.

If problems persist, post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

You should boot up on a matter of seconds .. 
Once you are fully updated .. then[INDENT][INDENT]we start looking for where the problem lies
[/INDENT]
[/INDENT]


Thanks Bashing-om. Somebody told me to run the apt-get versions of those commands and from what I can gather the commands are similar enough so that the results should give you an idea of what's going on. And in the sudo apt-get update one I ran the command twice. Once before a software update and then I ran the software update and then ran the sudo apt-get update again.

```
gregg@LG:~/Desktop$ sudo apt-get update
[sudo] password for gregg: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [92.2 kB]   
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [92.2 kB]    
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [3,416 B]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [920 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [5,400 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [5,404 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [2,828 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [3,796 B]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [3,792 B]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [2,788 B]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [1,612 B]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Sources [920 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [2,920 B]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [2,924 B]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [1,288 B]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [188 B]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [1,584 B]
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [1,588 B]
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [1,080 B]
Get:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [190 B]
Fetched 227 kB in 1s (159 kB/s)     
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
gregg@LG:~/Desktop$ sudo apt-get update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease               
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease       
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Reading package lists... Done                      
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
gregg@LG:~/Desktop$
```

Then I ran sudo apt-get upgrade and got this:

```
gregg@LG:~/Desktop$ sudo apt-get upgrade
[sudo] password for gregg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libapt-inst1.7 libapt-pkg4.16 libboost-regex1.58.0 libcdaudio1 libenca0
  libept1.4.16 libgtop2-10 libidl-2-0 libisl13 libkf5waylandserver5
  libkwineffects7 libkwinglutils6 libkwinxrenderutils6 libkwinxrenderutils7
  libllvm3.5v5 liborbit2 libpgm-5.1-0 libslv2-9 libsoundtouch0 libvpx2
  linux-headers-4.2.0-30 linux-headers-4.2.0-34 python-gnome2 python-pyorbit
  python3-ply
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gregg@LG:~/Desktop$
```

Can you tell from the data if this solves my problem? Or is there something else I need to do? And btw I will run the commands again without the "get" if that is imperative. Thanks for the help!

---

### Post by Bashing-om on 2016-04-26
gregg3; Hey ...

So far, so good .
Looks good .. the google-chrome warning you can ignore .. 
see: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331)

As to 'apt' does it also return the same warning ?
'apt' is the new updated 'apt-get' .
what now returns:
```

sudo apt update
sudo apt full-upgrade
sudp apt -f install
sudo dpkg -C

```

Maybe now we can reboot the system and see about that boot delay ??

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-26
> **Bashing-om said:**
> gregg3; Hey ...

So far, so good .
Looks good .. the google-chrome warning you can ignore .. 
see: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331)

As to 'apt' does it also return the same warning ?
'apt' is the new updated 'apt-get' .
what now returns:
```

sudo apt update
sudo apt full-upgrade
sudp apt -f install
sudo dpkg -C

```

Maybe now we can reboot the system and see about that boot delay ??[INDENT][INDENT]hey it could happen
[/INDENT]
[/INDENT]

Here's the sudo apt update:
```

gregg@LG:~/Desktop$ sudo apt update
[sudo] password for gregg: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [92.2 kB]   
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease    
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [92.2 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [5,400 B]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [5,404 B]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [3,796 B]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [3,792 B]
Fetched 203 kB in 0s (207 kB/s)                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
gregg@LG:~/Desktop$ 
```

Here's the sudo apt full-upgrade:

```
gregg@LG:~/Desktop$ sudo apt full-upgrade
[sudo] password for gregg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gregg@LG:~/Desktop$ 
```

That sounds like it's all good. Do you think I need to run those last two commands you suggested? And sudo apt -f install I've heard of but not sudo dpkg -C. Is the latter the same as:
sudo dpkg --configure -a  ?

Thanks!

---

### Post by Bashing-om on 2016-04-26
gregg3; Yeah ...

For peace of mind :
```

sudo apt -f install
sudo dpkg -C

```
see:
```

man dpkg

```
where "apt -f" will look for broken packages and attempt to fix.
where in dpkg the -c option "  Searches for packages that have been installed only partially on your  system. dpkg will suggest what to do with them to get them working."

I do not expect there to be anything to fix .. ( apt would have said so ) ; just cheap insurance for " peace of mind" .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-26
> **Bashing-om said:**
> gregg3; Yeah ...

For peace of mind :
```

sudo apt -f install
sudo dpkg -C

```
see:
```

man dpkg

```
where "apt -f" will look for broken packages and attempt to fix.
where in dpkg the -c option "  Searches for packages that have been installed only partially on your  system. dpkg will suggest what to do with them to get them working."

I do not expect there to be anything to fix .. ( apt would have said so ) ; just cheap insurance for " peace of mind" .[INDENT][INDENT]together we can
[/INDENT]
[/INDENT]


Okay, man. (Thanks a lot for the explanations.)

Here are the results of those commands:

```
gregg@LG:~/Desktop$ sudo apt -f install
[sudo] password for gregg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gregg@LG:~/Desktop$ sudo dpkg -C
gregg@LG:~/Desktop$ 
```

Ha ha. Read about that -C command in man dpkg. 

```
Performs  database  sanity and consistency checks 
```

(I could use one of those sanity checks myself!)

Well, thanks. So this is looking good, right? Anything left to do?

---

### Post by Bashing-om on 2016-04-26
gregg3l Hey, hey ..

Look'n good .....

Reboot and let's see how things-a-look'n .

[INDENT][INDENT]so far so nice
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-27
> **Bashing-om said:**
> gregg3l Hey, hey ..

Look'n good .....

Reboot and let's see how things-a-look'n .[INDENT][INDENT]so far so nice
[/INDENT]
[/INDENT]


Okay. Thanks. I did the reboot. The Xubuntu screen came on and stayed on for three or four minutes (it's usually on only a few seconds during a typical reboot). So a lot was happening. The screen with the RAM info came up. Then "Operating System is loading." But then the screen went blank and a window came on saying there was 'no input' and the screen (monitor) went to sleep. I waited around five minutes and nothing. I mean, the computer was on but the monitor was getting no input signal. The first time I did restarts it took roughly 40 minutes for the computer to come back on, but this time it came on in less than 15 minutes. So progress! 

I keep wondering if that original warning message about the cache and a file missing has anything to do with it. (see attachment)

Anyway I'll (it's my work computer) turn the computer on tomorrow morning and report back.

Thanks so much for the help. I really appreciate it.

---

### Post by gregg3 on 2016-04-27
Okay. It's the next morning. Started the computer and nothing much changed that I can tell. It started booting up. The RAM info etc. Then it said: Loading Operating System. And the last thing it showed was 'boot from CD/DVD.' 

I thought the latter might have something to do with the delay becuase it was trying to boot from the CD/DVD tray, but the CD/DVD tray never lit up, and even if the boot sequence in the BIOS were set to boot from the CD/DVD tray first it would very quickly jump to boot from the hard drive.

So, yeah, nothing on the monitor after 'boot from CD/DVD' except "No Input Signal." And I watched the monitor for 15 minutes and the computer did not come on. Then I had to go out and came back in after another 15 minutes and the computer was on. So it came on between 15 and 30 minutes.

I can only think of two things:

1) That missing cache file I mentioned in my last post 
2) It's the bug people are saying came along with the upgrade from 15.10 to 16.04LTS

Any ideas on how to proceed or maybe I should just be patient (and do nothing) and see if they fix the bug?

Thanks.

---

### Post by Bashing-om on 2016-04-27
gregg3; Hey ...

A lot of the delay appears to be in Bios .. How comfortable are you messing about in bios ?

Now we want to know that the release upgrade completed:
```

lsb_release -a
cat /proc/version
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

The parsing error appears to be a corrupted package management control file .. that is easily repaired:
Once rebooted .. run:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt full-upgrade

```


Next after a fresh new reboot is to look at at how the boot is configured:
```

cat /boot/grub/grub.cfg

```

You should boot in a matter of seconds ....
[INDENT][INDENT]we look'n to find
[INDENT][INDENT][INDENT][INDENT]why not
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-27
Okay, my friend. (Thank you!) I'm going to do these one batch at at time.

For:

```
lsb_release -a
cat /proc/version
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
``````


gregg@LG:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
gregg@LG:~/Desktop$ cat /proc/version
Linux version 4.4.0-21-generic (buildd@lgw01-21) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016
gregg@LG:~/Desktop$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Xubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    41    deb http://security.ubuntu.com/ubuntu xenial-security universe
    42    deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    43    deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu utopic partner
    51    # deb-src http://archive.canonical.com/ubuntu utopic partner
    52    
gregg@LG:~/Desktop$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/bit-team-ubuntu-stable-vivid.list <==
# deb http://ppa.launchpad.net/bit-team/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/bit-team/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/bit-team-ubuntu-stable-vivid.list.distUpgrade <==
# deb http://ppa.launchpad.net/bit-team/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/bit-team/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/bit-team-ubuntu-stable-vivid.list.save <==
# deb http://ppa.launchpad.net/bit-team/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/bit-team/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main 

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/megasync.list <==
# deb http://mega.nz/linux/MEGAsync/xUbuntu_15.10/ ./ # disabled on upgrade to xenial

==> /etc/apt/sources.list.d/megasync.list.distUpgrade <==
deb http://mega.nz/linux/MEGAsync/xUbuntu_15.10/ ./

==> /etc/apt/sources.list.d/megasync.list.save <==
deb http://mega.nz/linux/MEGAsync/xUbuntu_15.10/ ./

==> /etc/apt/sources.list.d/mkusb-ubuntu-ppa-wily.list <==
# deb http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial main # disabled on upgrade to xenial
# deb-src http://ppa.launchpad.net/mkusb/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/mkusb-ubuntu-ppa-wily.list.distUpgrade <==
deb http://ppa.launchpad.net/mkusb/ppa/ubuntu wily main
# deb-src http://ppa.launchpad.net/mkusb/ppa/ubuntu wily main

==> /etc/apt/sources.list.d/paolorotolo-ubuntu-copy-utopic.list <==
# deb http://ppa.launchpad.net/paolorotolo/copy/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/paolorotolo/copy/ubuntu utopic main

==> /etc/apt/sources.list.d/paolorotolo-ubuntu-copy-utopic.list.distUpgrade <==
# deb http://ppa.launchpad.net/paolorotolo/copy/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/paolorotolo/copy/ubuntu utopic main

==> /etc/apt/sources.list.d/paolorotolo-ubuntu-copy-utopic.list.save <==
# deb http://ppa.launchpad.net/paolorotolo/copy/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/paolorotolo/copy/ubuntu utopic main

==> /etc/apt/sources.list.d/steam.list <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily

==> /etc/apt/sources.list.d/steam.list.distUpgrade <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily

==> /etc/apt/sources.list.d/steam.list.save <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
gregg@LG:~/Desktop$ 
```

Now remember it takes 15-30 minutes to reboot, so, *hopefully*, I'll be back then with the next batch.

---

### Post by gregg3 on 2016-04-27
Round Two. These guys:

```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt full-upgrade
```

The results:```


gregg@LG:~/Desktop$ sudo rm -fr /var/lib/apt/lists
[sudo] password for gregg: 
gregg@LG:~/Desktop$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory '/var/lib/apt/lists'
mkdir: created directory '/var/lib/apt/lists/partial'
gregg@LG:~/Desktop$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                  
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [92.2 kB]   
Get:4 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]                      
Get:5 http://dl.google.com/linux/chrome/deb stable Release.gpg [916 B]                                
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [93.3 kB]                         
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [82.2 kB]
Get:8 http://dl.google.com/linux/chrome/deb stable/main amd64 Packages [1,335 B]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial/main Sources [868 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main Sources [4,932 B]  
Get:11 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources [64 B]          
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [920 B]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources [64 B]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [25.8 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [25.8 kB]                      
Get:16 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [8,356 B]                     
Get:17 http://us.archive.ubuntu.com/ubuntu xenial/restricted Sources [4,808 B]                                   
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [188 B]                      
Get:19 http://us.archive.ubuntu.com/ubuntu xenial/universe Sources [7,728 kB]                                    
Get:20 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [64 B]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/restricted i386 Packages [64 B]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [64 B]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [158 B]         
Get:24 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [3,932 B]      
Get:25 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [3,920 B]
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [2,328 B] 
Get:27 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [190 B]
Get:28 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [64 B]
Get:29 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [64 B]
Get:30 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [64 B]
Get:31 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [159 B]
Get:32 http://us.archive.ubuntu.com/ubuntu xenial/multiverse Sources [179 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1,201 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1,196 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]                                                                                                 
Get:38 http://us.archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [8,344 B]                                                                                              
Get:39 http://us.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8,684 B]                                                                                               
Get:40 http://us.archive.ubuntu.com/ubuntu xenial/restricted Translation-en [2,908 B]                                                                                              
Get:41 http://us.archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]                                                                                         
Get:42 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,532 kB]                                                                                               
Get:43 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7,512 kB]                                                                                                
Get:44 http://us.archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,354 kB]                                                                                               
Get:45 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3,410 kB]                                                                                        
Get:46 http://us.archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7,448 kB]                                                                                           
Get:47 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [144 kB]                                                                                               
Get:48 http://us.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                                                                
Get:49 http://us.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                                                               
Get:50 http://us.archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]                                                                                       
Get:51 http://us.archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                                                           
Get:52 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Sources [8,968 B]                                                                                                   
Get:53 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted Sources [64 B]                                                                                                
Get:54 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [920 B]                                                                                                 
Get:55 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse Sources [64 B]                                                                                                
Get:56 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [31.3 kB]                                                                                            
Get:57 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [31.3 kB]                                                                                             
Get:58 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [11.5 kB]                                                                                            
Get:59 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [5,487 B]                                                                                     
Get:60 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [4,408 B]                                                                                        
Get:61 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [64 B]                                                                                         
Get:62 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages [64 B]                                                                                          
Get:63 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [64 B]                                                                                         
Get:64 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                                                                                 
Get:65 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [7,500 B]                                                                                        
Get:66 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [7,500 B]                                                                                         
Get:67 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [4,988 B]                                                                                        
Get:68 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [157 B]                                                                                   
Get:69 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [64 B]                                                                                         
Get:70 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [64 B]                                                                                          
Get:71 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [64 B]                                                                                         
Get:72 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [158 B]                                                                                 
Get:73 http://us.archive.ubuntu.com/ubuntu xenial-backports/main Sources [28 B]                                                                                                    
Get:74 http://us.archive.ubuntu.com/ubuntu xenial-backports/restricted Sources [28 B]                                                                                              
Get:75 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe Sources [28 B]                                                                                                
Get:76 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse Sources [28 B]                                                                                              
Get:77 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [28 B]                                                                                             
Get:78 http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [28 B]                                                                                              
Get:79 http://us.archive.ubuntu.com/ubuntu xenial-backports/main Translation-en [28 B]                                                                                             
Get:80 http://us.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages [28 B]                                                                                       
Get:81 http://us.archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages [28 B]                                                                                        
Get:82 http://us.archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en [28 B]                                                                                       
Get:83 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages [28 B]                                                                                         
Get:84 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages [28 B]                                                                                          
Get:85 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en [28 B]                                                                                         
Get:86 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 Packages [28 B]                                                                                       
Get:87 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse i386 Packages [28 B]                                                                                        
Get:88 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en [28 B]                                                                                       
Fetched 44.6 MB in 19s (2,253 kB/s)                                                                                                                                                
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: There is no public key available for the following key IDs:
1397BC53640DB551
gregg@LG:~/Desktop$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  thunderbird thunderbird-locale-en thunderbird-locale-en-us
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.7 MB of archives.
After this operation, 11.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 thunderbird-locale-en amd64 1:38.7.2+build1-0ubuntu0.16.04.1 [350 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 thunderbird amd64 1:38.7.2+build1-0ubuntu0.16.04.1 [33.3 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 thunderbird-locale-en-us all 1:38.7.2+build1-0ubuntu0.16.04.1 [10.1 kB]                                        
Fetched 33.7 MB in 15s (2,150 kB/s)                                                                                                                                                
(Reading database ... 259477 files and directories currently installed.)
Preparing to unpack .../thunderbird-locale-en_1%3a38.7.2+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Preparing to unpack .../thunderbird_1%3a38.7.2+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a38.7.2+build1-0ubuntu0.16.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:38.7.2+build1-0ubuntu0.16.04.1) over (1:38.6.0+build1-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up thunderbird (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en (1:38.7.2+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en-us (1:38.7.2+build1-0ubuntu0.16.04.1) ...
gregg@LG:~/Desktop$ 
```


I should be back in 15-30 minutes with the final batch.

---

### Post by Bashing-om on 2016-04-27
gregg3; Hey,

Looking Good ..
You may want to spend some time in further investigating the 3rd party PPAs. Nothing I see is interfering with the system and these are commented out . When/IF you find they are supported in 16.04 you may choose to enable them.
" # deb [http://mega.nz/linux/MEGAsync/xUbuntu_15.10/](http://mega.nz/linux/MEGAsync/xUbuntu_15.10/) ./ " is valid in xenial (16.04) /

so far
[INDENT][INDENT]sooo good
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-28
Hi Bashing-om.

This last reboot took a full hour for the computer to come back on. (I must admit I got a little nervous.)

Okay. I ran the cat /boot/grub/grub.cfg command and this is what it brought up:

```
gregg@LG:~/Desktop$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
else
  search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
gregg@LG:~/Desktop$ 
```

And I, of course, have no idea what that means. LOL. Thanks for the help!

---

### Post by gregg3 on 2016-04-28
> **Bashing-om said:**
> gregg3; Hey,

Looking Good ..
You may want to spend some time in further investigating the 3rd party PPAs. Nothing I see is interfering with the system and these are commented out . When/IF you find they are supported in 16.04 you may choose to enable them.
" # deb [http://mega.nz/linux/MEGAsync/xUbuntu_15.10/](http://mega.nz/linux/MEGAsync/xUbuntu_15.10/) ./ " is valid in xenial (16.04) /

so far[INDENT][INDENT]sooo good
[/INDENT]
[/INDENT]


Thanks Bashing-om, but I'm not sure I follow. I mean, I get the 'further investigating PPAs part' but the rest, the 'commented out' and 'if they are supported' and the mega link in quotes, honestly, that's all over my head. I do have Mega on two computers sycning and it's worked fairly well, but that's about all I can tell you.

Anyway, going to call it a night here, so I'm shutting this computer down and will check back in in the morning with how the start-up went. Have a good night. (And thanks for all the help and hanging with me on this!)

---

### Post by Bashing-om on 2016-04-28
gregg3; Welp ;

Again, In a quick look, I see nothing miss . 
verify UUIDs and partitions:
```

sudo blkid
sudo parted -l

```

Looks as if we are getting close to reading the logs. 

There is a small matter of google's signing key .. but that has nothing to do with the boot delay.
It is late here my time. I am done for this session. I will catch up with you tomorrow.

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read the instructions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-28
> **Bashing-om said:**
> gregg3; Welp ;

Again, In a quick look, I see nothing miss . 
verify UUIDs and partitions:
```

sudo blkid
sudo parted -l

```

Looks as if we are getting close to reading the logs. 

There is a small matter of google's signing key .. but that has nothing to do with the boot delay.
It is late here my time. I am done for this session. I will catch up with you tomorrow.[INDENT][INDENT]when all else fails[INDENT][INDENT][INDENT]read the instructions
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hey Bashing-om.

I turned the computer on and it started to boot up. Showed the DDR3 RAM stuff. Then it showed a blank, but textured, gray screen, which I'd never seen before. Then it went blank and the "No input signal" window came on. Now it's been an hour and fifteen minutes and still nothing. 

Hmm. It had been booting up in the 15-30 minute range. Then I did that latest batch of commands (including the full upgrade) and then the reboot  I did after that took 1 hour, and now this start-up is at 1 hour 15 minutes. 

I was unable to run those latest commands because the computer is not on. 

One thing I noticed. When I shut the computer off, rather than doing it's gradual shutdown, it just shuts off within two seconds. I just figured I'd mention that.

Just checked it again (I'm on a different computer now) and still nothing.

I'm going to go out for an hour or so. I'll see if it's on when I get back and post. Thanks.

---

### Post by Bashing-om on 2016-04-28
gregg3; Ouch !

Hardware issues ? Presently difficult to determine what is not taking place .
Let's try this in small steps to attempt to isolate.
Can you quickly boot to the grub boot menu ? We want to rule out a ram or bios issue. -
When booting depress and hold a shift key as soon as the bios screen clears . -> Grub boot menu,
IF an EFI system .. it is the escape key that grub looks for - when the firmware screen clears spam the escape key . only a 3 second window of opportunity.
When you are able to boot to grub .. we set the system to boot to single user mode ( booting to a terminal rather than a GUI ) .

In the grub menu choose the latest kernel to boot , and press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line starting with linux ... and across to "quiet splash" . Delete these terms and ALL after .. and insert : " systemd.unit=multi-user.target " - without the quotes . key combo ctl+x to continue the boot process to terminal (TTY1) .. log in here with your credentials .. when pass word is entered there will be no response to the screen - enter password blindly and hit the enter key.

From here we can work without the overhead of a GUI ( that X layer on top of the kernel) .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-28
> **Bashing-om said:**
> gregg3; Ouch !

Hardware issues ? Presently difficult to determine what is not taking place .
Let's try this in small steps to attempt to isolate.
Can you quickly boot to the grub boot menu ? We want to rule out a ram or bios issue. -
When booting depress and hold a shift key as soon as the bios screen clears . -> Grub boot menu,
IF an EFI system .. it is the escape key that grub looks for - when the firmware screen clears spam the escape key . only a 3 second window of opportunity.
When you are able to boot to grub .. we set the system to boot to single user mode ( booting to a terminal rather than a GUI ) .

In the grub menu choose the latest kernel to boot , and press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line starting with linux ... and across to "quiet splash" . Delete these terms and ALL after .. and insert : " systemd.unit=multi-user.target " - without the quotes . key combo ctl+x to continue the boot process to terminal (TTY1) .. log in here with your credentials .. when pass word is entered there will be no response to the screen - enter password blindly and hit the enter key.

From here we can work without the overhead of a GUI ( that X layer on top of the kernel) .[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


Hi. I wouldn't think it was hardware issues because the computer is just a couple of years old and was working perfectly before the upgrade and is working perfectly now. (But of course it's possible.)

Anyway, the computer came back on. So some time between 1 hour and 15 minutes and 3 hours. (Now, while I was sitting here--during the hour and 15 minute stretch--I would every once in a while roll the mouse a bit to see if the screen showed anything. It seems that when I leave the mouse alone for long stretches, the computer is more likely to come on. I don't know. That might be a head game but I figured I'd mention it.) 

And forgive me if I'm being repetitive but I'm still somewhat thinking of that error message. (the attachment again) They were saying a file related to the cache is missing. And the little I know of the cache is that it speeds things up. Plus they are telling us that that is most likely what the problem is.

So, since the computer is on I decided to run the results of those commands you mentioned in your second to last post first. Here are the results. (I'll wait before I hear from you before I attempt any of what's in your last post.) Thanks.
```

gregg@LG:~/Desktop$ sudo blkid
[sudo] password for gregg: 
/dev/sda1: UUID="da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8" TYPE="ext4" PARTUUID="7f02422e-01"
/dev/sda5: UUID="db4c32d5-1b25-498b-8f6b-5ea2cfa69ce2" TYPE="swap" PARTUUID="7f02422e-05"
gregg@LG:~/Desktop$ sudo parted -l
Model: ATA WDC WD800JD-75MS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  76.2GB  76.2GB  primary   ext4            boot
 2      76.2GB  80.0GB  3754MB  extended
 5      76.2GB  80.0GB  3754MB  logical   linux-swap(v1)


gregg@LG:~/Desktop$ 
```

---

### Post by Bashing-om on 2016-04-28
gregg3; Welp ...

Was my hope that in post #13 " sudo rm -fr /var/lib/apt/lists " ect ... would take care of the cache error.
Looks like we have more work to do in this regard . Will study about it and see what I can come up with.

In the meantime ... let's take a look at what the system is mounting ... maybe that is the source of the wait states ?
```

cat /proc/mounts

```


[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]othertimes I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-28
> **Bashing-om said:**
> gregg3; Welp ...

Was my hope that in post #13 " sudo rm -fr /var/lib/apt/lists " ect ... would take care of the cache error.
Looks like we have more work to do in this regard . Will study about it and see what I can come up with.

In the meantime ... let's take a look at what the system is mounting ... maybe that is the source of the wait states ?
```

cat /proc/mounts

```[INDENT][INDENT]sometimes I do wonder[INDENT][INDENT][INDENT]othertimes I do not know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks Bashing-om. Obviously I defer to you in everything, but with the cache error message they were saying a file was missing, and your ```
" sudo rm -fr /var/lib/apt/lists " ect  
``` was removing something. (Just thinking out loud.)

Also wondering why that 'upgrade' batch of commands would lengthen the time it takes for the computer to come on. And I'm sure this is a lame request but I could live with the 15-30 minute boot time if it were possible to get back to that state. (Obviously I would like the normal boot more than anything, but this being my work computer I get nervous about losing it entirely. I mean, it's backed up and all but even so.) 

Anyway, here's the results of the latest. Thanks.
```

gregg@LG:~/Desktop$ cat /proc/mounts
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=1744016k,nr_inodes=436004,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=352772k,mode=755 0 0
/dev/sda1 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/ 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory,nsroot=/ 0 0
cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids,nsroot=/ 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices,nsroot=/ 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/ 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/ 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/ 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/ 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/ 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/ 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/ 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=352772k,mode=700,uid=1000,gid=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
gregg@LG:~/Desktop$ 
```

FYI Came across this Googling around. Doesn't seem like it would be much help but the guy had the same symptom (hours to boot).

[http://ubuntuforums.org/showthread.php?t=2229548](http://ubuntuforums.org/showthread.php?t=2229548)

---

### Post by Bashing-om on 2016-04-28
gregg3; Yuk ...on me ;

Your "cat /proc/mounts" totally unlike what I had expected .. I have not seen 16.04 and those mounts may be sane. I will boot up a systemd system much later and compare to my system. If there is a problem mounting .. well there is a problem. The log files will then say ... Getting closer and closer to reading the instructions.

Meanwhile I am still debating with self about /var/cache/apt/srcpkgcache.bin . I do think it is safe to delete it .. and move on .. but let me confirm .

[INDENT][INDENT]this puzzle sure beats a jig saw puzzle
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-28
> **Bashing-om said:**
> gregg3; Yuk ...on me ;

Your "cat /proc/mounts" totally unlike what I had expected .. I have not seen 16.04 and those mounts may be sane. I will boot up a systemd system much later and compare to my system. If there is a problem mounting .. well there is a problem. The log files will then say ... Getting closer and closer to reading the instructions.

Meanwhile I am still debating with self about /var/cache/apt/srcpkgcache.bin . I do think it is safe to delete it .. and move on .. but let me confirm .[INDENT][INDENT]this puzzle sure beats a jig saw puzzle
[/INDENT]
[/INDENT]


Thanks Bashing-om. Okay. In the meantime, it's a good bet to leave the computer on, right? I mean, that way I can at least get to the terminal. And the progression (for the start-up) was from less than a half hour to three hours, and so I'm pretty concerned if I'll be able to get the computer back on if I shut it down. Thanks.

---

### Post by Bashing-om on 2016-04-28
gregg3; Well ...

Best practice with a computer is never shut it down .. and only reboot as needed .
I have had systems running constantly for years on end.

Back to : /var/cache/apt/srcpkgcache.bin
> 
apt-get clean
 removes all pkgcache.bin files, including the temporary ones that apt-get update uses
 to rebuild the cache. This error is harmless, since pkgcache.bin should also have been
 removed, and thus the next time the cache will be opened the cache will be rebuilt.


So let's do like so:
```

ls -al /var/cache/apt/srcpkgcache.bin
sudo apt-get clean
sudo apt-get autoclean
ls -al /var/cache/apt/srcpkgcache.bin
sudo apt update
sudo apt upgrade
ls -al /var/cache/apt/srcpkgcache.bin

```
and see what happened.

I would still even in the light of never shutting down ... at some convenient point .. reboot to the terminal .. and see what happens with no GUI in the equation .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-28
> **Bashing-om said:**
> gregg3; Well ...

Best practice with a computer is never shut it down .. and only reboot as needed .
I have had systems running constantly for years on end.

Back to : /var/cache/apt/srcpkgcache.bin


So let's do like so:
```

ls -al /var/cache/apt/srcpkgcache.bin
sudo apt-get clean
sudo apt-get autoclean
ls -al /var/cache/apt/srcpkgcache.bin
sudo apt update
sudo apt upgrade
ls -al /var/cache/apt/srcpkgcache.bin

```
and see what happened.

I would still even in the light of never shutting down ... at some convenient point .. reboot to the terminal .. and see what happens with no GUI in the equation .[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


Thanks Bashing-om. Okay here are the results:
```

gregg@LG:~/Desktop$ ls -al /var/cache/apt/srcpkgcache.bin
-rw-r--r-- 1 root root 42269651 Apr 28 17:07 /var/cache/apt/srcpkgcache.bin
gregg@LG:~/Desktop$ sudo apt-get clean
[sudo] password for gregg: 
gregg@LG:~/Desktop$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gregg@LG:~/Desktop$ ls -al /var/cache/apt/srcpkgcache.bin
-rw-r--r-- 1 root root 42269651 Apr 28 21:50 /var/cache/apt/srcpkgcache.bin
gregg@LG:~/Desktop$ sudo apt update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                                                               
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease                                                               
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [93.3 kB]                                    
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [92.2 kB]         
Hit:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease                             
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [31.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [31.3 kB]
Fetched 248 kB in 0s (248 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: There is no public key available for the following key IDs:
1397BC53640DB551
gregg@LG:~/Desktop$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  google-chrome-stable
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 48.4 MB of archives.
After this operation, 5,120 B disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://dl.google.com/linux/chrome/deb stable/main amd64 google-chrome-stable amd64 50.0.2661.94-1 [48.4 MB]
Fetched 48.4 MB in 21s (2,253 kB/s)                                                                                                                                                
(Reading database ... 259477 files and directories currently installed.)
Preparing to unpack .../google-chrome-stable_50.0.2661.94-1_amd64.deb ...
Unpacking google-chrome-stable (50.0.2661.94-1) over (50.0.2661.86-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up google-chrome-stable (50.0.2661.94-1) ...
gregg@LG:~/Desktop$ ls -al /var/cache/apt/srcpkgcache.bin
-rw-r--r-- 1 root root 42269651 Apr 28 21:52 /var/cache/apt/srcpkgcache.bin
gregg@LG:~/Desktop$ 
```


Okay, I'll leave the computer on, thanks. And for rebooting to the terminal use 
```
sudo reboot
```
?

And I'll wait for you to tell me to do that. :) 

Thanks.

BTW I think this will do it for me tonight. I really appreciate all the help. Have a good night!

P.S. One last thought. When I was away from the computer for over an hour before I came back to it for this post I had the monitor off.  So when I came back I turned the monitor on and the "No Input Signal" window came on the screen. (I almost fainted!) Then when I rolled the mouse a little the normal screen (it happened to be here--the Ubuntu forum) came on. I just mention that if it might be a clue.

---

### Post by Bashing-om on 2016-04-29
gregg3; Morning !

1) appears the /var/cache/apt/srcpkgcache.bin error has been taken care of.
2) appears the GPG signing key for google-chrome has been taken care of.
3) "No Input Signal" window came on the screen." Normal , The kernel recognizing a changed condition - screen saver .
4) Your concern about loosing your data - unable to boot the system : Have you got a liveDVD(USB) on hand ? With the live environment we can always mount the installed file system from the liveDVD and copy your data off , in preparation for a fresh clean install of the operating system.
5)Now to the biggy ... " cat /proc/mounts;
My results:
```

15.10 cat /proc/mounts 29Apr2016
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0 **
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0 **
udev /dev devtmpfs rw,nosuid,relatime,size=1973504k,nr_inodes=493376,mode=755 0 0
udev /dev devtmpfs rw,nosuid,relatime,size=1744016k,nr_inodes=436004,mode=755 0 0 **
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0 **
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=404752k,mode=755 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=352772k,mode=755 0 0 **
/dev/sdb3 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/sda1 / ext4 rw,relatime,errors=remount-ro,data=ordered 0 0 **
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0 **
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0 **
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0 **
tmpfs /sys/fs/cgroup tmpfs rw,mode=755 0 0
->tmpfs /sys/fs/cgroup tmpfs ro,nosuid,nodev,noexec,mode=755 0 0 **
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
->cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd,nsroot=/ 0 0 **
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0 **
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb 0 0
->cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb,nsroot=/ 0 0 **
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
->cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio,nsroot=/ 0 0 **
->cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset,clone_children 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset,nsroot=/ 0 0 **
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/
->cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event,nsroot=/ 0 0 **
agents/cgm-release-agent.perf_event 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
->cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory,nsroot=/ 0 0 **
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
->cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer,nsroot=/ 0 0 **

cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
->cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct,nsroot=/ 0 0 **
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
->cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio,nsroot=/ 0 0 **
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices,nsroot=/ 0 0 **
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct 0 0 **
mqueue /dev/mqueue mqueue rw,relatime 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0 **
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0 **
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0 **
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0 **
cgmfs /run/cgmanager/fs tmpfs rw,relatime,size=100k,mode=755 0 0
tmpfs /run/user/119 tmpfs rw,nosuid,nodev,relatime,size=404752k,mode=700,uid=119,gid=129 0 0
->tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=352772k,mode=700,uid=1000,gid=1000 0 0 **
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=404752k,mode=700,uid=1000,gid=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0 **
//
##these two are not accounted for.

cgroup /sys/fs/cgroup/pids cgroup rw,nosuid,nodev,noexec,relatime,pids,nsroot=/ 0 0


binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0
----------------------

```
Where the entries ending in '**" are from your mounts ... and a difference in yours to mine are noted by ' ->' at the start of the entry.

Honestly, I do not have the knowledge to know here ... I have yet to see 16.04 - what the differences imply . " nsroot=/ " I do not know what this switch is ! , "/r/run/user/119 " ... why this ID rather than that of 1000 ? What is the system doing here : " cgroup /sys/fs/cgroup/pids" ??  Nor do I know what the system is mounting here " binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,relatime 0 0 " .

Presently the concern is in the delay in booting up . In order to isolate I do advocate to boot to grub;
a) If one can boot to grub in  a timely manner then bios is not an issue -
b) If we can boot to terminal in a timely manner then the file system is not an issue -
c) Then we start the GUI from terminal and see what the errors are. A number of log files - in addition to what is reported in the terminal - we can examine to see where the fault may lie.
d) Booting to terminal, only basic services are started and we control what additional services are started ; see if service activation is the root cause of the long delay in booting.

[INDENT][INDENT][INDENT]all I know to do
[/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-29
> **Bashing-om said:**
> gregg3; Morning !

1) appears the /var/cache/apt/srcpkgcache.bin error has been taken care of.
2) appears the GPG signing key for google-chrome has been taken care of.
3) "No Input Signal" window came on the screen." Normal , The kernel recognizing a changed condition - screen saver .
4) Your concern about loosing your data - unable to boot the system : Have you got a liveDVD(USB) on hand ? With the live environment we can always mount the installed file system from the liveDVD and copy your data off , in preparation for a fresh clean install of the operating system.

I can make a live USB flash drive easily enough. (But of Xubuntu 16.04LTS, right? And would that be the circled one in the 073 attachment?)

> **Bashing-om said:**
> 

Presently the concern is in the delay in booting up . In order to isolate I do advocate to boot to grub;
a) If one can boot to grub in  a timely manner then bios is not an issue -
b) If we can boot to terminal in a timely manner then the file system is not an issue -
c) Then we start the GUI from terminal and see what the errors are. A number of log files - in addition to what is reported in the terminal - we can examine to see where the fault may lie.
d) Booting to terminal, only basic services are started and we control what additional services are started ; see if service activation is the root cause of the long delay in booting.[INDENT][INDENT][INDENT]all I know to do
[/INDENT]
[/INDENT]
[/INDENT]


Thanks Bashing-om. So where do we start? The live USB flash drive? The boot to grub? And remember, I'm a newbie. For instance, boot to grub--okay, I have a general idea of what that means but that's it. Would I be following this sort of thing? (see 072 attachment)

Let me know what you want me to do. (And, as always, step-by-step instructions really help me.) Thanks.

---

### Post by Bashing-om on 2016-04-29
gregg3; Yeah ...

xubuntu as a live environment will work very well IF the need to recoup -arate should present it's self.

OK, so far so good . System is fully updated and all errors have been resolved with the package manager.
Onward !
As you boot to grub fine .. let's see how fast you boot to terminal.
At that grub menu with the latest kernel selected to boot pres the 'e' key for edit mode -> boot parameters screen.
Here arrow down to the line starting with linux, and arrow across to "quiet splash" . Delete these terms and all after and insert " systemd.unit=multi-user.target " - without the quotes .
Key combo ctl+x to continue to the TTY1 terminal.
Log in here .. be aware there are minimal services available .. We must enable all other services as we desire . At this time .. all I am concerned about is how fast you boot to terminal .. and IF/What errors maybe reported in this terminal interface . Networking IS NOT available until we enable it . Maybe note what the happenstance is .. and we take it from this point .

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-29
> **Bashing-om said:**
> gregg3; Yeah ...

xubuntu as a live environment will work very well IF the need to recoup -arate should present it's self.

OK, so far so good . System is fully updated and all errors have been resolved with the package manager.
Onward !
As you boot to grub fine .. let's see how fast you boot to terminal.
At that grub menu with the latest kernel selected to boot pres the 'e' key for edit mode -> boot parameters screen.
Here arrow down to the line starting with linux, and arrow across to "quiet splash" . Delete these terms and all after and insert " systemd.unit=multi-user.target " - without the quotes .
Key combo ctl+x to continue to the TTY1 terminal.
Log in here .. be aware there are minimal services available .. We must enable all other services as we desire . At this time .. all I am concerned about is how fast you boot to terminal .. and IF/What errors maybe reported in this terminal interface . Networking IS NOT available until we enable it . Maybe note what the happenstance is .. and we take it from this point .[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]


Thanks Bashing-om. Before I follow your instructions, I had this thought (that I'm sure you know about): Can't I just go back and boot from the previous kernel? Then I can do another upgrade to 16.04LTS MUCH later when all the bugs are worked out. Now, mind you, I have no idea if this will work but it does seem to be something a lot of people are doing: 

[https://www.google.com/#q=can+i+go+back+to+an+old+kernel+ubuntu&safe=active&start=0](https://www.google.com/#q=can+i+go+back+to+an+old+kernel+ubuntu&safe=active&start=0)

And it seems to be something my simple brain could handle. :) As to the best method I do not know what that would be. I am familiar with getting rid of old kernels with ```
sudo aptitude remove
``` but in this instance I would be getting rid of the new kernel. And I'm sure the whole thing (if possible at all) would be much more complicated than that.

Here's what's in the terminal in terms of kernels:

```
gregg@LG:~/Desktop$ aptitude search linux-image |grep '^i'
i A linux-image-4.2.0-35-generic    - Linux kernel image for version 4.2.0 on 64
i A linux-image-4.4.0-21-generic    - Linux kernel image for version 4.4.0 on 64
i A linux-image-extra-4.2.0-35-gene - Linux kernel extra modules for version 4.2
i A linux-image-extra-4.4.0-21-gene - Linux kernel extra modules for version 4.4
i A linux-image-generic             - Generic Linux kernel image                
gregg@LG:~/Desktop$ uname -r
4.4.0-21-generic
gregg@LG:~/Desktop$ 
```

Then if that is un-workable I do have a couple of questions regarding your instructions. (I'm afraid of getting lost in the grub stuff.)

1) I get to the grub menu by: restart>holding down the "shift" key, right?
2) I get everything till this point: [U]be aware there are minimal services available .. We must enable all other services as we desire . At this time .. all I am concerned about is how fast you boot to terminal .. and IF/What errors maybe reported in this terminal interface . Networking IS NOT available until we enable it . 

[/U]Okay, I'll be aware of the minimal services but do I need to *do* anything? And what am I supposed to *do *in terms of enabling all other services as we desire? So, okay, I'll record the time it takes to boot to terminal, but then do the errors (granted, if there are any) just appear in the terminal? And lastly I don't know what the significance of the Networking not being available is. (Again do I need to do anything about that?)

I'm just concerned that I do the right things and do not do the wrong things. Thanks.

---

### Post by Bashing-om on 2016-04-29
gregg3; Welp ...

A good thought to see what results in booting the older kernel !

As to booting to terminal in the present new kernel . There is at this time nothing else to be done . This presently is but a test to see how quick it boots, and IF there are reported errors.

Again, if this is an EFI system, it is the escape key that grub looks for  when booting to the grub menu.

[INDENT][INDENT]poke at it til something gives
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-29
> **Bashing-om said:**
> gregg3; Welp ...

A good thought to see what results in booting the older kernel !

As to booting to terminal in the present new kernel . There is at this time nothing else to be done . This presently is but a test to see how quick it boots, and IF there are reported errors.

Again, if this is an EFI system, it is the escape key that grub looks for  when booting to the grub menu.[INDENT][INDENT]poke at it til something gives
[/INDENT]
[/INDENT]


Thanks Bashing-om. But is my logic good? The idea that I can just use the older kernel until maybe June and then upgrade to the 16.04LTS? Is it that simple? And then to turn the computer off I would have to get rid of the new kernel (I mean, in order for it to start properly), right?

And is it worth this attempt or would a better approach be following your instructions and seeing what error messages come up in the current kernel?

---

### Post by Bashing-om on 2016-04-29
gregg3; Welp;

> 
The idea that I can just use the older kernel until maybe June and then upgrade to the 16.04LTS?

You already have 16.04 installed. You also have the older kernels from prior releases installed. There is not a thing wrong with seeing what results booting an older kernel .. If it boots and runs fine .. one can make that kernel the default booting kernel.
1) Seeing what results when booting up the older kernels
2) Booting up a liveDVD pf release 16.04 and seeing how the system performs
3) Saving your personal data and doing a fresh clean install and see how the system performs in a "clean" environment
4) continue to trouble shoot this install .. next step is boot to terminal .

Your system
[INDENT]your time
[INDENT][INDENT][INDENT]your call
[INDENT]Me, I always opt to fix[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-04-29
> **Bashing-om said:**
> gregg3; Welp;


You already have 16.04 installed. You also have the older kernels from prior releases installed. There is not a thing wrong with seeing what results booting an older kernel .. If it boots and runs fine .. one can make that kernel the default booting kernel.
1) Seeing what results when booting up the older kernels
2) Booting up a liveDVD pf release 16.04 and seeing how the system performs
3) Saving your personal data and doing a fresh clean install and see how the system performs in a "clean" environment
4) continue to trouble shoot this install .. next step is boot to terminal .

Your system[INDENT]your time[INDENT][INDENT][INDENT]your call[INDENT]Me, I always opt to fix[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



All right, Bashing-om, thanks. I took some time and learned a little bit (I experimented on a lesser computer) about the GRUB loader and was able to get that to work on the troubled computer. For the heck of it I tried to boot from the 16.04LTS--same result. In other words--nothing (and probably another 3 hour boot). I did also (via the GRUB) manage to boot from the older kernel and it worked great. Booted up normal. Seemed Dropbox had to sync for a while but there seemed to be hardly any differences. The only differences would be what I've done on the 16.04LTS kernel, right? 

So that is a great relief, knowing I'll be able to use the computer for work. And I can also work at fixing 16.04LTS, right? (I mean, when I'm not using the 15.10.) And I checked out that 'parameters screen' on a lesser computer. I should be able to follow your instructions (in terms of deleting the 'splash' etc and adding that other line.)

So I will attempt the "fix" soon and report back. (But calling it a night tonight.:))

Thanks so much!

---

### Post by QLee on 2016-04-30
> **Bashing-om said:**
> 
Honestly, I do not have the knowledge to know here ... I have yet to see 16.04 - what the differences imply . " nsroot=/ " I do not know what this switch is ! , "/r/run/user/119 " ... why this ID rather than that of 1000 

This is a laptop, presumably when  gregg3 is working on this at home the Netscaler device is not attached, so are there fstab lines relating to it affecting boot time?  I don't know, just theorising.

gregg3 can find out what group 119 is by entering command getent group in a terminal and "grepping" for 119.

Don't know if this will help or not but maybe worth considering.

We are pretty far afield of the thread title at this point.

---

### Post by gregg3 on 2016-04-30
> **Bashing-om said:**
> gregg3; Yeah ...

xubuntu as a live environment will work very well IF the need to recoup -arate should present it's self.

OK, so far so good . System is fully updated and all errors have been resolved with the package manager.
Onward !
As you boot to grub fine .. let's see how fast you boot to terminal.
At that grub menu with the latest kernel selected to boot pres the 'e' key for edit mode -> boot parameters screen.
Here arrow down to the line starting with linux, and arrow across to "quiet splash" . Delete these terms and all after and insert " systemd.unit=multi-user.target " - without the quotes .
Key combo ctl+x to continue to the TTY1 terminal.
Log in here .. be aware there are minimal services available .. We must enable all other services as we desire . At this time .. all I am concerned about is how fast you boot to terminal .. and IF/What errors maybe reported in this terminal interface . Networking IS NOT available until we enable it . Maybe note what the happenstance is .. and we take it from this point .[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]


Okay, booting to Grub I did NOT see the usual bar (which slides left to right) screen, but only the screen with the stuff like DDR3, and then 'loading operating system' so during that time I held down the 'shift' key and the Grub menu came up in less than 10 seconds.

Okay, in the Gnu Grub setparams 'Ubuntu, with Linux 4.4.0-21-generic' screen, I deleted:

```
quiet splash $vt_handoff
```

Then I added:```
systemd.unit=multi-user.target
```

Then I hit ctl + x and a bunch of data ran across the terminal for five seconds or so, then the "No Input Signal" appeared.

Now it's been 4 and a half hours and still nothing but the "No Input Signal."

Just leave the computer on all night like this? Thanks.

---

### Post by gregg3 on 2016-04-30
> **QLee said:**
> This is a laptop, presumably when  gregg3 is working on this at home the Netscaler device is not attached, so are there fstab lines relating to it affecting boot time?  I don't know, just theorising.

gregg3 can find out what group 119 is by entering command getent group in a terminal and "grepping" for 119.

Don't know if this will help or not but maybe worth considering.

We are pretty far afield of the thread title at this point.

QLee, FWIW it's not a laptop. It's a desktop.

---

### Post by Bashing-om on 2016-04-30
gregg3; Yuk !

Presently I have no idea :
> 
so, then the "No Input Signal" appeared.
 what would cause this loss of signal.
Older kernels boot fine, right ?

as to powering the system down:
> 
Just leave the computer on all night like this? Thanks.

there is no point in leaving the system on.

If we can not activate a terminal, we are dead in the water with nowhere to go.

[INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-01
> **gregg3 said:**
> QLee, FWIW it's not a laptop. It's a desktop.

Sorry, that was meant to be a question and then I just kept writing a sentence.  You said this was the computer you use for work so is it always connected to the Netscaler device? That line nsroot=/ seems to indicate a Citrix NetScaler but that is just a guess. 

If you ever get to a terminal you can enter ```
 getent group | grep 119 
``` to answer Bashing-om's question about user 119. The command will enumerate the group database and grep (find) and return the name of the group and thus likely the name of the user. 

Good luck to you both!

---

### Post by Bashing-om on 2016-05-01
@QLee;  :)

Appreciate the input and advise .. this has become a real conundrum . A struggle to even find a means to find the fault(s).

gregg3; Nother thought here...

In my continuing cogitation - "No Input Signal" :
Old hardware, such that drivers in 16.04 are not available ??? If you can boot an older kernel we can look at the graphic's situation, and perhaps rule that one out as the fault ? Not able to boot to terminal really puts a crimp in my style, working to see what the logs relate.

Faulty kernel install on this later kernel that is giving us such fits ?  Presently, we just do not know .

[INDENT][INDENT]what to do when we can not
[INDENT][INDENT][INDENT]read the instructions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-01
> **QLee said:**
> Sorry, that was meant to be a question and then I just kept writing a sentence.  You said this was the computer you use for work so is it always connected to the Netscaler device? 

Thanks, QLee. I don't know if I the computer is connected to a Netscaler device.

> **QLee said:**
> 

If you ever get to a terminal you can enter ```
 getent group | grep 119 
``` to answer Bashing-om's question about user 119. The command will enumerate the group database and grep (find) and return the name of the group and thus likely the name of the user. 

Good luck to you both!

I do have the computer up and running but with the *previous* kernel. Would the ```
 getent group | grep 119 
``` command be something to run there? Or was that only for the 16.04LTS kernel?

---

### Post by Bashing-om on 2016-05-01
:);

Good thinking ! .. we await a response from QLee.

[INDENT][INDENT]in this case, I just do not know
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-01
I have no idea if user 119 matters or not, I just think it a good thing that Bashing-om spotted the anomaly, I would just look it up to see if there were any hints I could use. The groups are part of the system, will be the same with the different kernels.

If I am not mistaken, at this point we are trying to troubleshoot a long boot up time (sometimes hours), that's why I suggested looking at fstab to see if mountall is choking on an entry.  Bashing-om seems to have taken care of the package problem very well.

If no device then, that was just a bad guess I made about "nsroot=/".

It's also possible that I made a bad guess about fstab too. Just throwing out ideas.

---

### Post by gregg3 on 2016-05-01
> **Bashing-om said:**
> @QLee;  :)

Appreciate the input and advise .. this has become a real conundrum . A struggle to even find a means to find the fault(s).

gregg3; Nother thought here...

In my continuing cogitation - "No Input Signal" :
Old hardware, such that drivers in 16.04 are not available ??? If you can boot an older kernel we can look at the graphic's situation, and perhaps rule that one out as the fault ? Not able to boot to terminal really puts a crimp in my style, working to see what the logs relate.

Faulty kernel install on this later kernel that is giving us such fits ?  Presently, we just do not know .[INDENT][INDENT]what to do when we can not[INDENT][INDENT][INDENT]read the instructions
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hey Bashing-om. Ok, I finally got back here and the computer was on 24 hours and nothing. 

I was able to start the computer again (see screenshot) via the GRUB menu with the 4.2.0-35-generic kernel. (And what does the "upstart" mean?) The startup from the Grub did seem different. There was the "No input signal" window at first, then a black screen for two or three minutes and then the toolbar came on and the icons on the Desktop started populating. (Usually I get the bright blue Xubunutu window and the spinning action during a normal boot. But I don't know--the black screen may be normal for booting from the GRUB menu.) 

The one thing I thought of was when I first upgraded from 15.10 to the 16.04LTS everything went smoothly. Until  I got to the "reboot" stage. So I rebooted. But when I did, rather than the familiar process of the screen going black and then coming back on and starting the boot process, the screen just went black and stayed black. I waited a couple of minutes and the screen stayed black. Then I, thinking the computer had powered off, pressed the power button, which of course did nothing because the computer was on. So I realized the computer was on and let it be. Then maybe 40 minutes later the computer booted. I seriously doubt that premature pushing the power button screwed anything up but I figured I'd mention it as a possible clue anyway. 

The other thing, which I mentioned before, was the computer went from a 15-30 minute startup to a 1 hour 15 minute (and then 3 hour) startup after I ran this bunch of commands:

```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt full-upgrade
```

I don't know enough about the commands as to why that might've caused the delay in booting up but I figured I'd mention it.

The only other thing I can think of is a lot of people seem to be struggling with the upgrade to 16.04. Couldn't it just be a buggy upgrade I got? And, as I said before,  maybe I can just live with the 4.2.0-35 version until maybe a couple weeks before the support for 15.10 ends (which I think isn't until July) and then  try another upgrade to 16.04LTS? (I don't know if it works that way, though. I mean, I don't know if the computer will give me another window saying 'do you want to upgrade to 16.04LTS?' like it did before.)

I know you are a "fixer" :D and I'm up for trying to fix it still but we do seem to be pretty stuck. 

As to the old hardware and drivers I've attached a couple of screenshots from SysInfo. The computer is only four years old or so and works great. 

In my _*very*_ uninformed opinion, the best course would seem to be to get rid of the  4.4.0-21-generic kernel and use the 4.2.0-35-generic kernel until maybe June and then upgrade again to 16.04LTS. 

P.S. I did see that  you wrote (about waiting on QLee) while I was writing this post. 
P.S.S. Thanks! (Sorry this thing has become such a mess!)

---

### Post by gregg3 on 2016-05-01
> **QLee said:**
> I have no idea if user 119 matters or not, I just think it a good thing that Bashing-om spotted the anomaly, I would just look it up to see if there were any hints I could use. The groups are part of the system, will be the same with the different kernels.

If I am not mistaken, at this point we are trying to troubleshoot a long boot up time (sometimes hours), that's why I suggested looking at fstab to see if mountall is choking on an entry.  Bashing-om seems to have taken care of the package problem very well.

If no device then, that was just a bad guess I made about "nsroot=/".

It's also possible that I made a bad guess about fstab too. Just throwing out ideas.

Thanks QLee. Here's the 119 thing:

```
gregg@LG:~/Desktop$ getent group | grep 119
lightdm:x:119:
gregg@LG:~/Desktop$ 

```

---

### Post by Bashing-om on 2016-05-01
gregg3; Hey hey !

Now that ^^ " lightdm:x:119:" is a good hint of what might not be taking place ..

OK answer questions:
upstart is one initiate system that was the default up and until 15.10;
in 15.10 ( testing available in 14.04) systemd was introduced. that has now become the default initiate system to boot up the system and control the services.
in 16.04 we still have the option of which initiate system to boot with .

Lightdm: that is the display manager, control the greeter. display and logout . The GUI elements.

Nope on a future offer to release upgrade . this only happens once .. and we move on. Now what you can do .. is backup your personal data .. and RE-install 16.04 fresh . This after testing 16.04 with that live xubuntu install media in the "try ubuntu" mode and insuring all hardware works as expected. Hey, when backups are done, it is but a matter of about 30 minutes to RE-install.

As to your present situation, we now know that it is a problem with systemd in 16.04- maybe some old upstart scripts still around that are incompatible with systemd (??). Maybe in starting lightdm .( not too likely as we fail to boot to terminal and lightdm at that point should not be a factor) We are making progress on isolating where and the nature of the fault .. just lacking tools ( a terminal) to have a good look. We really want to see things from the broken boot attempt's perspective .. somehow . To get to the relevant log files.
--------------------

Additional thoughts: As the original opening query has been addressed and is solved, AND as I am struggling so, - I never dreamed a booting issue to be this deep - might be in your best interest to mark this thread 'solved' . To fix this booting issue to open a new thread - referencing this thread - to gain a wider focused audience.

[INDENT][INDENT]there is no substitute for experience
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-01
A bit more to consider.

Well, here's the thing Gregg, if I read what you wrote correctly, you've already upgraded to 16.04, you are just using an older kernel. 

Enter ```
cat /etc/lsb-release
```

What does the system think?

Did you read the release notes before you tried the upgrade? These things about the AMD Radeon video will be of interest.


From release notes:> Graphics and Display

fglrx

The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). AMD put a lot of work into the drivers, and we backported kernel code from Linux 4.5 to provide a better experience.

When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

More information is available at [https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

[http://askubuntu.com/questions/744050/im-using-ubuntu-16-04-and-theres-no-fglrx](http://askubuntu.com/questions/744050/im-using-ubuntu-16-04-and-theres-no-fglrx)

So, maybe some of those black screens that you have seen might be due to video not being set up correctly when you tried to turn off with the power switch during the reboot from the upgrade attempt. Your system might be in a state "in-between".

---

### Post by Bashing-om on 2016-05-02
> **QLee said:**
> A bit more to consider.

Well, here's the thing Gregg, if I read what you wrote correctly, you've already upgraded to 16.04, you are just using an older kernel. 

Enter ```
cat /etc/lsb-release
```

What does the system think?

Did you read the release notes before you tried the upgrade? These things about the AMD Radeon video will be of interest.


From release notes:

[http://askubuntu.com/questions/744050/im-using-ubuntu-16-04-and-theres-no-fglrx](http://askubuntu.com/questions/744050/im-using-ubuntu-16-04-and-theres-no-fglrx)

So, maybe some of those black screens that you have seen might be due to video not being set up correctly when you tried to turn off with the power switch during the reboot from the upgrade attempt. Your system might be in a state "in-between".

Concur totally .. could be ..
Also I am considering .. corruption within the normal user account ? .. 
a) What results when booting the latest systemd kernel in the guest account ?
b) What results booting this ^ kernel up from grub's boot menu with the " nomodeset" boot parameter ? ( insert nomodeset vice systemd.unit=multi-user.target ) ?

As we still try to isolate where this fault lies.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by QLee on 2016-05-02
Well Bashing-om, it looks like Gregg might have decided to take your advice and try a reinstall over the current system. Hopefully it can complete without errors. That very likely was faster than trying to sort out what was needed to get the video corrected anyway. 

BTW, when you were trying to get Gregg to a terminal did you consider booting from GRUB to a recovery mode? 

We need a lot of tools in the toolbox.

When one doesn't work, we try another. :-)

---

### Post by gregg3 on 2016-05-02
> **Bashing-om said:**
> gregg3; Hey hey !

Now that ^^ " lightdm:x:119:" is a good hint of what might not be taking place ..

OK answer questions:
upstart is one initiate system that was the default up and until 15.10;
in 15.10 ( testing available in 14.04) systemd was introduced. that has now become the default initiate system to boot up the system and control the services.
in 16.04 we still have the option of which initiate system to boot with .

Lightdm: that is the display manager, control the greeter. display and logout . The GUI elements.

Nope on a future offer to release upgrade . this only happens once .. and we move on. Now what you can do .. is backup your personal data .. and RE-install 16.04 fresh . This after testing 16.04 with that live xubuntu install media in the "try ubuntu" mode and insuring all hardware works as expected. Hey, when backups are done, it is but a matter of about 30 minutes to RE-install.

As to your present situation, we now know that it is a problem with systemd in 16.04- maybe some old upstart scripts still around that are incompatible with systemd (??). Maybe in starting lightdm .( not too likely as we fail to boot to terminal and lightdm at that point should not be a factor) We are making progress on isolating where and the nature of the fault .. just lacking tools ( a terminal) to have a good look. We really want to see things from the broken boot attempt's perspective .. somehow . To get to the relevant log files.
--------------------

Additional thoughts: As the original opening query has been addressed and is solved, AND as I am struggling so, - I never dreamed a booting issue to be this deep - might be in your best interest to mark this thread 'solved' . To fix this booting issue to open a new thread - referencing this thread - to gain a wider focused audience.[INDENT][INDENT]there is no substitute for experience
[/INDENT]
[/INDENT]


Thanks Bashing-om. I think that testing with the live 16.04LTS before installing is an excellent suggestion. The thing is I'll have to re-install all my applications and then resync all the things I have synced, but that's not the end of the world. 

Thanks for the explanations about upstart etc.. 

And since I can't get to the terminal in the 16.04LTS version, I guess it's pretty pointless to start a new thread in terms of still trying to fix it, right?

I'm pretty resigned to the testing the live 16.04LTS before fresh installing it.

Regarding the "upstart" and "recovery mode." We wouldn't want to try the recovery mode for the 16.04LTS? (I'm just guessing, mind you. Just because of the name with 'recovery' in it.) And when would I ever use the "upstart" mode?

(see screenshot) This is the 16.04 (the one I highlighted) I want, right? (Even though it doesn't say LTS?) 

Is there any advantage to waiting, till say June, before testing, and only then installing the 16.04LTS? Like as time passes potential bugs will get worked out.

And I may be getting confused by the terminology, but you mention: 

> _RE-install_ 16.04[U] fresh .

[/U]What I thought you were intending was for me to boot up a live bootable USB flash drive with the 16.04LTS iso on it. Then use the "try Xubuntu" mode until I was satisfied it was working okay, and then permanently installing it.

But I have also seen stuff on "re-installing" which allows one to save all their data and settings (which of course would be nice), but might be over my head. (With stuff like:

```
Boot from install disk, choose 'something else, Dclick on your '/' partition, choose a file system, choose '/' as your mount (do not format)

```
in it.

The above is from this link:

[http://ubuntuforums.org/showthread.php?t=2057342](http://ubuntuforums.org/showthread.php?t=2057342)

But I suppose, as you say, all that sort of stuff should be in a new thread. (But you're just so helpful I'm afraid of losing you!!LOL)

I figure after you answer this, I'll mark this thread as "solved."

Thanks!

---

### Post by gregg3 on 2016-05-02
> **QLee said:**
> A bit more to consider.

Well, here's the thing Gregg, if I read what you wrote correctly, you've already upgraded to 16.04, you are just using an older kernel. 

Enter ```
cat /etc/lsb-release
```

What does the system think?

Did you read the release notes before you tried the upgrade? These things about the AMD Radeon video will be of interest.


From release notes:

[http://askubuntu.com/questions/744050/im-using-ubuntu-16-04-and-theres-no-fglrx](http://askubuntu.com/questions/744050/im-using-ubuntu-16-04-and-theres-no-fglrx)

So, maybe some of those black screens that you have seen might be due to video not being set up correctly when you tried to turn off with the power switch during the reboot from the upgrade attempt. Your system might be in a state "in-between".

Thanks QLee. 

Well, this just about flabbergasted me. When I ran your command this is what I got:

```
gregg@LG:~/Desktop$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"
gregg@LG:~/Desktop$
``` 


Did the ```
cat /etc/lsb-release
``` command call up the distro information of the active distro?

And if it did, how is that even possible that it's 16.04LTS?!! Because I booted from the GRUB menu (see attachment) into the 4.2.0-35 kernel, which is the previous kernel, which I *thought* was Xubuntu 15.10.

---

### Post by gregg3 on 2016-05-02
> **QLee said:**
> Well Bashing-om, it looks like Gregg might have decided to take your advice and try a reinstall over the current system. Hopefully it can complete without errors. That very likely was faster than trying to sort out what was needed to get the video corrected anyway. 

BTW, when you were trying to get Gregg to a terminal did you consider booting from GRUB to a recovery mode? 

We need a lot of tools in the toolbox.

When one doesn't work, we try another. :-)

Thanks QLee. I was typing up my reply to Bashing-om while this post of yours came in, so yes, I was wondering about attempting the recovery mode option from the GRUB menu as well. 

So that means we should be able to still work in the terminal, right?
But if I do go for a new install I do have questions about a "fresh" install vs. a "reinstall." See post 52 in this thread if you would.

And a final thought: in other words, I'm still open to "fixing" this latest version. (Which although I* thought *was 15.10 might be 16.04LTS!) That really would be the best solution.

And a final final :) thought: I checked out that ```
lsb_release -a
``` command--I *am* running 16.04LTS. LOL--my head is spinning!

And so we should still be able to work in the terminal, right?

---

### Post by Bashing-om on 2016-05-02
gregg3; Welp;

Like this, I am in this game primarily for what I can learn, you are my ginny pig. I am always for fixing an issue.
If you are happy to use your system with the older kernel, and you can do all that you need to do in the environment, I have no heartburn at all to continue to prosecute this booting issue. There is more I do not know that what I do know . I do not have 16.04 installed and am at a disadvantage in that respect. Also I have little familiarity with systemd. If you were to decide to open a new thread on this booting issue, would give audience to others who may have the experience and knowledge to give better advise.

OK, answering questions:
recovery mode:
A means to boot the system with only bare services running, menu driven to provide some tools. From here one can control what is happening and have access to the system to see things .

fresh install . 'buntu is all about options and choices even to installation. In a problematic situation where the fault is NOT identified and correctable then I do advocate in the instance of a RE-install to do it clean - doing away with ALL prior files and configurations. When one chooses not to format say '/ ' or /home then the old config files and settings remain - maybe a source of the problem(s) .
My booting operating system, for your reference and considered consideration :
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           396M  744K  395M   1% /run
/dev/sda1       4.7G  1.8G  2.7G  41% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   12K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   26M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  834M  8.2G  10% /home
/dev/sda8       4.7G  2.5G  2.0G  56% /var
sysop@1404mini:~$

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$

```
where my primary operating system is a 14.04 minimal install - build my own .
Note in my use case I have a separate '/' , /home, and /var partitions. This arrangement works well for me, for MY usecase. In this arrangement if I needed ( again ) to RE-install .. I can do so and not even touch the old /home . When my logs run a-muck -filling up-, will not crash my system. When you have some experience and have an idea of what you use your system for one can only then do a better job of installing than that of the default install wizard. Flexibility .. IF you want/need to .... you can !
---------------------

Back to our booting issue:
> 
And since I can't get to the terminal in the 16.04LTS version, I

We still have other options to explore in an attempt to get us to a terminal to find out what is not taking place ! There is always that last resort - an do what is called a CHange Root from some other booted medium into this install ... 'buntu - there is always a way ! If one has the patience, and the frustration level is not excessive.

> 
I'm pretty resigned to the testing the live 16.04LTS before fresh installing it.

A good thing to do anyway, just for the confidence factor . To know that it is not an issue with the hardware or with systemd.

> 
Is there any advantage to waiting, till say June, before testing, and only then installing the 16.04LTS? 

Yes and no . July 21 is the due date for the 1st point release ( think service pack in Windows) . Bug fixes and some others things will be ironed out - maybe improved graphic's drivers - and such. At that point 16.04 will no longer be considered as development; and may be considered 'stable' . However .. 16.04.1 may not address what the current issue is .- that we have not to this time isolated.

> 
What I thought you were intending was for me to boot up a live bootable USB flash drive with the 16.04LTS iso on it. Then use the "try Xubuntu" mode until I was satisfied it was working okay, and then permanently installing it.

options, options - what do you want to do a.. and how ?

> 
But I suppose, as you say, all that sort of stuff should be in a new thread. [color=blue](But you're just so helpful I'm afraid of losing you!!LOL)[/color]

Experience counts .. those who do know will get us a faster solution . Your thread, your call .. There is no quit in my nature. I will be with you - in some shape form or fashion until the end.

Keep in mind, this is the best way to learn this operating system . Break it, pick up the pieces ( we do get to keep all the pieces ) and put it back together. Wonderful learning experience. 
Taking that nuclear solution of a RE-install ...we learn little or nothing.
--------------------------

So, I ask ya;
[INDENT][INDENT][INDENT]whacha wanna do
[/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-02
> **Bashing-om said:**
> gregg3; Welp;

Like this, I am in this game primarily for what I can learn, you are my ginny pig. I am always for fixing an issue.
If you are happy to use your system with the older kernel, and you can do all that you need to do in the environment, I have no heartburn at all to continue to prosecute this booting issue. There is more I do not know that what I do know . I do not have 16.04 installed and am at a disadvantage in that respect. Also I have little familiarity with systemd. If you were to decide to open a new thread on this booting issue, would give audience to others who may have the experience and knowledge to give better advise.

OK, answering questions:
recovery mode:
A means to boot the system with only bare services running, menu driven to provide some tools. From here one can control what is happening and have access to the system to see things .

fresh install . 'buntu is all about options and choices even to installation. In a problematic situation where the fault is NOT identified and correctable then I do advocate in the instance of a RE-install to do it clean - doing away with ALL prior files and configurations. When one chooses not to format say '/ ' or /home then the old config files and settings remain - maybe a source of the problem(s) .
My booting operating system, for your reference and considered consideration :
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           396M  744K  395M   1% /run
/dev/sda1       4.7G  1.8G  2.7G  41% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   12K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   26M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  834M  8.2G  10% /home
/dev/sda8       4.7G  2.5G  2.0G  56% /var
sysop@1404mini:~$

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$

```
where my primary operating system is a 14.04 minimal install - build my own .
Note in my use case I have a separate '/' , /home, and /var partitions. This arrangement works well for me, for MY usecase. In this arrangement if I needed ( again ) to RE-install .. I can do so and not even touch the old /home . When my logs run a-muck -filling up-, will not crash my system. When you have some experience and have an idea of what you use your system for one can only then do a better job of installing than that of the default install wizard. Flexibility .. IF you want/need to .... you can !
---------------------

Back to our booting issue:

We still have other options to explore in an attempt to get us to a terminal to find out what is not taking place ! There is always that last resort - an do what is called a CHange Root from some other booted medium into this install ... 'buntu - there is always a way ! If one has the patience, and the frustration level is not excessive.


A good thing to do anyway, just for the confidence factor . To know that it is not an issue with the hardware or with systemd.


Yes and no . July 21 is the due date for the 1st point release ( think service pack in Windows) . Bug fixes and some others things will be ironed out - maybe improved graphic's drivers - and such. At that point 16.04 will no longer be considered as development; and may be considered 'stable' . However .. 16.04.1 may not address what the current issue is .- that we have not to this time isolated.


options, options - what do you want to do a.. and how ?


Experience counts .. those who do know will get us a faster solution . Your thread, your call .. There is no quit in my nature. I will be with you - in some shape form or fashion until the end.

Keep in mind, this is the best way to learn this operating system . Break it, pick up the pieces ( we do get to keep all the pieces ) and put it back together. Wonderful learning experience. 
Taking that nuclear solution of a RE-install ...we learn little or nothing.
--------------------------

So, I ask ya;[INDENT][INDENT][INDENT]whacha wanna do
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for all the great explanations, Bashing-om. But did you get a chance to see post #53, which seems to say that I am in 16.04LTS right now! Honestly, I'm confused. 

It's like (if indeed, I am in 16.04LTS) all I need to do is boot from GRUB every time. Not ideal, granted, but not bad considering the alternative. And of course (again, if indeed it's true that I am in 16.04LTS) I can get into the terminal now too. :confused:

---

### Post by Bashing-om on 2016-05-02
gregg3; Uh Huh //

Bear in mind I advised you several posts back that you have indeed 16.04 operating system installed.
As to what 'image' you boot the operating system into .. well that is optional as per what kernel-images are installed.
4.4.0.21.22: == 16.04 xenial,
4.2.XXX     : == 15.10 wily
3.13.XXX   : == 14.04 trusty
then in the LTS releases is HardWare Enablement stacks:
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

```

dpkg -l | grep linux-

```
is one way to know what images are installed.

Getting deep now, as to what happens within "kernel space" when the image is built in ram prior to transfer to hard drive to what is termed "user space". That 'image' is built according to the 'image' that is selected in grub.
All that said, we can make any boot image the default if we so desire negating the requirement to manually select an image in grub.
All that is required is a simple edit to the config file /etc/default/grub line " GRUB_DEFAULT=0" in accord to the menu listing in the boot file /boot/grub/grub.cfg .

As to what you want to do .. all I can do is present options as I become aware of what you want to do. And catch 22, you can not know what you want to do until you are aware of the options, and I can not give you options until I know what you want to do.

Currently I think the 16.04 systemd install is broke - somewhere.
To find that where we need a terminal to examine what is not taking place.
Maybe a graphics driver ?
maybe corrupted config files in your user account 
maybe lightdm is broke
maybe mabe maybe

All we can do at this point is 'look' and ask the system what the situation is. We have to have some good direction to know what to ask of the system. And that my friend takes a (C)ommand (L)ine (I)nterface and a whole lot of thought to isolate the problem. To compound the issue, we need to boot up that broken instance to 'see' where it is broke .. The more I think the more it looks like bootup a liveDVD(USB) into a full CHange Root - after a failed boot attempt  may be a better way to proceed..... and read the log files of what took place. That is one option .
I say again, when all else fails; read the instructions.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-02
> **Bashing-om said:**
> gregg3; Uh Huh //

Bear in mind I advised you several posts back that you have indeed 16.04 operating system installed.
As to what 'image' you boot the operating system into .. well that is optional as per what kernel-images are installed.
4.4.0.21.22: == 16.04 xenial,
4.2.XXX     : == 15.10 wily
3.13.XXX   : == 14.04 trusty
then in the LTS releases is HardWare Enablement stacks:
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

```

dpkg -l | grep linux-

```
is one way to know what images are installed.

Getting deep now, as to what happens within "kernel space" when the image is built in ram prior to transfer to hard drive to what is termed "user space". That 'image' is built according to the 'image' that is selected in grub.
All that said, we can make any boot image the default if we so desire negating the requirement to manually select an image in grub.
All that is required is a simple edit to the config file /etc/default/grub line " GRUB_DEFAULT=0" in accord to the menu listing in the boot file /boot/grub/grub.cfg .

As to what you want to do .. all I can do is present options as I become aware of what you want to do. And catch 22, you can not know what you want to do until you are aware of the options, and I can not give you options until I know what you want to do.

Currently I think the 16.04 systemd install is broke - somewhere.
To find that where we need a terminal to examine what is not taking place.
Maybe a graphics driver ?
maybe corrupted config files in your user account 
maybe lightdm is broke
maybe mabe maybe

All we can do at this point is 'look' and ask the system what the situation is. We have to have some good direction to know what to ask of the system. And that my friend takes a (C)ommand (L)ine (I)nterface and a whole lot of thought to isolate the problem. To compound the issue, we need to boot up that broken instance to 'see' where it is broke .. The more I think the more it looks like bootup a liveDVD(USB) into a full CHange Root - after a failed boot attempt  may be a better way to proceed..... and read the log files of what took place. That is one option .
I say again, when all else fails; read the instructions.[INDENT][INDENT]which way did he go, George
[/INDENT]
[/INDENT]


Thanks. I wish I knew more about computers, Bashing-om. I really do. I read your post four times and I understand parts of it, but still feel I'm in over my head. Sorry I missed the 16.04 being installed in your post. I think it seemed a revelation when I ran Qlee's command and it brought that up.

I get, pretty much, the image thing. So 16.04 is installed, but it's just not accessible, right? And so we're Grub booting 15.10. So I'm just using my old 15.10, which is fine, which is great.

Okay, what I was doing before was using Xubuntu and getting the 6 month upgrades. It was fun, getting the latest versions of LibreOffice etc. Then this latest upgrade confused me because it offered *only*16.04_LTS_. Some friends explained that I had to get the 16.04LTS and then in October I could get back on the 6 month upgrade path. 

I would like to get back on that path. 

So what is the easiest, simplest way of doing that?

It seems to me  I can limp along GRUB booting 15.10 (and somehow make the transition to 16.04 in July when support ends for 15.10) or I can try to fix the 16.04. And to do that (it sounds like anyway) we need to do the > bootup a liveDVD(USB) into a full CHange Root. Is doing that safe? See, we've already lost the terminal doing the Grub boot for the 16.04. I would hate to lose the grub boot for the 15.10. Sorry for being such a chicken but this is my work computer. Losing it would be a major hit.

And I always  check the versions via: 

```
aptitude search linux-image |grep '^i' 
```and then I would remove the older ones with:

```
sudo aptitude remove
```

I'll list the results of your ```
dpkg -l | grep linux-
``` and the ```
aptitude search linux-image |grep '^i' 
``` just in case it sheds any light on things. 

Thanks.

```
gregg@LG:~/Desktop$ dpkg -l | grep linux-
ii  linux-base                                                  4.0ubuntu1                                          all          Linux image base package
ii  linux-firmware                                              1.157                                               all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.21.22                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-35                                      4.2.0-35.40                                         all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic                              4.2.0-35.40                                         amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.21.22                                         amd64        Generic Linux kernel headers
rc  linux-image-3.16.0-23-generic                               3.16.0-23.31                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-33-generic                               3.16.0-33.44                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-34-generic                               3.16.0-34.47                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-15-generic                               3.19.0-15.15                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-16-generic                               3.19.0-16.16                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-18-generic                               3.19.0-18.18                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-20-generic                               3.19.0-20.20                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-21-generic                               3.19.0-21.21                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-22-generic                               3.19.0-22.22                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-23-generic                               3.19.0-23.24                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-26-generic                               3.19.0-26.28                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-28-generic                               3.19.0-28.30                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-30-generic                               3.19.0-30.34                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-31-generic                               3.19.0-31.36                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-32-generic                               3.19.0-32.37                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-17-generic                                4.2.0-17.21                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-18-generic                                4.2.0-18.22                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-19-generic                                4.2.0-19.23                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-22-generic                                4.2.0-22.27                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-23-generic                                4.2.0-23.28                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-25-generic                                4.2.0-25.30                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                                4.2.0-27.32                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-30-generic                                4.2.0-30.36                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-34-generic                                4.2.0-34.39                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-35-generic                                4.2.0-35.40                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                         3.16.0-23.31                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-33-generic                         3.16.0-33.44                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-34-generic                         3.16.0-34.47                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                         3.19.0-15.15                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-16-generic                         3.19.0-16.16                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-18-generic                         3.19.0-18.18                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-20-generic                         3.19.0-20.20                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-21-generic                         3.19.0-21.21                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-22-generic                         3.19.0-22.22                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-23-generic                         3.19.0-23.24                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic                         3.19.0-30.34                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-17-generic                          4.2.0-17.21                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-18-generic                          4.2.0-18.22                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-19-generic                          4.2.0-19.23                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-22-generic                          4.2.0-22.27                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-23-generic                          4.2.0-23.28                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-25-generic                          4.2.0-25.30                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                          4.2.0-27.32                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                          4.2.0-30.36                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic                          4.2.0-34.39                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-35-generic                          4.2.0-35.40                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.21.22                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-21.37                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                               all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
gregg@LG:~/Desktop$ aptitude search linux-image |grep '^i'
i A linux-image-4.2.0-35-generic    - Linux kernel image for version 4.2.0 on 64
i A linux-image-4.4.0-21-generic    - Linux kernel image for version 4.4.0 on 64
i A linux-image-extra-4.2.0-35-gene - Linux kernel extra modules for version 4.2
i A linux-image-extra-4.4.0-21-gene - Linux kernel extra modules for version 4.4
i A linux-image-generic             - Generic Linux kernel image                
gregg@LG:~/Desktop$ 

```

---

### Post by Bashing-om on 2016-05-02
gregg3; Well ...........

This is the way:
> 
I wish I knew more about computers,

you get there .. use them, break them fix them. 
This forum also functions as an institution of higher learning. Ask an intelligent thought out question, and you will get a thoughtful response. By the way I commend you on your thoughtfulness.
You may open as many threads as you want .. One question to the thread . Forum threads like dead men -> one to the box .

> 
 16.04 is installed, but it's just not accessible, 

16.04 is accessible. You are using it now, just with the 15.10's- kernel. So far can even use 16.04 in the "upstart" mode . What we can not do is boot the 16.04 kernel in systemd mode. ( now that is what is strange !) 

> 
 October I could get back on the 6 month upgrade path. 

correct. soon as 16.10 is released // year 20(16) month 10 (October)

> 
And to do that (it sounds like anyway) we need to do the

CHange Root . Only as safe as we are careful . Extreme care to be exercised, one is 'root' in this environment. There is no forgiveness for an error. All I have in mind is to have some looksees at the logs and drivers and get back out - real quick .

so options:
a) leave as is and work from the 15.10 kernel
b) leave as is and work from the upstart mode of 16.04 kernel
c) find the fault in 16.04 systemd .
It is a possibility that with the 16.04 updates .. the problem might get resolved = possible but not too likely.

[INDENT][INDENT]time and effort
[INDENT][INDENT][INDENT]time and effort
[INDENT][INDENT][INDENT][INDENT]sometimes brain fluid also
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QLee on 2016-05-03
Phew, that was a lot to read to catch up. I want to state that it is great that Bashing-om takes the time to explain things, even if the thread title is incorrect there is a lot of information in this thread for people who are following along.

Greqq, it might clarify to realise that you are using the software versions of 16.04 but booted with an older kernel (the one you already had on your 14.04 system). [Edit] I mean your 15.10 system, I'm the one using that kernel on 14.04. 

My best guess of what happened is that during the upgrade, the transition to the new Radeon drivers didn't happen. (remember the section in the release notes for 16.04, after I saw the picture Gregg posted of his computer specs, I reread the release notes) I'd guess that's why the system is choking and giving that black screen. I don't know what the upgrade path developers planned into the upgrade to make that transition but Gregg's system is probably using the old xserver and fglrx drivers with the old kernel. Personally, I would try the recovery mode before doing the chroot. Recovery mode even has a failsafeX.

Good luck!

Bashing-om, I admire your enthusiasm and energy, you work very hard to help people here and we all learn in the process.

I put all the pieces back together, ...but, I've still got pieces left over!   ;-)

---

### Post by Bashing-om on 2016-05-03
@QLee : Hey ..

I do appreciate your knowledgeable inputs here .. 3 heads are better then one .. even if goat heads are involved - I can be as dense as a box of rocks. :)
> 
Bashing-om, I admire your enthusiasm and energy, you work very hard to help people here and we all learn in the process.

Problem solving, an exercise of the mind .. keeps me young. I am a strong proponent of open source, and nowhere is it better exemplified than in ubuntu; with it's great community of support in so many realms. I just try and do my part.

@gregg3; Yeah ..
There are many paths to any end in linux. Many times the difficulty is only in choosing the path of least resistance. We just want a terminal; however we can get it to give us access to the broken 16.04 -systemd- install. One way or another we find out what is not going on .. or where it is going astray. Path of least resistance is look at what might be 1st; authorizations, drivers, config files ?? The logs will relate a bunch !

[INDENT][INDENT]decisions decisions decisions
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-03
> **QLee said:**
> Phew, that was a lot to read to catch up. I want to state that it is great that Bashing-om takes the time to explain things, even if the thread title is incorrect there is a lot of information in this thread for people who are following along.

Greqq, it might clarify to realise that you are using the software versions of 16.04 but booted with an older kernel (the one you already had on your 14.04 system). [Edit] I mean your 15.10 system, I'm the one using that kernel on 14.04. 

My best guess of what happened is that during the upgrade, the transition to the new Radeon drivers didn't happen. (remember the section in the release notes for 16.04, after I saw the picture Gregg posted of his computer specs, I reread the release notes) I'd guess that's why the system is choking and giving that black screen. I don't know what the upgrade path developers planned into the upgrade to make that transition but Gregg's system is probably using the old xserver and fglrx drivers with the old kernel. Personally, I would try the recovery mode before doing the chroot. Recovery mode even has a failsafeX.

Good luck!

Bashing-om, I admire your enthusiasm and energy, you work very hard to help people here and we all learn in the process.

I put all the pieces back together, ...but, I've still got pieces left over!   ;-)

Thanks QLee. I appreciate the input. Also, in your second to last post, the idea of the computer being in an "in-between" state, seemed accurate.

---

### Post by gregg3 on 2016-05-03
> **Bashing-om said:**
> gregg3; Well ...........

This is the way:

you get there .. use them, break them fix them. 
This forum also functions as an institution of higher learning. Ask an intelligent thought out question, and you will get a thoughtful response. By the way I commend you on your thoughtfulness.
You may open as many threads as you want .. One question to the thread . Forum threads like dead men -> one to the box .


16.04 is accessible. You are using it now, just with the 15.10's- kernel. So far can even use 16.04 in the "upstart" mode . What we can not do is boot the 16.04 kernel in systemd mode. ( now that is what is strange !) 


correct. soon as 16.10 is released // year 20(16) month 10 (October)


CHange Root . Only as safe as we are careful . Extreme care to be exercised, one is 'root' in this environment. There is no forgiveness for an error. All I have in mind is to have some looksees at the logs and drivers and get back out - real quick .

so options:
a) leave as is and work from the 15.10 kernel
b) leave as is and work from the upstart mode of 16.04 kernel
c) find the fault in 16.04 systemd .
It is a possibility that with the 16.04 updates .. the problem might get resolved = possible but not too likely.[INDENT][INDENT]time and effort[INDENT][INDENT][INDENT]time and effort[INDENT][INDENT][INDENT][INDENT]sometimes brain fluid also
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks Bashing-om.

I need to think ahead. Because I knew I had to upgrade to 16.04 by July, but since I'm already in 16.04, the July deadline is meaningless and I only need to think about October 2016 and doing something then, right? (Even if I leave as is and work from the 15.10 kernel?)

Are you sure I can work from the upstart mode of 16.04? And that would be the ```
4.4.0-21-generic (upstart)
``` entry in the GRUB menu (see screenshot)?

And I re-read your post and Googled around but what would effectively be the difference between working in the 15.10 kernel and the upstart mode of the 16.04 kernel? 

And again, with my amateur sleuthing, to my understanding, systemd and upstart are interchangeable. Yes, systemd is newer but some people still prefer upstart, and upstart seems fully functional. (In other words, it doesn't seem like I'd be giving anything up by working in 16.04 upstart, right?)

You don't think the recovery mode is a good option to pursue? (My *only* indication that it might be is the name.)

I like the idea of updates solving the problem (LOL) but would I need to be in the 16.04 upstart mode for them to take effect?

If I go the 16.04 upstart mode route (or the 15.10 route, for that matter) then we can work it so the 16.04 upstart boots from the power button, rather than the GRUB menu, right?

If we try to find the fault in 16.04 systemd via the change root, what is the worst that can happen?

Thanks.

---

### Post by Bashing-om on 2016-05-03
gregg3; Hey ;

Let's put some perspective in this your work system. As a work system you should value stability above all other considerations, right ?
Now that stability means (L)ong (T)erm (S)upport .. that is 16.04 for 5 years !
And you also like cutting edge ... well you can get the best of both IF you dual boot .
say the ole work horse is 16.04 with 5 years support, installed as the main primary operating system
and the play-around-test system are those interim releases that last only 9 months - 16.10 to be for instance that have a 6 month release upgrade cycle. -> that works for me !

Present circumstance, as to what you want to do:
4.4.0-21-generic (upstart) ;
You had formerly advised , I seem to recall, that the system functions perfectly booting this mode . So use it vice systemd. Yes we can make it the default merely making an edit to the default file. There is no drawback as far s I am aware to using upstart .
> 
And I re-read your post and Googled around but what would effectively be the difference between working in the 15.10 kernel and the upstart mode of the 16.04 kernel?

effectively, there is no difference .

No mater the kernel that you are booting the 16.04 operating system with .. all updates will still be available and will be applied to the system at large.

As I understand this condition, the only thing non-functional is systemd booting the current/latest kernel.
That said, the only way I know to find the fault is to boot it, no terminal availability within the operating system then we get this terminal from another system by changing the root from the working system into that of the broken 16.04 and looking at what might be. The only danger here is doing something thoughtless or careless - we are not going to do that, are we ? At this point we are only looking with no intent to change anything .
Recovery mode; the default is to mount the file system read only - in this state can not do any damage to the operating system. Again presently all we are doing is looking and seeking to find.

[INDENT][INDENT]it is your time, your effort
[INDENT][INDENT][INDENT]both of our learning curves[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-03
> **Bashing-om said:**
> gregg3; Hey ;

Let's put some perspective in this your work system. As a work system you should value stability above all other considerations, right ?
Now that stability means (L)ong (T)erm (S)upport .. that is 16.04 for 5 years !
And you also like cutting edge ... well you can get the best of both IF you dual boot .
say the ole work horse is 16.04 with 5 years support, installed as the main primary operating system
and the play-around-test system are those interim releases that last only 9 months - 16.10 to be for instance that have a 6 month release upgrade cycle. -> that works for me !

Thanks Bashing-om. Good suggestion but I know myself well enough that I'm not going to be flipping back and forth between the short-term and LTS versions. I like the short-term versions. And I've never had any problems upgrading before. I just want to get back on that short-term release train.

> **Bashing-om said:**
> 

Present circumstance, as to what you want to do:
4.4.0-21-generic (upstart) ;
You had formerly advised , I seem to recall, that the system functions perfectly booting this mode . So use it vice systemd. Yes we can make it the default merely making an edit to the default file. There is no drawback as far s I am aware to using upstart .

effectively, there is no difference .

No, I never ran the 4.4.0-21-generic (upstart). So I decided to run it now and nothing happened. Just the blank "No Input Signal" stuff. So the only one I know that works is 4.2.0-35-generic. I have not tried 4.2.0-35-generic (upstart).

> **Bashing-om said:**
> 

No mater the kernel that you are booting the 16.04 operating system with .. all updates will still be available and will be applied to the system at large.



That's good. And it will be good to--eventually--do that default where the computer boots up with the power switch, rather than having to go through the GRUB menu.

> **Bashing-om said:**
> 

As I understand this condition, the only thing non-functional is systemd booting the current/latest kernel.



As I said, that is not the case. 
> **Bashing-om said:**
> 

That said, the only way I know to find the fault is to boot it, no terminal availability within the operating system then we get this terminal from another system by changing the root from the working system into that of the broken 16.04 and looking at what might be. The only danger here is doing something thoughtless or careless - we are not going to do that, are we ? At this point we are only looking with no intent to change anything .
Recovery mode; the default is to mount the file system read only - in this state can not do any damage to the operating system. 

I am game, my friend. I don't know if not having the 4.4.0-21-generic (upstart) changes the scenario though.
> **Bashing-om said:**
> 

Again presently all we are doing is looking and seeking to find.[INDENT][INDENT]it is your time, your effort[INDENT][INDENT][INDENT]both of our learning curves[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Yes, but you are a Linux Zen Master and I am just in over my head! :)

---

### Post by Bashing-om on 2016-05-03
gregg3; K;

Lets make the 15.10 kernel the default.
Post again anew:
```

dpkg -l | grep linux-
cat /boot/grub/grub.cfg

```
and we can match kernel to config file line number ... and edit /etc/default/grub to make it so.

And hey:
> 
Yes, but you are a Linux Zen Master and I am just in over my head!


Nawwww ... I just been around a bit .. broke my system a few times and learned what it takes to fix it. You hang in here and next you will be teaching me. Now there are some Linux Zen Masters around (here), but it ain't me you should be think'n of . Me be that lowly 1st responder .

[INDENT][INDENT]nothing happens;
[INDENT][INDENT][INDENT]that together
[INDENT][INDENT][INDENT]we can not finger out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-04
> **Bashing-om said:**
> gregg3; K;

Lets make the 15.10 kernel the default.


Sounds good.

> **Bashing-om said:**
> 

Post again anew:
```

dpkg -l | grep linux-
cat /boot/grub/grub.cfg

```

```

gregg@LG:~/Desktop$ dpkg -l | grep linux-
ii  linux-base                                                  4.0ubuntu1                                          all          Linux image base package
ii  linux-firmware                                              1.157                                               all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.21.22                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-35                                      4.2.0-35.40                                         all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic                              4.2.0-35.40                                         amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.21.22                                         amd64        Generic Linux kernel headers
rc  linux-image-3.16.0-23-generic                               3.16.0-23.31                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-33-generic                               3.16.0-33.44                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-34-generic                               3.16.0-34.47                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-15-generic                               3.19.0-15.15                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-16-generic                               3.19.0-16.16                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-18-generic                               3.19.0-18.18                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-20-generic                               3.19.0-20.20                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-21-generic                               3.19.0-21.21                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-22-generic                               3.19.0-22.22                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-23-generic                               3.19.0-23.24                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-26-generic                               3.19.0-26.28                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-28-generic                               3.19.0-28.30                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-30-generic                               3.19.0-30.34                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-31-generic                               3.19.0-31.36                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-32-generic                               3.19.0-32.37                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-17-generic                                4.2.0-17.21                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-18-generic                                4.2.0-18.22                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-19-generic                                4.2.0-19.23                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-22-generic                                4.2.0-22.27                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-23-generic                                4.2.0-23.28                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-25-generic                                4.2.0-25.30                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                                4.2.0-27.32                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-30-generic                                4.2.0-30.36                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-34-generic                                4.2.0-34.39                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-35-generic                                4.2.0-35.40                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                         3.16.0-23.31                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-33-generic                         3.16.0-33.44                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-34-generic                         3.16.0-34.47                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                         3.19.0-15.15                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-16-generic                         3.19.0-16.16                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-18-generic                         3.19.0-18.18                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-20-generic                         3.19.0-20.20                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-21-generic                         3.19.0-21.21                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-22-generic                         3.19.0-22.22                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-23-generic                         3.19.0-23.24                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic                         3.19.0-30.34                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-17-generic                          4.2.0-17.21                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-18-generic                          4.2.0-18.22                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-19-generic                          4.2.0-19.23                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-22-generic                          4.2.0-22.27                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-23-generic                          4.2.0-23.28                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-25-generic                          4.2.0-25.30                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                          4.2.0-27.32                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                          4.2.0-30.36                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic                          4.2.0-34.39                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-35-generic                          4.2.0-35.40                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.21.22                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-21.37                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                               all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
gregg@LG:~/Desktop$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
else
  search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
gregg@LG:~/Desktop$ 
```


> **Bashing-om said:**
> 


and we can match kernel to config file line number ... and edit /etc/default/grub to make it so.

And hey:


Nawwww ... I just been around a bit .. broke my system a few times and learned what it takes to fix it. You hang in here and next you will be teaching me. Now there are some Linux Zen Masters around (here), but it ain't me you should be think'n of . Me be that lowly 1st responder .[INDENT][INDENT]nothing happens;[INDENT][INDENT][INDENT]that together[INDENT][INDENT][INDENT]we can not finger out
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks, man!

---

### Post by Bashing-om on 2016-05-04
gregg3; Hey !

I am beginning to get a glimmer of what is not going on here ! Maybe !
Consider:
You do have xenial (16.04) installed, BUT the latest kernel installed is wily's (15.10) kernel from the HardWare Enablement stack - linux-image-4.2.0-35-generic  - // Now xenial runs kernel 4.4.0.21.22: I can accept that HWE is not playing nice with xenial's X layer !

Before we set up to change the default boot kernel .. let us get the correct kernel installed ! 
Then see what happens.
Let's see if the package manager will do this feat of installing the correct kernel .
Do in any booted kernel:
```

sudo apt update
sudo apt full-upgrade
sudo update-grub

```
show us these outputs .. if the 4.4.XX kernel does not install .. we take matters into our own hands.

[INDENT][INDENT]I see said the blind man
[/INDENT][/INDENT]

Edit :
Ouch !  Failure to see that " ii  linux-image-4.4.0-21-generic " is in fact installed among all the clutter of removed stuff . Run the above anyway .. to see if there is any change, Tunnel vision .. look before I leap to a conclusion .

reaching reaching reaching .

---

### Post by gregg3 on 2016-05-04
> **Bashing-om said:**
> gregg3; Hey !

I am beginning to get a glimmer of what is not going on here ! Maybe !
Consider:
You do have xenial (16.04) installed, BUT the latest kernel installed is wily's (15.10) kernel from the HardWare Enablement stack - linux-image-4.2.0-35-generic  - // Now xenial runs kernel 4.4.0.21.22: I can accept that HWE is not playing nice with xenial's X layer !

Before we set up to change the default boot kernel .. let us get the correct kernel installed ! 
Then see what happens.
Let's see if the package manager will do this feat of installing the correct kernel .
Do in any booted kernel:
```

sudo apt update
sudo apt full-upgrade
sudo update-grub

```
show us these outputs .. if the 4.4.XX kernel does not install .. we take matters into our own hands.[INDENT][INDENT]I see said the blind man
[/INDENT]
[/INDENT]

Edit :
Ouch !  Failure to see that " ii  linux-image-4.4.0-21-generic " is in fact installed among all the clutter of removed stuff . Run the above anyway .. to see if there is any change, Tunnel vision .. look before I leap to a conclusion .

reaching reaching reaching .

Okay, Bashing-om. Here's the results. Now since it's an upgrade when it was done it's telling me to restart the computer, so I'll re-start it and see what happens, which should be interesting, because it should start via 4.4.0-21, right? I'll report back after the re-start. Thanks.
```

gregg@LG:~/Desktop$ sudo apt update
[sudo] password for gregg: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [92.2 kB]
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [93.3 kB]   
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:6 http://dl.google.com/linux/chrome/deb stable Release
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Sources [14.1 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Sources [1,996 B]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [43.4 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [43.3 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [16.6 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [10.4 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [10.4 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [7,276 B]
Fetched 333 kB in 0s (348 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
23 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: There is no public key available for the following key IDs:
1397BC53640DB551
gregg@LG:~/Desktop$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bind9-host dnsutils gnome-software gnome-software-common libbind9-140 libdns-export162 libdns162 libisc-export160 libisc160 libisccc140 libisccfg140 liblwres141 libsmbclient
  libssl1.0.0 libssl1.0.0:i386 libtasn1-6 libtasn1-6:i386 libtevent0 libwbclient0 openssl samba-libs ubuntu-drivers-common xinit
23 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.6 MB of archives.
After this operation, 10.2 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libtevent0 amd64 0.9.28-0ubuntu0.16.04.1 [26.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 samba-libs amd64 2:4.3.9+dfsg-0ubuntu0.16.04.1 [5,172 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwbclient0 amd64 2:4.3.9+dfsg-0ubuntu0.16.04.1 [30.4 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsmbclient amd64 2:4.3.9+dfsg-0ubuntu0.16.04.1 [53.3 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-drivers-common amd64 1:0.4.17.1 [48.4 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libisc-export160 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [152 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdns-export162 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [665 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libssl1.0.0 amd64 1.0.2g-1ubuntu4.1 [1,122 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libssl1.0.0 i386 1.0.2g-1ubuntu4.1 [949 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 libtasn1-6 i386 4.7-3ubuntu0.16.04.1 [45.4 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libtasn1-6 amd64 4.7-3ubuntu0.16.04.1 [43.2 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dnsutils amd64 1:9.10.3.dfsg.P4-8ubuntu1 [89.1 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 bind9-host amd64 1:9.10.3.dfsg.P4-8ubuntu1 [38.4 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libisc160 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [214 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdns162 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [877 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libisccc140 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [16.3 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libisccfg140 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [40.5 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 liblwres141 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [33.0 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libbind9-140 amd64 1:9.10.3.dfsg.P4-8ubuntu1 [23.6 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 openssl amd64 1.0.2g-1ubuntu4.1 [491 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-software amd64 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 [225 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-software-common all 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 [2,257 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 xinit amd64 1.3.4-3ubuntu0.1 [18.3 kB]
Fetched 12.6 MB in 5s (2,265 kB/s)
Preconfiguring packages ...
(Reading database ... 259477 files and directories currently installed.)
Preparing to unpack .../libtevent0_0.9.28-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libtevent0:amd64 (0.9.28-0ubuntu0.16.04.1) over (0.9.26-3) ...
Preparing to unpack .../samba-libs_2%3a4.3.9+dfsg-0ubuntu0.16.04.1_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.3.9+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ...
Preparing to unpack .../libwbclient0_2%3a4.3.9+dfsg-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libwbclient0:amd64 (2:4.3.9+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ...
Preparing to unpack .../libsmbclient_2%3a4.3.9+dfsg-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libsmbclient:amd64 (2:4.3.9+dfsg-0ubuntu0.16.04.1) over (2:4.3.8+dfsg-0ubuntu1) ...
Preparing to unpack .../ubuntu-drivers-common_1%3a0.4.17.1_amd64.deb ...
Unpacking ubuntu-drivers-common (1:0.4.17.1) over (1:0.4.17) ...
Preparing to unpack .../libisc-export160_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libdns-export162_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libssl1.0.0_1.0.2g-1ubuntu4.1_amd64.deb ...
De-configuring libssl1.0.0:i386 (1.0.2g-1ubuntu4) ...
Unpacking libssl1.0.0:amd64 (1.0.2g-1ubuntu4.1) over (1.0.2g-1ubuntu4) ...
Preparing to unpack .../libssl1.0.0_1.0.2g-1ubuntu4.1_i386.deb ...
Unpacking libssl1.0.0:i386 (1.0.2g-1ubuntu4.1) over (1.0.2g-1ubuntu4) ...
Preparing to unpack .../libtasn1-6_4.7-3ubuntu0.16.04.1_i386.deb ...
De-configuring libtasn1-6:amd64 (4.7-3) ...
Unpacking libtasn1-6:i386 (4.7-3ubuntu0.16.04.1) over (4.7-3) ...
Preparing to unpack .../libtasn1-6_4.7-3ubuntu0.16.04.1_amd64.deb ...
Unpacking libtasn1-6:amd64 (4.7-3ubuntu0.16.04.1) over (4.7-3) ...
Preparing to unpack .../dnsutils_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking dnsutils (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../bind9-host_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking bind9-host (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libisc160_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libisc160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libdns162_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libdns162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libisccc140_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libisccc140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libisccfg140_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libisccfg140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../liblwres141_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking liblwres141:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../libbind9-140_1%3a9.10.3.dfsg.P4-8ubuntu1_amd64.deb ...
Unpacking libbind9-140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) over (1:9.10.3.dfsg.P4-8) ...
Preparing to unpack .../openssl_1.0.2g-1ubuntu4.1_amd64.deb ...
Unpacking openssl (1.0.2g-1ubuntu4.1) over (1.0.2g-1ubuntu4) ...
Preparing to unpack .../gnome-software_3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1_amd64.deb ...
Unpacking gnome-software (3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1) over (3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2) ...
Preparing to unpack .../gnome-software-common_3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1_all.deb ...
Unpacking gnome-software-common (3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1) over (3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2) ...
Preparing to unpack .../xinit_1.3.4-3ubuntu0.1_amd64.deb ...
Unpacking xinit (1.3.4-3ubuntu0.1) over (1.3.4-3) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.48.0-1ubuntu4) ...
Processing triggers for libglib2.0-0:amd64 (2.48.0-1ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up libtevent0:amd64 (0.9.28-0ubuntu0.16.04.1) ...
Setting up libwbclient0:amd64 (2:4.3.9+dfsg-0ubuntu0.16.04.1) ...
Setting up samba-libs:amd64 (2:4.3.9+dfsg-0ubuntu0.16.04.1) ...
Setting up libsmbclient:amd64 (2:4.3.9+dfsg-0ubuntu0.16.04.1) ...
Setting up ubuntu-drivers-common (1:0.4.17.1) ...
Setting up libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.2g-1ubuntu4.1) ...
Setting up libssl1.0.0:amd64 (1.0.2g-1ubuntu4.1) ...
Setting up libtasn1-6:amd64 (4.7-3ubuntu0.16.04.1) ...
Setting up libtasn1-6:i386 (4.7-3ubuntu0.16.04.1) ...
Setting up libisc160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up libdns162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up libisccc140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up libisccfg140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up libbind9-140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up liblwres141:amd64 (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up bind9-host (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up dnsutils (1:9.10.3.dfsg.P4-8ubuntu1) ...
Setting up openssl (1.0.2g-1ubuntu4.1) ...
Setting up gnome-software-common (3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1) ...
Setting up gnome-software (3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1) ...
Setting up xinit (1.3.4-3ubuntu0.1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
gregg@LG:~/Desktop$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
gregg@LG:~/Desktop$ 
```

---

### Post by Bashing-om on 2016-05-04
gregg3; Well ..

I see nutin that directly applies to our situation .,.. but who knows ... maybe ?

Awaiting the outcome before editing grub's config file .

[INDENT][INDENT]if at 1st you do not succeed
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-04
Okay. I'm back. I hit the restart button and the red light came on my computer (which is typical during a restart) and stayed on for maybe two minutes, but then the "No input signal" window came on and then the black screen (and nothing).

I was still able to grub boot from 4.2.0-35-generic.

---

### Post by Bashing-om on 2016-05-04
gregg3; Ho Kay, Not .

Set up to boot the desired kernel .

We will edit a system file . Always make a backup 1st of any file that is to be edited. Never can tell what might per chance - power outages !
```

sudo cp /etc/default/grub /etc/default/grub-04may2016

```
edit the file:
```

sudo -H gedit /etc/default/grub

```

> 
[color=blue]#0[/color]menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
[color=blue]#1[/color]submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
[color=blue]#2[/color]    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
[color=blue]#3[/color]    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
 [color=blue]#4[/color]   menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail



The first uncommented line "GRUB_DEFAULT=0"
change the "0" to 4 . In accordance with where the boot entry is located in the /boot/ grub/grub.cfg file - above.

And propagate the change:
```

sudo uppdate-grub

```

reboot now. do it workie like you want it to ? Booting by default now the  4.2.0-35- kernel.

Then .. back to finding out why the xenial kernel fails to boot .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-04
> **Bashing-om said:**
> gregg3; Ho Kay, Not .

Set up to boot the desired kernel .

We will edit a system file . Always make a backup 1st of any file that is to be edited. Never can tell what might per chance - power outages !
```

sudo cp /etc/default/grub /etc/default/grub-04may2016

```
edit the file:
```

sudo -H gedit /etc/default/grub

```



The first uncommented line "GRUB_DEFAULT=0"
change the "0" to 4 . In accordance with where the boot entry is located in the /boot/ grub/grub.cfg file - above.

And propagate the change:
```

sudo uppdate-grub

```

reboot now. do it workie like you want it to ? Booting by default now the  4.2.0-35- kernel.

Then .. back to finding out why the xenial kernel fails to boot .[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


Thanks Bashing-om. I just need you to clarify these two sentences.

> The first uncommented line "GRUB_DEFAULT=0"
change the "0" to 4 . In accordance with where the boot entry is located in the /boot/ grub/grub.cfg file - above.


An "uncommented line" will not have a "#" in front of it?

So I use the 
```
sudo -H gedit /etc/default/grub
```

command and the file opens. 

Then I find the first time this ```
GRUB_DEFAULT=0
``` appears.

Then I find ```
GRUB_DEFAULT=0
``` each place where you have those blue numbers? 

And is my grub file going to look like the data you posted? Because I don't see any ```
GRUB_DEFAULT=0
``` occurrences in the data you posted.

Would I be making the 0 to 4 change five times (For the blue [COLOR=#0000ff]#0[/COLOR], [COLOR=#0000ff]#1[/COLOR], [COLOR=#0000ff]#2[/COLOR], [COLOR=#0000ff]#3[/COLOR], [COLOR=#0000ff]#4[/COLOR] in your data)?

And am I going to have gedit? (I have edited with Nano--once--before but not gedit.)

And in Nano it's kind of complicated saving things, but in your instructions, I should just make the changes and then run  


```
sudo uppdate-grub
``` ?

No special saving process?

Thanks.

---

### Post by Bashing-om on 2016-05-04
gregg3; Ouch ..

Regret my directive was so so unclear .
The only file you will change is /etc/default/grub .
There is but the one occurrence of the subject line.
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0[color=red] <- this line here [/color]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""
<snip>

```

I did the colorization in our reference boot file to show my work .. and to make sure I got the count/number correct .

And YES, when the edit is done ... SAVE the file, save the file !
When done do not forget to :
```

sudo update-grub

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-04
> **Bashing-om said:**
> gregg3; Ouch ..

Regret my directive was so so unclear .
The only file you will change is /etc/default/grub .
There is but the one occurrence of the subject line.
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0[COLOR=red] <- this line here [/COLOR]
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""
<snip>

```

I did the colorization in our reference boot file to show my work .. and to make sure I got the count/number correct .

And YES, when the edit is done ... SAVE the file, save the file !
When done do not forget to :
```

sudo update-grub

```[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Ok, thanks for the clarification. I had to get gedit (and actually it looks easier to use than Nano was), but when I deleted the "0" I got a warning. So I put the "4" back in and exited gedit without saving. Here's how it looked in the terminal:
```

gregg@LG:~/Desktop$ sudo cp /etc/default/grub /etc/default/grub-04may2016
[sudo] password for gregg: 
gregg@LG:~/Desktop$ sudo -H gedit /etc/default/grub
sudo: gedit: command not found
gregg@LG:~/Desktop$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libpeas-1.0-0 libpeas-1.0-0-python3loader libpeas-common
Suggested packages:
  gedit-plugins
The following NEW packages will be installed:
  gedit gedit-common gir1.2-gtksource-3.0 gir1.2-peas-1.0 libpeas-1.0-0 libpeas-1.0-0-python3loader libpeas-common
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 632 kB of archives.
After this operation, 5,745 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libpeas-common all 1.16.0-1ubuntu2 [13.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libpeas-1.0-0 amd64 1.16.0-1ubuntu2 [47.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 gir1.2-gtksource-3.0 amd64 3.18.2-1 [17.1 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 gedit-common all 3.18.3-0ubuntu4 [131 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 gir1.2-peas-1.0 amd64 1.16.0-1ubuntu2 [5,678 B]
Get:6 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libpeas-1.0-0-python3loader amd64 1.16.0-1ubuntu2 [11.1 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 gedit amd64 3.18.3-0ubuntu4 [406 kB]
Fetched 632 kB in 0s (1,325 kB/s)
Selecting previously unselected package libpeas-common.
(Reading database ... 259477 files and directories currently installed.)
Preparing to unpack .../libpeas-common_1.16.0-1ubuntu2_all.deb ...
Unpacking libpeas-common (1.16.0-1ubuntu2) ...
Selecting previously unselected package libpeas-1.0-0:amd64.
Preparing to unpack .../libpeas-1.0-0_1.16.0-1ubuntu2_amd64.deb ...
Unpacking libpeas-1.0-0:amd64 (1.16.0-1ubuntu2) ...
Selecting previously unselected package gir1.2-gtksource-3.0:amd64.
Preparing to unpack .../gir1.2-gtksource-3.0_3.18.2-1_amd64.deb ...
Unpacking gir1.2-gtksource-3.0:amd64 (3.18.2-1) ...
Selecting previously unselected package gedit-common.
Preparing to unpack .../gedit-common_3.18.3-0ubuntu4_all.deb ...
Unpacking gedit-common (3.18.3-0ubuntu4) ...
Selecting previously unselected package gir1.2-peas-1.0:amd64.
Preparing to unpack .../gir1.2-peas-1.0_1.16.0-1ubuntu2_amd64.deb ...
Unpacking gir1.2-peas-1.0:amd64 (1.16.0-1ubuntu2) ...
Selecting previously unselected package libpeas-1.0-0-python3loader.
Preparing to unpack .../libpeas-1.0-0-python3loader_1.16.0-1ubuntu2_amd64.deb ...
Unpacking libpeas-1.0-0-python3loader (1.16.0-1ubuntu2) ...
Selecting previously unselected package gedit.
Preparing to unpack .../gedit_3.18.3-0ubuntu4_amd64.deb ...
Unpacking gedit (3.18.3-0ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for libglib2.0-0:i386 (2.48.0-1ubuntu4) ...
Processing triggers for libglib2.0-0:amd64 (2.48.0-1ubuntu4) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libpeas-common (1.16.0-1ubuntu2) ...
Setting up libpeas-1.0-0:amd64 (1.16.0-1ubuntu2) ...
Setting up gir1.2-gtksource-3.0:amd64 (3.18.2-1) ...
Setting up gedit-common (3.18.3-0ubuntu4) ...
Setting up gir1.2-peas-1.0:amd64 (1.16.0-1ubuntu2) ...
Setting up libpeas-1.0-0-python3loader (1.16.0-1ubuntu2) ...
Setting up gedit (3.18.3-0ubuntu4) ...
update-alternatives: using /usr/bin/gedit to provide /usr/bin/gnome-text-editor (gnome-text-editor) in auto mode
Processing triggers for libc-bin (2.23-0ubuntu3) ...
gregg@LG:~/Desktop$ sudo -H gedit /etc/default/grub

(gedit:3222): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:3222): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
gregg@LG:~/Desktop$ 
```

---

### Post by Bashing-om on 2016-05-04
gregg3; Sheeshhh ...

I did not realize that you would have to go through such hassle - I had "assumed" a standard ubuntu install and that 'gedit' was installed . Now you may have a bunch of libs/dependencies installed that you did not want. The nano editor would have been just fine to edit that file !

The advisories when opening gedit are warnings .. not errors .. the editor should work just fine for this application. BUT, use the editor you are the more comfortable with . 


[INDENT]2 steps back
[INDENT][INDENT]1 forward
[/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-04
> **Bashing-om said:**
> gregg3; Sheeshhh ...

I did not realize that you would have to go through such hassle - I had "assumed" a standard ubuntu install and that 'gedit' was installed . Now you may have a bunch of libs/dependencies installed that you did not want. The nano editor would have been just fine to edit that file !

The advisories when opening gedit are warnings .. not errors .. the editor should work just fine for this application. BUT, use the editor you are the more comfortable with .[INDENT]2 steps back[INDENT][INDENT]1 forward
[/INDENT]
[/INDENT]
[/INDENT]


Well, seeing that I've never used gedit and have used nano only once years ago, I don't think I can say I'm "comfortable" LOL using any editor.

Well, I'm pretty scared off by the gedit warnings. A preliminary question: should I uninstall gedit. If so via:

```
sudo apt-get uninstall gedit 
``` or via Synaptic or the Ubuntu Software Center?

As always there seem to be so many way of doing things. (eg. uninstalling just gedit or its dependencies, as in this link:

[http://installion.co.uk/ubuntu/vivid/main/g/gedit/uninstall/index.html](http://installion.co.uk/ubuntu/vivid/main/g/gedit/uninstall/index.html)

(I normally use Mousepad or Kate when I use an editor with a GUI and have never needed gedit for anything.)

Next question: I don't know how to open a file using nano. Would I (adapting 
```
sudo -H gedit /etc/default/grub
``` use ```
sudo -H nano /etc/default/grub
```?

Then saving it in nano is funky. Is it ctrl+x and then 'save'?

And although the computer works great, I've noticed that every so often when I click on a tab in Firefox, a new Firefox *browser* opens 
with whatever was on that tab. Don't know if it has anything to do with any of this but I figured I'd mention it in case it did. Thanks.

---

### Post by Bashing-om on 2016-05-04
gregg3; Erk ...

Back me up .. and reqroup.
As this is not a standard ubuntu install .. what is it ?
What Desk Top environment are we in if not unity ? and what Display Manager if not lightdm ?
If you have kate - my ole favorite WYSIWYG editor - well use that  or whatever other editor is installed .

As to removing gedit .. maybe easier said than done ... dependencies.
Autoremove .. NO ! mot yet ! No, not till we are solid and stable with 16.04 kernel . Then ueah .. I am aware of some housecleaning I do want to get done ... all those 'rc' packages !
You might find that you like and prefer gedit as the editor of choice .
One can start with:
```

sudo apt remove gedit

```
Or 'purge' .
what was also installed:
> 
gir1.2-gtksource-3.0 gir1.2-peas-1.0 libpeas-1.0-0 libpeas-1.0-0-python3loader libpeas-common

we would have to play it by ear and see what else is affected when removing.

nano: 
Open the file
```

sudo nano /etc/default/grub

```
as nano is a CLI tool, we need not be concerned with containing ( sudo -H) sudo ( root privileges ) to the user environment acting on a GUI application.
it is xtl+o to write out (save), and ctl+x to exit nano.

Firefox: 
> 
every so often when I click on a tab in Firefox, a new Firefox browser opens 
with whatever was on that tab.

"every so often" ouch beats me .. tough to make a call on sometimes.
I would think that removing your preference file and restarting .. would regenerate preference to default values. I can not see that related to our present focus(s)

[INDENT]STOP ==>
[INDENT][INDENT][INDENT](S)queel (T)ires (O)n (P)avement
[INDENT][INDENT][INDENT]Green light now ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-05
> **Bashing-om said:**
> gregg3; Erk ...

Back me up .. and reqroup.
As this is not a standard ubuntu install .. what is it ? 

Hey Bashing-om. I don't know how to answer that question. I'll guess. I intially installed a Xubuntu short-term version distro on the computer with a bootable live USB drive. Then just did the upgrades as they came along. 

> **Bashing-om said:**
> 
What Desk Top environment are we in if not unity ? 

Xfce.

> **Bashing-om said:**
> 
and what Display Manager if not lightdm ?

It is lightdm

> **Bashing-om said:**
> 

As to removing gedit .. maybe easier said than done ... dependencies.
Autoremove .. NO ! mot yet ! No, not till we are solid and stable with 16.04 kernel . Then ueah .. I am aware of some housecleaning I do want to get done ... all those 'rc' packages !
You might find that you like and prefer gedit as the editor of choice .
One can start with:
```

sudo apt remove gedit

```
Or 'purge' .
what was also installed:

we would have to play it by ear and see what else is affected when removing.



I decided to leave gedit.

> **Bashing-om said:**
> 

nano: 
Open the file
```

sudo nano /etc/default/grub

```
as nano is a CLI tool, we need not be concerned with containing ( sudo -H) sudo ( root privileges ) to the user environment acting on a GUI application.
it is xtl+o to write out (save), and ctl+x to exit nano.



I did the above and exited out of nano. Then I realized I did not run 
```
sudo update-grub
```

So I opened the terminal back up and ran it and got this:
```

gregg@LG:~/Desktop$ sudo uppdate-grub
[sudo] password for gregg: 
sudo: uppdate-grub: command not found
gregg@LG:~/Desktop$ 
```

And I agree that the Firefox issue is not related to this.

Thanks.

---

### Post by Bashing-om on 2016-05-05
gregg3; K;

I find that gedit does very well for my use case . Fast and simple remains nano .

Try again:
> 
sudo uppdate-grub: command not found
sudo update-grub

As smart as 'buntu is .. still can not read your mind ... yet. That additional 'p' in the command .. the command then is not valid.

verify the edit 'took' and the file is as required.
then 
```

sudo update-grub

```
reboot to see the effect . I do expect that the 15.10 kernel is now the default booting kernel.

[INDENT][INDENT]Hold your mouth right
[INDENT][INDENT][INDENT]keep your fingers off the button
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-05
> **Bashing-om said:**
> gregg3; K;

I find that gedit does very well for my use case . Fast and simple remains nano .

Try again:

As smart as 'buntu is .. still can not read your mind ... yet. That additional 'p' in the command .. the command then is not valid.

verify the edit 'took' and the file is as required.
then 
```

sudo update-grub

```
reboot to see the effect . I do expect that the 15.10 kernel is now the default booting kernel.[INDENT][INDENT]Hold your mouth right[INDENT][INDENT][INDENT]keep your fingers off the button
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Ha ha. You would think Ubuntu would cut me a break! Ha ha. 

Here's what it wrought:
```

gregg@LG:~/Desktop$ sudo update-grub
[sudo] password for gregg: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found linux image: /boot/vmlinuz-4.2.0-35-generic
Found initrd image: /boot/initrd.img-4.2.0-35-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
gregg@LG:~/Desktop$ 
```

I'll reboot now and report back with results.

Thanks.

---

### Post by gregg3 on 2016-05-05
Okay. A mixed bag. When I rebooted, it looked like the same old same old. (The normal reboot, and startups for that matter, has the blue Xubuntu screen come on--and these reboots, and startups from the one I just did and the grub startups, go straight to a black screen and the "no input signal" and only then,  after maybe a minute, does the screen start populating (it starts with the clock and toolbar).) So back to this latest reboot--the screen went black and the "no input signal" came on. It seemed like the computer was loading (the red light was flashing, which indicates loading) but then after a couple of minutes, it gave up. I waited a few more minutes, then thinking it wouldn't come back up I left for a while. When I came back in about 20 minutes to my surprise the computer was on, the screen fully populated with icons, all normal.

I then shut the computer down. Then I started it and simultaneously set a stopwatch. I waited 17 minutes and nothing so I powered the computer off.

Then I started the computer again via GRUB (choosing: 4.2.0-35-generic) and  the computer came on in about 2 minutes.

---

### Post by Bashing-om on 2016-05-05
gregg3; Yuk ..

Now that just does not compute . Should workie .

All I can think of is to boot up letting the system choose the kernel to boot ( should boot 4.2.0-35-generic) and let's look at what is set once it finally boots:
```

uname -r
cat /etc/default/grub
cat /boot/grub/grub.cfg

```

Maybe time to bite the bullet and remove all the cruft on the system; but I can not be certain there will not be unwanted side effects. The good news is that I only see 2 kernels installed .. so 'autoremove' should not affect these ( famous last words) .

[INDENT][INDENT]can we see the tree for the forest
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-05
> **Bashing-om said:**
> gregg3; Yuk ..

Now that just does not compute . Should workie .

All I can think of is to boot up letting the system choose the kernel to boot ( should boot 4.2.0-35-generic) and let's look at what is set once it finally boots:
```

uname -r
cat /etc/default/grub
cat /boot/grub/grub.cfg

```

Maybe time to bite the bullet and remove all the cruft on the system; but I can not be certain there will not be unwanted side effects. The good news is that I only see 2 kernels installed .. so 'autoremove' should not affect these ( famous last words) .[INDENT][INDENT]can we see the tree for the forest
[/INDENT]
[/INDENT]


Okay, Bashing-om. I will start the computer up from scratch and then run your commands. 

I don't have a problem with booting from GRUB as the computer comes on really quickly. And it works perfectly. I would hate to mess that up. In other words, whatever cruft is present doesn't seem to be  affecting the computer's functioning. 

I am concerned about the next upgrade though. Which would be in October. I know you said 16.04 is installed, but (I think) you also said that I won't be offered the upgrade option automatically. 

As I said earlier, I just want to get back on the 6-month short-term upgrade path. And I figure upgrading, say in October, to the new short-term upgrade will make all the current cruft meaningless.

But the question is: "Will I be able to make the upgrade in October with the computer in its current state?"

Thanks.

---

### Post by Bashing-om on 2016-05-05
gregg3; K ..

As to :
> 
I am concerned about the next upgrade though. Which would be in October. I know you said 16.04 is installed, but (I think) you also said that I won't be offered the upgrade option automatically. 


We can make that happen.

> 
But the question is: "Will I be able to make the upgrade in October with the computer in its current state?"

That upgrade is questionable ; maybe yes, maybe not . However, between now and then there will be several new kernels released . A new kernel install may in fact resolve the present predicament. Good and bad in that experience. Good the issue is resolved, bad that after all this time and effort, will not know the root cause . I hate when that happens.

I have entertained the notion to reconfigure the present kernel . but my experience with systemd is lacking. I do not have the experience in systemd to know the result of the attempt.

[INDENT][INDENT]poke at it gently
[INDENT][INDENT][INDENT]something is gonna give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-05
> **Bashing-om said:**
> gregg3; K ..

As to :

We can make that happen.

Ok, that's good.

> **Bashing-om said:**
> 
That upgrade is questionable ; maybe yes, maybe not . However, between now and then there will be several new kernels released . A new kernel install may in fact resolve the present predicament. Good and bad in that experience. Good the issue is resolved, bad that after all this time and effort, will not know the root cause . I hate when that happens.

Agreed. Even so, with the potential issues being ironed out by future kernels, why not let well enough alone? (The computer works great.)

Now I don't know if I'm reading this terminal output right or not, but it seems to me the 4.4.0-21-generic kernel booted! Which would be expected, considering we set only the GRUB boot to boot the 4.2.0-35-generic. (Yeah, in hindsight, I'm wondering why we did that since booting from the GRUB boot I had to manually choose something every time.) 

So here's what happened. I started the computer and let it go an hour before checking it and it was on. And I ran your commands.

So then   the slow start (and it may only have been 15 minutes) seems to be the only issue then, right?  I could live with that. Then, maybe, since it's the latest kernel, the next upgrade might not be problematic, right? Thanks.
```

gregg@LG:~/Desktop$ uname -r
4.4.0-21-generic
gregg@LG:~/Desktop$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=4
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
gregg@LG:~/Desktop$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="4"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
else
  search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-21-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
gregg@LG:~/Desktop$ 
```

---

### Post by Bashing-om on 2016-05-05
gregg3; Ouch .

Something is fishy !
The edit is correct BUT booting 4.4.0-21-generic instead of the target (4) and we see in the boot file that " ### BEGIN /etc/grub.d/00_header ### >> else >>  set default="4" "" is also set. And verified again that our target is the 5th menu entry:
confirmed this is a correct method :
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

Ouch .. how to isolate what is now not going on ???????? As we only have the 2 kernels installed and only 1 working .. I am very hesitant to mess about doing any reconfiguration of the boot image . Install an additional older kernel ??? Now that is a thought and see what results with grub ? will have to reset our target menu number if we do that .

May take a spell for me to see a way forward from this .


EDIT:
-----------------------------------
If it be any consolation, I am aware of two others on IRC that are experiencing the same same issue of a long delay in booting. Maybe what we have here is a bug !
[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-05
> **Bashing-om said:**
> gregg3; Ouch .

  As we only have the 2 kernels installed and only 1 working 

Hey Bashing-om. I thought there were two kernels working. 4.2.0-35-generic (which I've been booting manually from the GRUB menu) and 4.4.0-21-generic (which just booted this last time when I turned the computer on with the power button). 

I was actually taking this as a positive that 4.4.0-21-generic booted up from the power button. Like the system is on track now and a upgrade might be easier now.

> **Bashing-om said:**
> 


If it be any consolation, I am aware of two others on IRC that are experiencing the same same issue of a long delay in booting. Maybe what we have here is a bug !

I think it is a bug. Especially since that clicking on a tab opening a new browser is still happening.

Thanks.

---

### Post by Bashing-om on 2016-05-05
gregg3; Welp;

No, 2 kernels - 4.2.0-35 & 4.4.0-21 - are all that are installed:
```

dpkg -l | grep linix-

```
ALL those entries starting 'rc' are (R)emoved but (C)onfig files remain (clutter ) . That leaves 2 sets (ii)  = desired state is (I)install and actual state is (I)nstalled . 4.2.0-35 is wily 15.10 :
[http://packages.ubuntu.com/search?keywords=linux-image-generic&searchon=names&suite=wily-updates&section=all](http://packages.ubuntu.com/search?keywords=linux-image-generic&searchon=names&suite=wily-updates&section=all) .

I have a thought that perhaps " submenu 'Advanced options " heading is throwing the count off where we should be counting " menuentry  " ??

What mode are you presently booting in ?
Post back :
```

uname -r
sudo stat /proc/1/exe
ps -p1 | grep systemd && echo systemd || echo upstart

``` let's see of we want to adjust the count .

[INDENT][INDENT]it might be a process of learning here
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-05
> **Bashing-om said:**
> gregg3; Welp;

No, 2 kernels - 4.2.0-35 & 4.4.0-21 - are all that are installed:
```

dpkg -l | grep linix-

```
ALL those entries starting 'rc' are (R)emoved but (C)onfig files remain (clutter ) . That leaves 2 sets (ii)  = desired state is (I)install and actual state is (I)nstalled . 4.2.0-35 is wily 15.10 :

I get that. The thing is you wrote (in post 87): > As we only have the 2 kernels installed and _only 1 working_ And I was asking: Don't I have _two_ kernels _working_? The 4.2.0-35-generic (which I've been booting manually from the GRUB menu)  and 4.4.0-21-generic (which I just booted this last time when I turned the  computer on with the power button). 

And since I have the two working, do I really need to do anything? Yes, I have the slow start up time for 4.4.0-21-generic but the 4.2.0-35-generic boots up from GRUB in less than two minutes. I can use either one. 

And regarding the clutter (all the (R) (C) stuff. Those are kernels I've been removing regularly with 
```
sudo aptitude remove
``` 

So that clutter is just there in name, right? It's not taking up a lot of space, right? (Because that's why I was removing it.)

And, again, *if* there are indeed two working kernels, I don't really need to do too much more, do I? I can boot 4.2.0-35-generic with GRUB if I want to use that or 4.4.0-21-generic with the power button. 

> **Bashing-om said:**
> 

I have a thought that perhaps " submenu 'Advanced options " heading is throwing the count off where we should be counting " menuentry  " ??

What mode are you presently booting in ?

Post back :
```

uname -r
sudo stat /proc/1/exe
ps -p1 | grep systemd && echo systemd || echo upstart

``` let's see of we want to adjust the count .[INDENT][INDENT]it might be a process of learning here
[/INDENT]
[/INDENT]
```


gregg@LG:~/Desktop$ uname -r
4.4.0-21-generic
gregg@LG:~/Desktop$ sudo stat /proc/1/exe
[sudo] password for gregg: 
  File: '/proc/1/exe' -> '/lib/systemd/systemd'
  Size: 0             Blocks: 0          IO Block: 1024   symbolic link
Device: 4h/4d    Inode: 10022       Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2016-05-05 16:30:30.236340842 -0500
Modify: 2016-05-05 16:30:27.960340760 -0500
Change: 2016-05-05 16:30:27.960340760 -0500
 Birth: -
gregg@LG:~/Desktop$ ps -p1 | grep systemd && echo systemd || echo upstart
    1 ?        00:00:01 systemd
systemd
gregg@LG:~/Desktop$ 
```

And the ```
systemd
``` was orange.

Thanks. 

P.S. Calling it a night tonight. Have a good night!

---

### Post by Bashing-om on 2016-05-05
gregg3; Hey;

Certainly nothing wrong with resting on our laurels and leaving well enough alone; you have a working system .
Lastly is to re-add Google's signing key:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551

```

As you are happy
[INDENT][INDENT]I am tickled pink
[INDENT][INDENT][INDENT]I expect we are free to go
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-06
> **Bashing-om said:**
> gregg3; Hey;

Certainly nothing wrong with resting on our laurels and leaving well enough alone; you have a working system .
Lastly is to re-add Google's signing key:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551

```

As you are happy[INDENT][INDENT]I am tickled pink[INDENT][INDENT][INDENT]I expect we are free to go
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Yes, Bashing-om, I am happy. Thank you _so much_ for all your help! I do have a few more questions, though.

1) What is the command for re-adding Google's signing key for? (Did we remove it?)

2) Do I have two working kernels?

3) If so, does it matter which I use? (My mind thinks it's best to stay with the 4.4.0-21-generic (which now boots with the power switch).)

4) Should I go back in and change that GRUB_DEFAULT back to "0"? (from "4")

5) Since the computer is starting to the 4.4.0-21-generic would switching the GRUB_DEFAULT back to "0" screw things up?

6) Will having that GRUB_DEFAULT at "4" screw up future upgrades down the road?

7) Is all that (R) (C) clutter from that one terminal output just there in name only or is that taking up space on the computer (and should I get rid of it)?

8) In terms of wanting to get back onto that 6 month short-term release train, what's the best way of doing that? (I ask because I think you mentioned I won't be offered the upgrade window from Xubuntu. And I guess I might have to do the sudo apt update and sudo apt upgrade commands on my own. And so, should I just wait till maybe September and then go with the 16.10 short term release via sudo apt update and sudo apt upgrade?)

Thanks.

---

### Post by Bashing-om on 2016-05-06
gregg3l Hey ...

Like so:
1) Google's signing key:
> 
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: There is no public key available for the following key IDs:
1397BC53640DB551

so we import this "trusted" signing key .

2) Well, honestly, you tell me . Right now appears you do . Still with a long long delay in booting 4.4.0-21 in systemd mode (??).

3) No, it does not matter, use the one that works the better. That is but one reason why the system will not remove old kernels; leaving to your discretion the in-use, use/case of kernels.

4) Yeah, I would as the target menu entry will change with the next kernel install. ( there is a way araound this if one wanted to keep the present booting kernel ) . Change back to '0' and let's see what happens.

5) Maybe yes, maybe not so yes . We do not know why at this point the system boots so slow with this kernel. try and see what results. We know the change will not break the system . No harm in trying and see.

6) Yeah, it will ... see the above. However, so long as you know what is going on .. no big deal to keep the situation under control . Just one more thing in system administration.

7) Those are no-longer-required config files . They do take up a small amount of space; with the dim possibility of a conflict in interest if the system gets confused. I prefer to err on the side of safety and keep things clean behind me . IF I were certain that the system is solid and stable .. I - on my system - would remove them .
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
In a unstable system doing a 'rc' purge can have undesired side effects.

8) When 16.10 is released, in software sources set the upgrade to "any" : system is fully updated, PPAs are disabled and proprietary driver reverted and any screen saver is disabled . Then let the update-manager do it's thing . The update-manager on a desktop machine controls the release upgrade process, you control the update-manager.
> 
sudo apt update and sudo apt upgrade commands on my own.

is something I do EVERY time I boot up any one of my operating systems. Mostly due to security updates and patches .

----------------------

Run through the list, see where we stand ->

[INDENT][INDENT][INDENT]"carry on my wayward son"
[/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-06
> **Bashing-om said:**
> gregg3l Hey ...

Like so:
1) Google's signing key:

so we import this "trusted" signing key .

2) Well, honestly, you tell me . Right now appears you do . Still with a long long delay in booting 4.4.0-21 in systemd mode (??).

3) No, it does not matter, use the one that works the better. That is but one reason why the system will not remove old kernels; leaving to your discretion the in-use, use/case of kernels.

4) Yeah, I would as the target menu entry will change with the next kernel install. ( there is a way araound this if one wanted to keep the present booting kernel ) . Change back to '0' and let's see what happens.

5) Maybe yes, maybe not so yes . We do not know why at this point the system boots so slow with this kernel. try and see what results. We know the change will not break the system . No harm in trying and see.

6) Yeah, it will ... see the above. However, so long as you know what is going on .. no big deal to keep the situation under control . Just one more thing in system administration.

7) Those are no-longer-required config files . They do take up a small amount of space; with the dim possibility of a conflict in interest if the system gets confused. I prefer to err on the side of safety and keep things clean behind me . IF I were certain that the system is solid and stable .. I - on my system - would remove them .
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
In a unstable system doing a 'rc' purge can have undesired side effects.

8) When 16.10 is released, in software sources set the upgrade to "any" : system is fully updated, PPAs are disabled and proprietary driver reverted and any screen saver is disabled . Then let the update-manager do it's thing . The update-manager on a desktop machine controls the release upgrade process, you control the update-manager.

is something I do EVERY time I boot up any one of my operating systems. Mostly due to security updates and patches .

----------------------

Run through the list, see where we stand ->[INDENT][INDENT][INDENT]"carry on my wayward son"
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om! Thanks. (Carrying on waywardly.)

Okay. Maybe it will help to stay with the numbers.

1) I ran that Google command (in the 4.4.0-21-generic kernel).

2) I have two working kernels. 

3) I'm going to go with the 4.4.0-21-generic. It just feels more normal turning the computer on with the power button. And I can handle the 20 minute startup, and if it's a bug, a software update might fix it. And I get weirded out, thinking something I might do in one kernel won't carry over to the other. And the 4.2.0-35-generic is the 15.10 and (granted, this is in my woefully uninformed mind) seems old and seems like I was supposed to update to 16.04 (and what happens in July when I have to update to 16.04--hypothetically speaking--and I'm still in 15.10)? Plus I'll have later apps on the 16.04. No, I'm going with 4.4.0-21. Phew!

4) I changed it back to "0"

5) It didn't boot. Just the "No input signal." So I changed it back to "4" and restarted. It came on in the 20 minutes.

6) me: Will having that GRUB_DEFAULT at "4" screw up future upgrades down the road? You: there is a way around this if one wanted to keep the present booting kernel me: good (LOL) And what is that way?

7) Thanks very much for the explanation. Since they're not taking up a lot of space (I was told to remove the older kernels because they took up A LOT of space--is that true or maybe I should just leave them?) and I might not have a stable system I'll leave them. 

8) Got it! Not really. LOL I don't have 'software sources.' Maybe 'Software & Updates' (see screenshot) is the same thing?
 
And a software update just came through. I looked at the 'details' during the download. It was for 4.4.0-22-generic. Should be interesting. I'll restart and come back with a report.

And thanks!

---

### Post by Bashing-om on 2016-05-06
gregg3; Hey, hey ...

Well ,,, we know there is a hitch in grub's hooks - somewhere !
Maybe the install of the new kernel will fix it for us .

As to keeping the old kernel as the booting kernel, instead of a number .. pass it the version as per instruction given in this link:
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

> 
Maybe 'Software & Updates' (see screenshot) is the same thing?

Uh huh ... see the options under the "updates" tab ..

[INDENT][INDENT]fingers are crossed !
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-06
> **Bashing-om said:**
> gregg3; Hey, hey ...

Well ,,, we know there is a hitch in grub's hooks - somewhere !
Maybe the install of the new kernel will fix it for us .

Alas, no luck. After the restart it still took the 20 minutes to come on.

> **Bashing-om said:**
> 

As to keeping the old kernel as the booting kernel, instead of a number .. pass it the version as per instruction given in this link:
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

There's three answers that got voted up. We already did the 146 votes one. Not sure what you're saying I should do.

> **Bashing-om said:**
> 
Uh huh ... see the options under the "updates" tab ..[INDENT][INDENT]fingers are crossed !
[/INDENT]
[/INDENT]


Found it. Yeah, that seems easy enough. Can't I just set the updates tab at "any" now? And that other stuff (system is fully updated, PPAs are disabled and proprietary driver reverted and any screen saver is disabled) does that pretty much happen automatically or do I have to run that stuff down and do it myself?

I ran a command to see what was going on. (posted below). It shows the 4.4.0-22-generic is installed, but how can we tell if it's the active kernel?

```
gregg@LG:~/Desktop$ dpkg -l | grep linux-
ii  linux-base                                                  4.0ubuntu1                                          all          Linux image base package
ii  linux-firmware                                              1.157                                               all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.22.23                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-35                                      4.2.0-35.40                                         all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic                              4.2.0-35.40                                         amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                                      4.4.0-21.37                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                              4.4.0-21.37                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-22                                      4.4.0-22.39                                         all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-22-generic                              4.4.0-22.39                                         amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.22.23                                         amd64        Generic Linux kernel headers
rc  linux-image-3.16.0-23-generic                               3.16.0-23.31                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-33-generic                               3.16.0-33.44                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-34-generic                               3.16.0-34.47                                        amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-15-generic                               3.19.0-15.15                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-16-generic                               3.19.0-16.16                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-18-generic                               3.19.0-18.18                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-20-generic                               3.19.0-20.20                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-21-generic                               3.19.0-21.21                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-22-generic                               3.19.0-22.22                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-23-generic                               3.19.0-23.24                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic                               3.19.0-25.26                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-26-generic                               3.19.0-26.28                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-28-generic                               3.19.0-28.30                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-30-generic                               3.19.0-30.34                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-31-generic                               3.19.0-31.36                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-32-generic                               3.19.0-32.37                                        amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-17-generic                                4.2.0-17.21                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-18-generic                                4.2.0-18.22                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-19-generic                                4.2.0-19.23                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-22-generic                                4.2.0-22.27                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-23-generic                                4.2.0-23.28                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-25-generic                                4.2.0-25.30                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-27-generic                                4.2.0-27.32                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-30-generic                                4.2.0-30.36                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-34-generic                                4.2.0-34.39                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-35-generic                                4.2.0-35.40                                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                                4.4.0-21.37                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-22-generic                                4.4.0-22.39                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                         3.16.0-23.31                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-33-generic                         3.16.0-33.44                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-34-generic                         3.16.0-34.47                                        amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-15-generic                         3.19.0-15.15                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-16-generic                         3.19.0-16.16                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-18-generic                         3.19.0-18.18                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-20-generic                         3.19.0-20.20                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-21-generic                         3.19.0-21.21                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-22-generic                         3.19.0-22.22                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-23-generic                         3.19.0-23.24                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                         3.19.0-25.26                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-30-generic                         3.19.0-30.34                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-31-generic                         3.19.0-31.36                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-32-generic                         3.19.0-32.37                                        amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-17-generic                          4.2.0-17.21                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-18-generic                          4.2.0-18.22                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-19-generic                          4.2.0-19.23                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-22-generic                          4.2.0-22.27                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-23-generic                          4.2.0-23.28                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-25-generic                          4.2.0-25.30                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-27-generic                          4.2.0-27.32                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-30-generic                          4.2.0-30.36                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic                          4.2.0-34.39                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-35-generic                          4.2.0-35.40                                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                          4.4.0-21.37                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-22-generic                          4.4.0-22.39                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                         4.4.0.22.23                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        4.4.0-22.39                                         amd64        Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                               all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
gregg@LG:~/Desktop$ 
```

Calling it a day here. Should be able (it's the work computer) to get back here tomorrow. Have a good night! And thanks!

---

### Post by Bashing-om on 2016-05-06
gregg3; Well, we could hope !

Here:
> 
You can also chose the default by the name instead of index, e.g.:

GRUB_DEFAULT='Ubuntu'
if there was a menuentry 'Ubuntu' line on /boot/grub/grub.cfg. This may be a better method, as it does not depend on the order of the entries, which could change.


As to the release upgrade: 
You can set the update-manager to "any" at any time . The prep work for the release upgrade is best done by you . 3rd party (PPA) is not ubuntu . And the system may or may not be able to cope well . That does include a proprietary driver .. not ubuntu ... some cleaver programming to make it work in a particular environment. When the environment changes the software breaks .
---------------

Let's look at what grub has set for booting currently:
```

ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot

```

Now there is another thought ... we see what we shall see.

[INDENT][INDENT]we have the will
[INDENT][INDENT][INDENT]look'n to find that way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-07
> **Bashing-om said:**
> gregg3; Well, we could hope ! 

Thanks Bashing-om. (Yes, hope is a good thing!) Okay, I'm still *hoping* to make that next upgrade work. So following this:

```
You can also chose the default by the name instead of index, e.g.:

  GRUB_DEFAULT='Ubuntu'
  if there was a menuentry 'Ubuntu' line on /boot/grub/grub.cfg. This may be a better method, as it does not depend on the order of the entries, which could change.


```

I went to my /boot/grub/grub.cfg file and found this:
```

export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-22-generic
```


So I have the ```
menuentry 'Ubuntu'
``` line. 

So all I have to do is use nano to go into the /etc/default/grub file and change ```
GRUB_DEFAULT=4

``` to ```
GRUB_DEFAULT='Ubuntu'
``` , right? And it's ```
GRUB_DEFAULT='Ubuntu'
``` , not ```
GRUB_DEFAULT=Ubuntu
``` , right?

And I'm wondering, Can I do that now already? Or should I do it right before the distro upgrade in October?


> **Bashing-om said:**
> 
As to the release upgrade: 
You can set the update-manager to "any" at any time . 

I just did.

> **Bashing-om said:**
> 

The prep work for the release upgrade is best done by you . 3rd party (PPA) is not ubuntu . And the system may or may not be able to cope well . That does include a proprietary driver .. not ubuntu ... some cleaver programming to make it work in a particular environment. When the environment changes the software breaks . 

This does not sound ecouraging, especially as how I don't know how to do the prep work. I think I'll just have to throw myself at the mercy of the Sky Penguin and hope the distro upgrade works somehow. (This seems to be such a mess--maybe it is a bug and they'll straighten it all out before I upgrade.)


> **Bashing-om said:**
> 
---------------

Let's look at what grub has set for booting currently:
```

ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot

```

Now there is another thought ... we see what we shall see.[INDENT][INDENT]we have the will[INDENT][INDENT][INDENT]look'n to find that way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
```


gregg@LG:~/Desktop$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 29 May  6 16:46 /vmlinuz -> boot/vmlinuz-4.4.0-22-generic
lrwxrwxrwx 1 root root 29 Apr 23 14:26 /vmlinuz.old -> boot/vmlinuz-4.4.0-21-generic
gregg@LG:~/Desktop$ ls -al /initrd.img*
lrwxrwxrwx 1 root root 32 May  6 16:46 /initrd.img -> boot/initrd.img-4.4.0-22-generic
lrwxrwxrwx 1 root root 32 Apr 23 14:26 /initrd.img.old -> boot/initrd.img-4.4.0-21-generic
gregg@LG:~/Desktop$ ls -al /boot
total 142200
drwxr-xr-x  3 root root     4096 May  6 16:47 .
drwxr-xr-x 24 root root     4096 May  6 16:46 ..
-rw-r--r--  1 root root  1313029 Mar 15 19:45 abi-4.2.0-35-generic
-rw-r--r--  1 root root  1239577 Apr 18 17:21 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1239612 May  5 14:03 abi-4.4.0-22-generic
-rw-r--r--  1 root root   184888 Mar 15 19:45 config-4.2.0-35-generic
-rw-r--r--  1 root root   189412 Apr 18 17:21 config-4.4.0-21-generic
-rw-r--r--  1 root root   189520 May  5 14:03 config-4.4.0-22-generic
drwxr-xr-x  5 root root     4096 May  6 16:47 grub
-rw-r--r--  1 root root 34346822 Apr 23 13:36 initrd.img-4.2.0-35-generic
-rw-r--r--  1 root root 36987572 Apr 23 14:32 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 36995319 May  6 16:47 initrd.img-4.4.0-22-generic
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3745312 Mar 15 19:45 System.map-4.2.0-35-generic
-rw-------  1 root root  3853719 Apr 18 17:21 System.map-4.4.0-21-generic
-rw-------  1 root root  3855781 May  5 14:03 System.map-4.4.0-22-generic
-rw-------  1 root root  6829104 Mar 15 19:45 vmlinuz-4.2.0-35-generic
-rw-------  1 root root  7013968 Apr 18 17:21 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7015344 May  5 14:03 vmlinuz-4.4.0-22-generic
gregg@LG:~/Desktop$ 
```

[/QUOTE]

So it looks like 4.4.0-22-generic is the one that's booting from the power switch, right?

Thanks.

---

### Post by Bashing-om on 2016-05-07
gregg3; Welp;

Grub2 edit:
see: [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

something like:
> 
GRUB_DEFAULT="xxxx" An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. 

Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"


> 
This does not sound encouraging, especially as how I don't know how to do the prep work.

nothing to it: disable PPAs in Software Sources and in Additional Drivers make sure the open source graphics's driver is enabled. Easy as that.


Booting kernel:
```

uname -r

``` tells that tale. I do not see a thing wrong with how the system installed the kernels .

So we are back to reading the logs if we are to continue to pursue the booting issue. And, I do not know where that will lead.

But ->
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-07
> **Bashing-om said:**
> gregg3; Welp;

Grub2 edit:
see: [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

something like:



nothing to it: disable PPAs in Software Sources and in Additional Drivers make sure the open source graphics's driver is enabled. Easy as that.


Booting kernel:
```

uname -r

``` tells that tale. I do not see a thing wrong with how the system installed the kernels .

So we are back to reading the logs if we are to continue to pursue the booting issue. And, I do not know where that will lead.

But ->[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


Thanks Bashing-om. So if I wanted to do the changeover of the GRUB *today* from this data in boot/grub/grub.cfg:
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="4"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
else
  search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```


In the /etc/default/grub file (via Nano) I would change:

```
GRUB_DEFAULT=4
``` to what? 

To

```
GRUB_DEFAULT='Ubuntu, with Linux 4.4.0-22-generic'
``` ? 

Something else?


Okay, you wrote:

[U]disable PPAs in Software Sources and in Additional Drivers make sure the open source graphics's driver is enabled. Easy as that.

[/U]Please check the three (hopefully pertinent) screenshots and tell me how to accomplish the above two actions.

And lastly:

[U]Booting kernel:
```

uname -r

``` tells that tale. I do not see a thing wrong with how the system installed the kernels .

[/U]```
gregg@LG:~/Desktop$ uname -r
4.4.0-22-generic
gregg@LG:~/Desktop$ 
```

And so since the computer picked up on the shift from 4.4.0-21-generic to 4.4.0-22-generic (and it boots from the power button) just leave 
```
GRUB_DEFAULT=4
```

as is, right?


Bashing-om, If I can feel confident I can go through the 16.10 distro upgrade satisfactorily I'll be very happy. The  computer is working great. This last time it came on after 17 minutes. I know that's ridiculously slow, but maybe it's a bug and the coder guys will fix  it on their end.

P.S. That'll do it for me tonight. Have a great night! And thanks!

---

### Post by Bashing-om on 2016-05-07
gregg3; Uh huh ...

If you count the menu entries .. 1st entry as '0' .. then you see that '4' is now "  Ubuntu, with Linux 4.4.0-21-generic' ".
What kernel do you want as the default booting kernel ? If it is " Linux 4.4.0-22-generic'  then reset in /etc/default/grub back to '0' .
Else, sure, lets try " Ubuntu, with Linux 4.2.0-35-generic " .
I am a bit confused; I do expect the the kernel booted from the power button to be what you have set in /etc/default/grub (4) to be that booting kernel !


Software and Updates -> other software tab: are your PPAs. As you have it set now .. will not get updates for any of the PPAs except google-chrome. Need to check and see if these PPA's are supported in 16.04 and perhaps re-enable them .
Software and updates -> Additional drivers tab : You have no  -proprietary- drivers in use or available .

As is now .. if you were to do a release upgrade now .. I would expect no problems.

---

### Post by Bashing-om on 2016-05-08
gregg3;  Hey !

Here is another thought to see what is going on with the delay on booting.
Watch the boot messages as you are booting .
To unhide the boot messages:
In the /etc/default/grub file the line: " GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" remove the terms quiet splash, such that it becomes: GRUB_CMDLINE_LINUX_DEFAULT=" "

remember to run 
```

sudo update-grub

```
after you have saved the file .. to propagate the change.

[INDENT][INDENT]we can do that too
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-09
> **Bashing-om said:**
> gregg3; Uh huh ...

If you count the menu entries .. 1st entry as '0' .. then you see that '4' is now "  Ubuntu, with Linux 4.4.0-21-generic' ".

Hi Bashing-om. Yes, I counted the entries (and is it the case that the #0 and #1 entry are the same {in this case: 4.4.0-22-generic}?) and I can see that #4 is 4.4.0-21-generic, but the fact of that matter is the computer boots to 4.4.0-22-generic. Here's the terminal data:
```

gregg@LG:~/Desktop$ uname -r
4.4.0-22-generic
gregg@LG:~/Desktop$ sudo nano /etc/default/grub
[sudo] password for gregg: 
gregg@LG:~/Desktop$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=4
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
gregg@LG:~/Desktop$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="4"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
else
  search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-22-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-22-generic ...'
        linux    /boot/vmlinuz-4.4.0-22-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-21-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.4.0-21-generic ...'
        linux    /boot/vmlinuz-4.4.0-21-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        else
          search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
        fi
        echo    'Loading Linux 4.2.0-35-generic ...'
        linux    /boot/vmlinuz-4.2.0-35-generic root=UUID=da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.2.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    else
      search --no-floppy --fs-uuid --set=root da6f1e1f-a2ff-4eed-8168-44dd46a8c2a8
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
gregg@LG:~/Desktop$ 
```

So that makes no sense. 

> **Bashing-om said:**
> 

What kernel do you want as the default booting kernel ? If it is " Linux 4.4.0-22-generic'  then reset in /etc/default/grub back to '0' .

Yes, I want 4.4.0-22-generic. I can try the reset to '0'  but I already tried that (granted, with a different kernel) in post #92 point #5 and the results are in post #94 point #5. (When I reset to '0' it just led to the "No input signal" black screen.) So the computer just seems to be booting the #4  spot as the #0  spot.

> **Bashing-om said:**
> 

Else, sure, lets try " Ubuntu, with Linux 4.2.0-35-generic " .

Not sure why you say this. You're saying: GRUB_DEFAULT= "Ubuntu, with Linux 4.2.0-35-generic" , right?  Why would I do that when I want to boot 4.4.0-22-generic?

> **Bashing-om said:**
> 
I am a bit confused; I do expect the the kernel booted from the power button to be what you have set in /etc/default/grub (4) to be that booting kernel !



As you can see (from the terminal data) that's not the case.

> **Bashing-om said:**
> 
Software and Updates -> other software tab: are your PPAs. As you have it set now .. will not get updates for any of the PPAs except google-chrome. Need to check and see if these PPA's are supported in 16.04 and perhaps re-enable them .

Okay, I looked those PPA's over. They were hard to understand. As you said only Chrome was enabled. The others appear to have been  disabled on different distro upgrades. I do use things of course from Canonical, but in that grouping I also mkusb, steam, bit (Back In Time) and Mega. I do not know (nor could I find out via Googling) how to see if the PPA's are supported in 16.04. My best guess would be just to check the ones I'm using. Would that be prudent?

And what about things like Firefox? Does that get updated in a different way? (This whole "other software" updates is news to me.)

> **Bashing-om said:**
> 
Software and updates -> Additional drivers tab : You have no  -proprietary- drivers in use or available .


Okay, so that's good.

> **Bashing-om said:**
> 

As is now .. if you were to do a release upgrade now .. I would expect no problems.

Good also.

Thanks.

---

### Post by gregg3 on 2016-05-09
> **Bashing-om said:**
> gregg3;  Hey !

Here is another thought to see what is going on with the delay on booting.
Watch the boot messages as you are booting .
To unhide the boot messages:
In the /etc/default/grub file the line: " GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" remove the terms quiet splash, such that it becomes: GRUB_CMDLINE_LINUX_DEFAULT=" "

remember to run 
```

sudo update-grub

```
after you have saved the file .. to propagate the change.[INDENT][INDENT]we can do that too
[/INDENT]
[/INDENT]


Thanks Bashing-om. But before I do that (since I have to use the computer now), I figured I'd mention something else about the booting process. When I boot, I DON'T get the Xubuntu screen at all. It's just the black screen with the RAM info type stuff and then 'Loading Operating System' and then the screen goes black and I get the "No input signal" window. Then the monitor shuts off. And then (say after 17 minutes or so) the computer does not come on *unless* I scroll the mouse.

I don't know what that might mean and I got used to the computer booting that way so didn't think of mentioning it until now.

Thanks.

---

### Post by Bashing-om on 2016-05-09
gregg3P Yuk.

Lemme reboot at a later time and look at a systemd config file . Comparing yours to my 14.04 I see a lot of unexpected differences that I do not understand.

When you can get back to a desk top .. what desktop environment does the system think you have ?
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
cat /etc/X11/default-display-manager

```
And we are going to consider purging grub and reinstalling .. An indepth re-do will take a liveDVD of 16.04  in a full CHange Root .

Verifying PPAs will keep 'till the system is stable.

There is a reason
[INDENT][INDENT]why we are not having fun now
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-05-10
gregg3; Well ....

I see nothing differing between your grub.cfg file and my standard 15.10:
```

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
	else
	  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
	fi
	linux	/boot/vmlinuz-4.2.0-35-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.2.0-35-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
	menuentry 'Ubuntu, with Linux 4.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-advanced-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
		else
		  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
		fi
		echo	'Loading Linux 4.2.0-35-generic ...'
		linux	/boot/vmlinuz-4.2.0-35-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.2.0-35-generic
	}
	menuentry 'Ubuntu, with Linux 4.2.0-35-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-init-upstart-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
		else
		  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
		fi
		echo	'Loading Linux 4.2.0-35-generic ...'
		linux	/boot/vmlinuz-4.2.0-35-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.2.0-35-generic
	}
	menuentry 'Ubuntu, with Linux 4.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-35-generic-recovery-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
		else
		  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
		fi
		echo	'Loading Linux 4.2.0-35-generic ...'
		linux	/boot/vmlinuz-4.2.0-35-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.2.0-35-generic
	}
	menuentry 'Ubuntu, with Linux 4.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-30-generic-advanced-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
		else
		  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
		fi
		echo	'Loading Linux 4.2.0-30-generic ...'
		linux	/boot/vmlinuz-4.2.0-30-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.2.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 4.2.0-30-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-30-generic-init-upstart-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
		else
		  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
		fi
		echo	'Loading Linux 4.2.0-30-generic ...'
		linux	/boot/vmlinuz-4.2.0-30-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro  quiet splash $vt_handoff init=/sbin/upstart
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.2.0-30-generic
	}
	menuentry 'Ubuntu, with Linux 4.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.2.0-30-generic-recovery-2ec4733f-db40-4db0-aef8-5c54e54085ab' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  2ec4733f-db40-4db0-aef8-5c54e54085ab
		else
		  search --no-floppy --fs-uuid --set=root 2ec4733f-db40-4db0-aef8-5c54e54085ab
		fi
		echo	'Loading Linux 4.2.0-30-generic ...'
		linux	/boot/vmlinuz-4.2.0-30-generic root=UUID=2ec4733f-db40-4db0-aef8-5c54e54085ab ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.2.0-30-generic
	}
}

### END /etc/grub.d/10_linux ###

```


I presently do not know why our grub edits fail to complete to achieve the desired booting kernel .
Nor do we know to this time if it is grub or the kernel routines taking so long, nor what they are looking for and not finding.

At this point to find out the why .. all I know to do is read the logs looking for large gaps in the time lines or errors .

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read the instructions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-10
> **Bashing-om said:**
> gregg3P Yuk.

Lemme reboot at a later time and look at a systemd config file . Comparing yours to my 14.04 I see a lot of unexpected differences that I do not understand.

When you can get back to a desk top .. what desktop environment does the system think you have ?
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
cat /etc/X11/default-display-manager

```

Thanks Bashing-om. 

```
gregg@LG:~/Desktop$ echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
xubuntu   XFCE
gregg@LG:~/Desktop$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm
gregg@LG:~/Desktop$ 
```

> **Bashing-om said:**
> 
And we are going to consider purging grub and reinstalling .. An indepth re-do will take a liveDVD of 16.04  in a full CHange Root .


I just ordered some DVDs from Newegg. Should have them tomorrow, so if you want to we can. 

This thing is weird. Today I watched the sequence more closely. There is no Dell screen at all. It just goes straight to the info. with Master/Slave/DDR3 type stuff. Then that stuff disappears and it says: "Loading Operating System." Then that disappears and "Boot from CD" appears. Then that disappears and the "No input signal" window appears.

And today I experimented. (And I had a feeling this might be the case.) I turned the computer on and scrolled the mouse at the five minute marks just to see if it came on any earlier than the 17:30 it took yesterday. (Remember, it only comes on when I scroll the mouse.) I was thinking that scrolling the mouse *too early *keeps the computer from turning on. I don't know how long it keeps it from turning on but this time I went to 22:26 and nothing. So I stopped the periodic scrolling and let the computer sit for 18 minutes, then I scrolled. It came on.

And is purging the grub and reinstalling it pretty straightforward and unrisky? 

Because as funky as this is, the computer works good. (I mean, what if it's some bizarre bug. Like you said a lot of people seem to be having issues with the upgrade to 16.04.) I'm just more concerned about the upgrade to 16.10. I mean, I'd like it work more normally LOL, but I can live with the quirks as it is. But yeah, the thought of the upgrade makes me nervous.

Thanks.

---

### Post by Bashing-om on 2016-05-10
gregg3; Welp;

I think at this point, if it were me :
a) I would remove "quiet splash" in the /etc/default/grub file , Reboot and watch the boot messages
b) Try and boot to terminal (TTY1), then start the GUI from terminal ..
c) Have a read in the logs:
once to a GUI activate a terminal and run:
```

systemd-analyze blame 

```
Informative turorial on systemd's booting:
[http://www.dedoimedo.com/computers/systemd-blame.html](http://www.dedoimedo.com/computers/systemd-blame.html)
The author stipulates "  So if you suspect there might be a problem somewhere, grab the SVG files and start charting. Have fun." .

[INDENT][INDENT]are we having fun now ?
[/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-10
> **Bashing-om said:**
> gregg3; Welp;

I think at this point, if it were me :
a) I would remove "quiet splash" in the /etc/default/grub file , Reboot and watch the boot messages
b) Try and boot to terminal (TTY1), then start the GUI from terminal ..
c) Have a read in the logs:
once to a GUI activate a terminal and run:
```

systemd-analyze blame 

```
Informative turorial on systemd's booting:
[http://www.dedoimedo.com/computers/systemd-blame.html](http://www.dedoimedo.com/computers/systemd-blame.html)
The author stipulates "  So if you suspect there might be a problem somewhere, grab the SVG files and start charting. Have fun." .[INDENT][INDENT]are we having fun now ?
[/INDENT]
[/INDENT]



Bashing-om! LOL You are relentless. (You'd make a great private eye!) 

I read some of the dedoimedo link, including this:

[I]The difficult part is now trying to understand what is taking so long and how you can resolve the issue, _if_ at         all.

[/I]The computer is working good. Besides the slow boot, the only other issue is occasionally a new browser being opened when I click on a tab. Both things I can live with. I really think I'm going to bail, and then just see what happens come 16.10. If the upgrade doesn't work out I'll do a fresh install. 

Yes, we're having fun. Thanks for all the help all along. It's mega-appreciated, my friend!

---

### Post by Bashing-om on 2016-05-10
gregg3; Ho kay;

We leave well enough alone .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

This dog buries the bone of booting.
I ya dig it back up later 
[INDENT][INDENT][INDENT]open  a new thread .

ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by gregg3 on 2016-05-10
> **Bashing-om said:**
> gregg3; Ho kay;

We leave well enough alone .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

This dog buries the bone of booting.
I ya dig it back up later [INDENT][INDENT][INDENT]open  a new thread .

ain't nothing but a thing
[/INDENT]
[/INDENT]
[/INDENT]


Absolutely. Thanks again!

---

### Post by Bashing-om on 2016-05-10
gregg3; :)

Look forward to our next adventure.

Take care.

Regards:
Bashing-om

---

