---
title: "Problem with updates and disk space"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by hanlie-pretorius on 2013-08-22
Hi,

I was busy installing in update when some packages woudln't install, apparently because of a disk space problem.

The system tells me to try sudo apt-get -f install, which gives

hanlie@hanlie-Inspiron-N4020:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans kde-l10n-de language-pack-kde-de language-pack-kde-en
  language-pack-de-base linux-headers-3.2.0-29 linux-headers-3.2.0-37
  language-pack-kde-zh-hans language-pack-kde-en-base kde-l10n-engb
  linux-headers-3.2.0-37-generic-pae linux-headers-3.2.0-29-generic-pae
  language-pack-kde-de-base kde-l10n-zhcn language-pack-zh-hans-base
  language-pack-de language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-52 linux-headers-3.2.0-52-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-52 linux-headers-3.2.0-52-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/12.7 MB of archives.
After this operation, 67.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package linux-headers-3.2.0-52.
(Reading database ... 451516 files and directories currently installed.)
Unpacking linux-headers-3.2.0-52 (from .../linux-headers-3.2.0-52_3.2.0-52.78_all.deb) ...
Unpacking linux-headers-3.2.0-52-generic-pae (from .../linux-headers-3.2.0-52-generic-pae_3.2.0-52.78_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-52-generic-pae_3.2.0-52.78_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-52-generic-pae/include/config/usb/wdm.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-52-generic-pae/include/config/usb/wdm.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-52-generic-pae_3.2.0-52.78_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't get rid of any old kernels etc. because I can't run apt-get or dpkg because of unmet dependencies that were created during the aborted update.

du -sm /*|sort -n gives:

0    /initrd.img
0    /initrd.img.old
0    /proc
0    /sys
0    /vmlinuz
0    /vmlinuz.old
1    /cdrom
1    /dev
1    /lost+found
1    /mnt
1    /root
1    /selinux
1    /srv
1    /tmp
2    /run
9    /bin
9    /sbin
14    /etc
16    /media
180    /opt
263    /boot
445    /var
1089    /home
1422    /lib
3898    /usr

I don't know what this means or what to do with this information.

Can someone please help? I would like to either uninstall the packages that are creating the unmet dependencies or open up some disk space so that the dependencies can be installed.

Thanks

---

### Post by TheFu on 2013-08-22
You need to finish the updates.
That means you need to somehow make more storage available on the partition(s) where it is lacking. The output from 
**$ df -kh **
and 
**$ df -ikh **
would be helpful. 

Storage by directory is less important than storage by partition at this point.  You can attempt to clean up old APT packages, but I doubt it will work until you can make some free space.
**$ sudo apt-get autoclean**

As a last ditch effort, if the /var and /usr directories are located on the same partition, you can move most of the directories under /usr/ off to different storage (be certain to maintain ownership, group and permissions when you do this), finish the upgrades, run autoclean again then move all those files back.    A better idea, if possible .... If /var and /home are on the same partition ... clean up your HOME. Empty the trash, wipe the .adobe and .macromedia folders ... remove/relocate large media files.

BTW, at this point, you are probably going to have the same issue going forward until you give the OS more storage.

I'd say that my daily desktop had only 10G of total storage until last year when I added 4G more.
```
$ df -h
Filesystem        Size  Used Avail Use% Mounted on
/dev/vda1          14G   10G  2.6G  80% /
```
and the inodes:
```
$ df -i
Filesystem       Inodes  IUsed  IFree IUse% Mounted on
/dev/vda1        884736 492671 392065   56% /
```

I've run out of inodes a few times on virtual machines. That sucks to have GB of free storage, but no more inodes, so no new files can be created. Hopefully, you don't have that issue.

I hope this reply makes sense. If not, ask and I'll try to do better.

---

### Post by hanlie-pretorius on 2013-08-23
Thanks for the reply,
 df -kh and df -ikh revealed that the space was used 90% and 99% respectively.

So I moved my var/share directory to an external hard drive, cleaned up some of the old kernels and then the numbers fell to about 50% and 70% respectively.

I copied the var/share files back, but the installation seemed to be broken, so I have reinstalled ubuntu.

I had dozens of old kernels, which was obviously the space hog, because I use my Windows partition as a file store rather than ubuntu.

So I'll have to diligently remove old kernels from now on.

Thanks for yout help.

---

### Post by TheFu on 2013-08-23
If you were out of inodes, then you have a major issue and it will happen again.  The default inode counts for small partitions is woefully small.

Glad that reinstalling fixed the issue short-term.  Used to be that 3-5 old kernels were retained. Something got changed/broken around 12.04 related to old kernel cleanup.  I wrote a script here: [http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt](http://blog.jdpfu.com/2013/02/23/cleanup-old-kernels-from-apt) that will help cleanup old kernels. I understand that Canonical or Debian has put back the old kernel cleanup in 13.04 patches, so we shouldn't have this same issue in 14.04, the next LTS.

To avoid the out-of-inode issue again, I think we need to recreate the file system and set a higher number of inodes - perhaps 3x-10x more.  There may be a way to do it after the file system is created, I don't know.  **tune2efs** looks like the command. Sorry I don't know more. [http://unix.stackexchange.com/questions/26598/how-can-i-increase-the-number-of-inodes-in-an-ext4-filesystem](http://unix.stackexchange.com/questions/26598/how-can-i-increase-the-number-of-inodes-in-an-ext4-filesystem) seems to agree with my belief that inodes need to be set at file system creation time.

---

### Post by hanlie-pretorius on 2013-08-23
Thanks, I will investigate and try your script when the next kernel update comes through.

---

