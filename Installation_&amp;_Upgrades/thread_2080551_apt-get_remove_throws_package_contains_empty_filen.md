---
title: "apt-get remove throws package contains empty filename"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by jinchuriki on 2012-11-04
Hi guys,

Newbie here just started using Ubuntu 11.10 this year. For some reason after trying to install zoneminder a few things stopped working eg. encountered gdm loop issue. I was able to fix it by creating a new user account and slowly move my settings from previous user to the new account.

I encounter a new issue today when trying to re-enable vino. Been searching the forum and following some instructions but unfortunately all to no avail. This thread [http://ubuntuforums.org/showthread.php?t=1861707&page=4](http://ubuntuforums.org/showthread.php?t=1861707&page=4) suggests to reinstall vino.

When trying to remove vino:-

[EMAIL="user@machine:~/.gconf"]user@machine:~/.gconf[/EMAIL]/desktop/gnome/remote_access$ sudo apt-get remove vino
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  vino
0 upgraded, 0 newly installed, 1 to remove and 1320 not upgraded.
After this operation, 565 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ...
dpkg: warning: files list file for package `linux-headers-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-3.0.0-24-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `icedtea-plugin' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

Also tried:-

apt-get clean all
dpkg --configure -a
apt-get remove icedtea-plugin

but all doesn't work.

Can someone shed some light please..

Thanks.

---

### Post by dino99 on 2012-11-04
Be aware of the multiple cross dependencies builtin the system. Why did you get these issues reported by dpkg ? These packages need to be installed.

sudo apt-get install --reinstall linux-libc-dev

do the same for the linux-headers too

---

### Post by jinchuriki on 2012-11-05
Hi dino99, 

Thanks for your reply.

The last thing I did before all hell broke loose was installing zoneminder on my Ubuntu 11.10. Now my goal is to "undo" my zoneminder installation and clean my apt-get so that it can be used again. I will find a zoneminder virtualbox appliance and virtualized it.

Just to double check, I just need to do these right:-

sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall linux-libc-dev

---

### Post by jinchuriki on 2012-11-05
Encountered same error(s):-

user@machine:~$ sudo apt-get install --reinstall linux-headers-generic linux-libc-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libnih-dbus1 libnih1
  linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libnih-dbus1 libnih1
  linux-headers-generic linux-libc-dev
9 upgraded, 2 newly installed, 0 to remove and 1312 not upgraded.
Need to get 868 kB/26.5 MB of archives.
After this operation, 65.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main linux-libc-dev amd64 3.2.0-32.51 [868 kB]
Fetched 868 kB in 4s (192 kB/s)
Preconfiguring packages ...
(Reading database ...
dpkg: warning: files list file for package `linux-headers-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-3.0.0-24-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `icedtea-plugin' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by ibjsb4 on 2012-11-05
Here's my two cents

I have not heard of apt-get clean all.  So if it works, then fine.  But I have always used just apt-get clean.

The icedtea-plugin, maybe try

sudo apt-get install --reinstall icedtea-plugin

dpkg --configure -a always a good idea and so is apt-get -f install (fix broken packages).

And last when it comes to kernels and conflicts:

apt-get dist-upgrade

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

  Probably won't do a bit of good, but that's all you get for two cents  :)

---

### Post by varunendra on 2012-11-06
jinchuriki,
Let me first have the privilege to welcome you to the forums - Welcome aboard :)

Next, a humble suggestion - 11.10 will reach its EOL (End Of Life) in April 2013. While 12.04 LTS is much more stable and will be supported till April 2017. So it makes sense to switch to 12.04 if 11.10 is causing too much troubles.

Accordingly, if the above suggestions don't fix your problem, I'd suggest to back up your data and either do a fresh installation of 12.04 (recommended), or attempt an upgrade (either online, or using the live cd of 12.04). Hopefully, it'll get rid of incompatible or problematic packages automatically.

---

