---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by mart-ratas on 2015-08-12
Hello!

I'm new to these forums as well as Ubuntu (and any Unix based system to be honest).

I'm using Ubuntu 14.04 LTS 64bit.

I've been having the above error.
I found a [thread]("http://ubuntuforums.org/showthread.php?t=1642173") with the exact same error, however it didn't seem to help me. I'll try to post all the information that I gathered might be relevant.

A few background remarks:
I also have Windows 7 installed on the same system. It has had quite a few BSOD episodes in the past.
I've had trouble upgrading to a newer kernel (3.13.0-61) and am thus stuck on 3.13.0-32.
I've had previous troubles with nvidia default drivers which made my ubuntu installation crash every now and then. I installed the other drivers from Additional Drivers
I've also had this exact same error before when trying to install ROS, but all the things seemed to work afterwards regardless.

Firstly, I'm trying to install python-scipy.
```
mart@mart-IC43T-A:/boot$ sudo apt-get install python-scipy[sudo] password for mart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.13.0-61-generic but it is not going to be installed
                       Depends: linux-image-extra-3.13.0-61-generic but it is not going to be installed
 python-scipy : Depends: python-decorator but it is not going to be installed
                Depends: libumfpack5.6.2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Then I try to do as it suggests:
```
mart@mart-IC43T-A:/boot$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic linux-image-3.13.0-61-generic
  linux-image-extra-3.13.0-61-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.13.0-61-generic linux-image-extra-3.13.0-61-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.13.0-61-generic linux-image-extra-3.13.0-61-generic
0 upgraded, 2 newly installed, 0 to remove and 18 not upgraded.
1 not fully installed or removed.
Need to get 0 B/51,9 MB of archives.
After this operation, 194 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 256152 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-61-generic_3.13.0-61.100_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-61-generic (3.13.0-61.100) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-61-generic_3.13.0-61.100_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/3.13.0-61-generic/kernel/fs/xfs/xfs.ko' to '/lib/modules/3.13.0-61-generic/kernel/fs/xfs/xfs.ko.dpkg-new': unexpected end of file or stream
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
Preparing to unpack .../linux-image-extra-3.13.0-61-generic_3.13.0-61.100_amd64.deb ...
Unpacking linux-image-extra-3.13.0-61-generic (3.13.0-61.100) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/linux-image-extra-3.13.0-61-generic_3.13.0-61.100_amd64.deb (--unpack):
 cannot copy extracted data for './lib/modules/3.13.0-61-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko' to '/lib/modules/3.13.0-61-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko.dpkg-new': unexpected end of file or stream
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
And there's the error mentioned in the title.

```
sudo dpkg --configure -a
```
```
mart@mart-IC43T-A:/boot$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-61-generic; however:
  Package linux-image-3.13.0-61-generic is not installed.
 linux-image-generic depends on linux-image-extra-3.13.0-61-generic; however:
  Package linux-image-extra-3.13.0-61-generic is not installed.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic

```

```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]```
mart@mart-IC43T-A:/boot$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ee.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ee.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ee.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty universe
deb http://ee.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ee.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://ee.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ee.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://ee.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

I figured the problem might not be the one here at first as well, I thought it might have something to do with the fact that my kernel upgrade didn't work, so I also looked at these 2 pages:
[http://askubuntu.com/questions/659431/installation-failed-with-linux-image-3-13-0-61-generic-3-13-0-61-100-amd64-deb](http://askubuntu.com/questions/659431/installation-failed-with-linux-image-3-13-0-61-generic-3-13-0-61-100-amd64-deb)
leading me to
[http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full](http://askubuntu.com/questions/263363/how-can-i-remove-old-kernels-install-new-ones-when-boot-is-full)

However, I did go to my /boot and delete all the newer kernels (the ones that don't work) and rebooted without a change.

```
[COLOR=#111111][FONT=Consolas]df -h[/FONT][/COLOR]
```
```
mart@mart-IC43T-A:/boot$ df -hFilesystem      Size  Used Avail Use% Mounted on
/dev/sda5       176G  7,8G  160G   5% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            3,9G  4,0K  3,9G   1% /dev
tmpfs           799M  1,4M  798M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            3,9G  101M  3,9G   3% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sdf         96M   72M   25M  75% /media/mart/boot

```

Would be grateful for any help that someone can give me and.
Huge thanks in advance!

EDIT:
Removing kernel with
```
sudo apt-get remove linux-image-generic
```
then doing what I needed and then reinstalling the same thing
```
sudo apt-get install linux-image-generic
```
seemed to work for me.
The final install produced an error (which I forgot to log), but a reboot worked.

I realize this is NOT how it should be done, though.


Best regards,
Mart

---

### Post by dino99 on 2015-08-12
you are executing command(s) from /boot system folder: that is not expected at all; that /boot is not used by the user, but only by the system and drived by its own rules.
a user only works from its home folder (or better its /home partition)

then when a user want to install extra app/lib/... it is only from the ubuntu archive to avoid version conflicts/mismatch. 
There is friendly user app named 'synaptic' for dealing with packages (less confusing than software-center which propose lot of untrusted sources)

As you first need to get clean/updated system, from a terminal, run:
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a 

an example of python-scipy installation
[http://askubuntu.com/questions/359254/how-to-install-numpy-and-scipy-for-python](http://askubuntu.com/questions/359254/how-to-install-numpy-and-scipy-for-python)

---

### Post by mart-ratas on 2015-08-17
Thanks for the reply!

The problem has been fixed.

---

