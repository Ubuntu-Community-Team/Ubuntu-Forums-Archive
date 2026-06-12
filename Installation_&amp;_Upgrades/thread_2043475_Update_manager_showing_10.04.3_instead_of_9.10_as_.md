---
title: "Update manager showing 10.04.3 instead of 9.10 as next update"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by paichkash on 2012-08-16
hello ..
i am on ubuntu 9.04 and my Update manager is showing 10.04.3 LTS instead of 9.10 as next update .. and when i click upgrade .. 
```
Can not upgrade
An upgrade from 'jaunty' to 'lucid' is not supported with this tool.
```
..please help me update my OS from 9.04 to 10.04 LTS ..

hera re some command outputs
> r@r-desktop:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

---

### Post by paichkash on 2012-08-16
..ok after reading about this issue ... i came to know that i have to use the iso install then upgrade to 10-.04 .. 
now i m downloading the iso...
i m following the folloing posts response which got 19 thumbs up ..

[http://askubuntu.com/questions/47807/skipping-intermediate-ubuntu-os-upgrade-to-latest-one-how-do-i-upgrade-from-9-04/135028#135028](http://askubuntu.com/questions/47807/skipping-intermediate-ubuntu-os-upgrade-to-latest-one-how-do-i-upgrade-from-9-04/135028#135028)

```
You cannot skip versions between upgrades. The version between Jaunty and Lucid is Karmic. I suggest you do backup important data and do a complete reinstall as many things has changed, including the boot loader.

If you do not like a fresh install, you can upgrade using an Alternate CD.

Preparations:
Backup the system (if possible a disk image)
Backup your personal files (the home directory) so you can easily copy the files
Remove all PPA's and non-standard repositories, including their packages
Be prepared for failure, have a Live CD available so you can still boot even if the disk is dead

The upgrade using the alternate CD is described below:
Download ubuntu-9.10-alternate-i386.iso from http://releases.ubuntu.com/karmic/ to your home directory (replace i386 with amd64 if you've a 64-bit system and ubuntu with kubuntu for KDE)


Open a terminal and run:
sudo mount -o loop ~/ubuntu-9.10-alternate-i386.iso /media/cdrom


Start the upgrade by executing:
gksu "sh /media/cdrom/cdromupgrade"

If you're using KDE (Kubuntu):
kdesudo "sh /media/cdrom/cdromupgrade"
Reboot

After this upgrade from 9.04 to 9.10, proceed with the upgrade to 10.04 using:
sudo do-release-upgrade -d
```

but i have a question ..
i would also like to upgrade from ext3 to ext4 .. 
i have heared that if i convert to ext4 only new ext4 based files will take advantage of it.. those which were created under ext3 wont get any benefit.. until these files are updated ..? 

so how should i proceede ?

---

