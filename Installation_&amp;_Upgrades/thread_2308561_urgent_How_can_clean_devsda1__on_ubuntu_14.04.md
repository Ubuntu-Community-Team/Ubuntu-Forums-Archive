---
title: "urgent: How can clean /dev/sda1  on ubuntu 14.04 ?"
date: 2016-01-04
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2016-01-04
df

```
Filesystem                  1K-blocks    Used Available Use% Mounted on
udev                          1013428       4   1013424   1% /dev
tmpfs                          204916     684    204232   1% /run
/dev/mapper/ubuntu--vg-root 205009664 7400804 187171844   4% /
none                                4       0         4   0% /sys/fs/cgroup
none                             5120       0      5120   0% /run/lock
none                          1024564       0   1024564   0% /run/shm
none                           102400       0    102400   0% /run/user
/dev/sda1                      240972  240972         0 100% /boot
```
---------------------------------------------------------------------------------------
I can not update or upgrade because of this
/dev/sda1                      240972  240972         0 100% /boot

---

### Post by matt_symes on 2016-01-04
Hi

Let's check how many old kernels you have installed. Open a terminal and post the output of this command into your next post.

```
dpkg -l | grep linux-image
```

Kind regards

---

### Post by grahammechanical on 2016-01-04
The Grub boot menu has an option called Advanced options for Ubuntu. It is a sub-menu and we can select to load Linux with recovery mode. The recovery mode menu will have an option to Clean - Try to make free space. It is a script that will run the apt-get clean & autoremove commands for us. Resume restarts the OS loading process.

Regards.

---

### Post by hoboy on 2016-01-04
```
sudo  apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-3.19.0-30 linux-headers-3.19.0-30-generic
  linux-headers-3.19.0-31 linux-headers-3.19.0-31-generic
  linux-headers-3.19.0-32 linux-headers-3.19.0-32-generic
  linux-headers-3.19.0-39 linux-headers-3.19.0-39-generic
  linux-headers-3.19.0-41 linux-headers-3.19.0-41-generic
  linux-image-3.19.0-25-generic linux-image-3.19.0-28-generic
  linux-image-3.19.0-30-generic linux-image-3.19.0-31-generic
  linux-image-3.19.0-32-generic linux-image-3.19.0-39-generic
  linux-image-3.19.0-41-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-extra-3.19.0-30-generic
  linux-image-extra-3.19.0-31-generic linux-image-extra-3.19.0-32-generic
  linux-image-extra-3.19.0-39-generic linux-image-extra-3.19.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.19.0-41-generic linux-image-3.19.0-42-generic
Suggested packages:
  fdutils linux-lts-vivid-tools
The following NEW packages will be installed
  linux-image-3.19.0-41-generic linux-image-3.19.0-42-generic
0 to upgrade, 2 to newly install, 0 to remove and 16 not to upgrade.
8 not fully installed or removed.
Need to get 33.5 MB of archives.
After this operation, 94.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-3.19.0-42-generic amd64 3.19.0-42.48~14.04.1 [16.7 MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-3.19.0-41-generic amd64 3.19.0-41.46~14.04.2 [16.7 MB]
Fetched 33.5 MB in 49s (670 kB/s)                                              
(Reading database ... 346386 files and directories currently installed.)
Preparing to unpack .../linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/abi-3.19.0-42-generic' to '/boot/abi-3.19.0-42-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
Preparing to unpack .../linux-image-3.19.0-41-generic_3.19.0-41.46~14.04.2_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-41-generic (3.19.0-41.46~14.04.2) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.19.0-41-generic_3.19.0-41.46~14.04.2_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-3.19.0-41-generic' to '/boot/System.map-3.19.0-41-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-41-generic /boot/vmlinuz-3.19.0-41-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-41-generic /boot/vmlinuz-3.19.0-41-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-3.19.0-41-generic_3.19.0-41.46~14.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I am using the server version no graphic

```
sudo  apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.19.0-41-generic : Depends: linux-image-3.19.0-41-generic but it is not installed
 linux-image-extra-3.19.0-42-generic : Depends: linux-image-3.19.0-42-generic but it is not installed
 linux-image-generic-lts-vivid : Depends: linux-image-3.19.0-42-generic but it is not installed
                                 Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.
```

---

### Post by matt_symes on 2016-01-04
Hi

```
sudo dpkg -P linux-image{,-extra}-3.19.0-{25,28,30,31,32}-generic
```

```
sudo apt-get -f install
```

```
sudo apt-get autoremove
```

Kind regards

---

### Post by hoboy on 2016-01-04
My goodness you are GOD :)
tks you made my day

> **matt_symes said:**
> Hi

```
sudo dpkg -P linux-image{,-extra}-3.19.0-{25,28,30,31,32}-generic
```

```
sudo apt-get -f install
```

```
sudo apt-get autoremove
```

Kind regards

Honestly matt_symes  how does one learn scripting in like you ? 
any book to read ? witch ? or tutorial ?

---

### Post by matt_symes on 2016-01-04
Hi

> **hoboy said:**
> Honestly matt_symes  how does one learn scripting in like you ? 
any book to read ? witch ? or tutorial ?

I've just picked it up over the 5 years I've been using Linux full time and in my dabbling before that. There certainly wasn't one source.

Helping on these forums really started me off. 

Learning how to get the best from the man pages really helps.

For bash:

[http://mywiki.wooledge.org/BASH](http://mywiki.wooledge.org/BASH)
[http://wiki.bash-hackers.org/](http://wiki.bash-hackers.org/)

The stack exchange forums are excellent.

There are some podcasts i watch and some blogs i follow and some IRC channels i lurk in.

The thing is i like technology and I'm prepared to put the time in to learn new things. I'm prepared to read and play.

Another thing i did was to set goals (eg: i want to learn how to build a PXE server) then i researched how to do it, how to secure it and how to break it.

Just make sure what you read is up to date and relevant.

From the forums, there is also this monster thread courtesy of Cortman.

[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

You should know that i consider myself a beginner in Linux though. The more i learn the more, i realise there are gaps in my knowledge and the more i realise the gaps are greater and more numerous than i realised :)

Kind regards

---

### Post by hoboy on 2016-01-05
Tks very very much

---

