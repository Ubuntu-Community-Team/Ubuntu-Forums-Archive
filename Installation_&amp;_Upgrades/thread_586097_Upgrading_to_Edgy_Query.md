---
title: "Upgrading to Edgy Query"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by coolboarderguy on 2007-10-22
Hi All,

I have Dapper and here at work we're responsible for our own desktop updates. I've been slack the past year or so. We usually use a mirror here, and point our sources.list to there. Problem now, though, is, it doesn't mirror Edgy anymore, so I changed all instances back to au.archive as below.

#

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


I get the following when doing the update,

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


There seems to be no upgrade option here. Am I missing something?

---

### Post by overdrank on 2007-10-23
Hi and maybe this link will help
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
Good luck!

---

### Post by coolboarderguy on 2007-10-24
Hi All,

thanx for that overdrank. I actually stumbled upon it myself a little later after posting. I now am curious, the system is prompting me to run apt-cdrom and then that prompts me that it failed. My cdrom is mounting at /media/cdrom-1. I don't really know why, it is a USB one. How can I make apt-cdrom see that mount point?

****
EDIT
****
Ok, I was able to manually mount the cdrom device as /media/cdrom, which apt-cdrom liked, but now am getting the following,

 apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [a24fcd3fce58b618a3d2f257b8543b19-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)'
Copying package lists...gpgv: Signature made Wed 25 Oct 2006 23:56:08 EST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
E: Could not open file /var/lib/apt/lists/Ubuntu%206.10%20%5fEdgy%20Eft%5f%20-%20Release%20i386%20(20061025.1)_dists_edgy_Release - open (13 Permission denied)
E: Could not open file /var/lib/apt/lists/Ubuntu%206.10%20%5fEdgy%20Eft%5f%20-%20Release%20i386%20(20061025.1)_dists_edgy_Release.gpg - open (13 Permission denied)

---

### Post by coolboarderguy on 2007-10-24
Hi All,

am I doing something fundamentally wrong here?

sudo mount -t iso9660 /dev/scd0 /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
:~$ ls /media/cdrom
cdromupgrade  dists  doc  install  isolinux  md5sum.txt  pics  pool  preseed  README.diskdefines  ubuntu
:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
E: Failed to mount the cdrom.
:~$ ls /media/cdrom
:~$

---

### Post by coolboarderguy on 2007-10-28
Hi All,

I finally figured this out. I had to change the path in /etc/fstab to reflect the mountpoint of the USB drive. Apparently apt-cdrom reads from either there or apt.conf, for the CD path. It is now finally working.

---

