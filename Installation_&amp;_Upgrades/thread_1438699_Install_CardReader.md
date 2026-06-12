---
title: "Install CardReader?"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by lyim on 2010-03-25
I've installed ubuntu 9.1 to eeepc 4G with an internal cardreader
Can see cardreader inside Computer-File Browser as USB2.0 CardReader SD0.
But cannot open SD memory card inside cardreader.
[http://www.cs.sfu.ca/~ggbaker/personal/cf-linux](http://www.cs.sfu.ca/~ggbaker/personal/cf-linux) explained how to.
It is too hard for me, a beginner, to install sg3-utils. Please help.
Because it cannot be done from Ubuntu Software Centre.
I've already downloaded from 
[http://packages.ubuntu.com/source/dapper-backports/sg3-utils](http://packages.ubuntu.com/source/dapper-backports/sg3-utils)
sg3-utils_1.21-1ubuntu1~dapper1.dsc
sg3-utils_1.21.orig.tar.gz
sg3-utils_1.21-1ubuntu1~dapper1.diff.gz

---

### Post by dstew on 2010-03-25
It might already be installed. Open a terminal (Applications --> Accessories --> Terminal) and enter on the command line```
sg_scan -i
```If you get no response, try```
sudo sg_scan -i
``` If it tells you that the command is not available, you should be able to install it using Synaptic. Or, from the command line,```
sudo apt-get install sg3-utils
```

---

### Post by lyim on 2010-03-25
Thanks for replying.
All tried. sg3-utils not found!
Download sg3-utils.rpm from debian, cannot install with rpm.
It will be good if Ubuntu Software Centre has this package???

---

### Post by lyim on 2010-03-25
Pity! I've tried ubuntu, eeepcbuntu, pclinuxos etc... more than 10 distributions.  None can handle CardReader.

---

### Post by dstew on 2010-03-26
The Software Center is a new program, it may have some problems. Try the command line```
sudo apt-get install sg3-utils
```If it does not work, post the command output to the forum.

---

### Post by lyim on 2010-03-26
Outputs. Thanks
user01@user01-laptop:~$ sg_scan -i
The program 'sg_scan' is currently not installed.  You can install it by typing:
sudo apt-get install sg3-utils
sg_scan: command not found
user01@user01-laptop:~$ 
user01@user01-laptop:~$ sudo sg_scan -i
sudo: sg_scan: command not found
user01@user01-laptop:~$ 
user01@user01-laptop:~$ sudo apt-get install sg3-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sg3-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sg3-utils has no installation candidate
user01@user01-laptop:~$

---

### Post by dstew on 2010-03-26
This probably means your repository list is not correct. Post to the forum the output of the command```
cat /etc/apt/sources.list
```

---

### Post by lyim on 2010-03-26
user01@user01-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
user01@user01-laptop:~$

---

### Post by lyim on 2010-03-26
user01@user01-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

This is a new installation of Ubuntu 9.10 to eeepc 4g from USB stick
CardReader was visible but content of SD memory could not be open
I´ve used Update Manager.(it has taken 10 hours)
After updating, CardReader is now invisible.
(but visible from Palimpsest Disk Utility; cannot see content)
[CardReader always works with WinXP, SD or HD SD
because I repeatly installing XP or Linux for testing
ie CardReader hardware is ok]

---

### Post by dstew on 2010-03-27
Try this:```
sudo apt-get install libsgutils2-2
```I found this package in your archives that is supposed to contain sg3-utils. But, I also found sg3-utils in the archive, so I guess I don't know why it won't install on your system. Can you install other packages?

---

### Post by lyim on 2010-03-28
Thank you dstew, appreciate very much your patience and assistance.  It works now. I will follow [http://www.cs.sfu.ca/~ggbaker/personal/cf-linux]("http://www.cs.sfu.ca/%7Eggbaker/personal/cf-linux") and see how things go. I´ll let you know.

The followings are outputs of your instructions, for your info. Thanks again.
user01@user01-laptop:~$ sudo -i
[sudo] password for user01: 
root@user01-laptop:~# sudo apt-get install libsgutils2-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsgutils2-2 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@user01-laptop:~# sg_scan -i
The program 'sg_scan' is currently not installed.  You can install it by typing:
apt-get install sg3-utils
sg_scan: command not found
root@user01-laptop:~# apt-get install sg3-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  sg3-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 527kB of archives.
After this operation, 1,638kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main sg3-utils 1.27-0.1 [527kB]
Fetched 527kB in 45s (11.7kB/s)                                                
Selecting previously deselected package sg3-utils.
(Reading database ... 135155 files and directories currently installed.)
Unpacking sg3-utils (from .../sg3-utils_1.27-0.1_i386.deb) ...
Processing triggers for man-db ...
Setting up sg3-utils (1.27-0.1) ...
root@user01-laptop:~# sg_scan -i
/dev/sg0: scsi1 channel=0 id=0 lun=0 [em]
    ATA       SILICONMOTION SM  n/a  [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg1: scsi2 channel=0 id=0 lun=0 [em]
    USB2.0    CardReader SD0    0100 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
root@user01-laptop:~#

---

### Post by lyim on 2010-03-28
root@user01-laptop:~# sg_scan -i
/dev/sg0: scsi1 channel=0 id=0 lun=0 [em]
    ATA       SILICONMOTION SM  n/a  [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg1: scsi2 channel=0 id=0 lun=0 [em]
    USB2.0    CardReader SD0    0100 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
root@user01-laptop:~# sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/sdb
root@user01-laptop:~#

It is too hard for me, a beginner, to make the card reader working; shall give up!

---

