---
title: "Won't let me upgrade... Command line results in thread"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by cmlewin on 2008-05-06
> 
justin@justin-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  capplets-data gnome-control-center gnome-system-monitor gvfs gvfs-backends
  gvfs-fuse jockey-common jockey-gtk libgnome-window-settings1 libgvfscommon0
  sudo
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3551kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main sudo 1.6.9p10-1ubuntu3.1 [176kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main capplets-data 1:2.22.1-0ubuntu4.1 [367kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-control-center 1:2.22.1-0ubuntu4.1 [487kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libgnome-window-settings1 1:2.22.1-0ubuntu4.1 [68.6kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-system-monitor 2.22.1-0ubuntu1 [1481kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libgvfscommon0 0.2.3-0ubuntu5
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gvfs-backends 0.2.3-0ubuntu5
  Unable to connect to us.archive.ubuntu.com http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gvfs 0.2.3-0ubuntu5
  Unable to connect to us.archive.ubuntu.com http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gvfs-fuse 0.2.3-0ubuntu5
  Unable to connect to us.archive.ubuntu.com http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main jockey-gtk 0.3.3-0ubuntu8
  Unable to connect to us.archive.ubuntu.com http:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main jockey-common 0.3.3-0ubuntu8
  Unable to connect to us.archive.ubuntu.com http:
Fetched 2579kB in 3min52s (11.1kB/s)                    
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_0.2.3-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_0.2.3-0ubuntu5_i386.deb)  Could not connect to us.archive.ubuntu.com:80 (91.189.88.31), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_0.2.3-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_0.2.3-0ubuntu5_i386.deb)  Unable to connect to us.archive.ubuntu.com http:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs_0.2.3-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs_0.2.3-0ubuntu5_i386.deb)  Unable to connect to us.archive.ubuntu.com http:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_0.2.3-0ubuntu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_0.2.3-0ubuntu5_i386.deb)  Unable to connect to us.archive.ubuntu.com http:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.3.3-0ubuntu8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.3.3-0ubuntu8_all.deb)  Unable to connect to us.archive.ubuntu.com http:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.3.3-0ubuntu8_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.3.3-0ubuntu8_all.deb)  Unable to connect to us.archive.ubuntu.com http:
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


what to do peoples? please help. thanks!

---

### Post by Pumalite on 2008-05-06
Check your connection. Try changing Servers
Post:
cat /etc/apt/sources.list

---

### Post by cmlewin on 2008-05-06
My connection works fine as I'm on firefox now... And just to let you know I was able to update/upgrade when I tried a couple days ago.

> 
justin@justin-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


thanks again.

---

### Post by Pumalite on 2008-05-06
Your sources.list is fine. The Servers have been slow today. Try tomorrow. Use USA, Main or others. You can go to System>Administration>Software Sources>Download From>Other>Let it choose the best Server for you.

---

### Post by cmlewin on 2008-05-06
fixed. mods delete.

---

### Post by letrappe on 2008-05-13
I didn't want to post a new question/problem on the main forum when this thread is on the same lines as my own issues.  Hopefully, someone is still looking at this one.

Ubuntu Server 7.10
LAMP install
ssh
updates
static ip
dns servers changed to opendns
sources.list:


I can ping google, and several other websites
I can ping security.ubuntu.com

Everytime I try to "apt-get update", I get a boat load of "Failed to fetch" 302 Redirect

If I try to install anything, I get the same 302 Redirect message.

any assistance is helpful.  I've been researching this for the past week with no successful fix.

Could it be that the servers really are that busy that I'm getting all of the Redirects?

---

### Post by Pumalite on 2008-05-13
When did the problem start?

---

