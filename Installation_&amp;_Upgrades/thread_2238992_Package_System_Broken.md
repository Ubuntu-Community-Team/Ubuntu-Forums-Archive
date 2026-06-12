---
title: "Package System Broken ?"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by Raggylad on 2014-08-11
Hi,
I am running 12.04 LTS but am currently unable to run updates (apparently there are 116 available) or upgrade to 14.04 LTS.

When I start Update Manager, I get the following error message:```
[INDENT]'The package system is broken.  If you are using third party dependencies (*comment: I'm not, so far as I know)* then disable them, since they are a common source of problems. Now run apt-get install -f.'
[/INDENT]

```
Pressing the 'details' button gives the following:```
[INDENT]'The following packages have unmet dependencies:

linux-headers-generic: Depends: linux-headers-3.2.0-65-generic but it is not installed
linux-headers-generic-lts-quantal: Depends: linux-headers-3.5.0-52-generic but it is not installed
linux-headers-generic-pae: Depends: linux-headers-3.2.0-65-generic-pae but it is not installed'
[/INDENT]

```
Running apt-get install -f in a terminal gives the following:```
[INDENT]'E: Invalid operation install-f
unick@ubuntu:~$  apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?'
[/INDENT]

```
I have now reached the limits of my competence and would be very grateful for any help or advice from those more knowledgeable than me.

Many thanks.

Nick

---

### Post by kansasnoob on 2014-08-11
You need to be root (sudo):

```
sudo apt-get -f install
```

Also please post the full output of these three commands:

```
lsb_release -a
```

```
uname -r
```

```
ls /boot
```

---

### Post by ajgreeny on 2014-08-11
It looks as if you have previously updated the hardware enablement stack to that of quantal, and it is that quantal version which is now EOL.

You may need to search for any other quantal packages by name that you have already installed (synaptic is excellent for that purpose) and  replace them either with the original precise versions, or probably better, newest trusty versions. Doing this will probably also remove other packages and replace them with new ones.

This recent HWE stack updating seems to have been a complete disaster for many users,with a huge number reporting the same sort of problems you have seen here.  I did not update my HWE from the original until this most recent update to the trusty version, which happened with no major problems, and now luckily for me, the whole system of 12.04 with the 14.04 HWE is running smooth as silk.

---

### Post by Raggylad on 2014-08-11
Thank you.  The results were as follows:

> **kansasnoob said:**
> You need to be root (sudo):

```
sudo apt-get -f install
```

Also please post the full output of these three commands:

```
lsb_release -a
```

```
uname -r
```

```
ls /boot
```

To the first command in root, after fetching the updates:```
[INDENT]Fetched 65.1 MB in 3min 7s (348 kB/s)                                                                                                  
Selecting previously unselected package linux-headers-3.5.0-54.
(Reading database ... 1086850 files and directories currently installed.)
Unpacking linux-headers-3.5.0-54 (from .../linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.5.0-54/drivers/rapidio/devices/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-54/drivers/rapidio/devices/Makefile'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-3.5.0-54-generic.
Unpacking linux-headers-3.5.0-54-generic (from .../linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.5.0-54-generic/include/config/keyboard/stmpe.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-54-generic/include/config/keyboard/stmpe.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-image-3.2.0-67-generic-pae.
Unpacking linux-image-3.2.0-67-generic-pae (from .../linux-image-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb) ...
Done.
Preparing to replace linux-image-generic-pae 3.2.0.65.77 (using .../linux-image-generic-pae_3.2.0.67.79_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-67.
Unpacking linux-headers-3.2.0-67 (from .../linux-headers-3.2.0-67_3.2.0-67.101_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-67_3.2.0-67.101_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-67/sound/synth/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-67/sound/synth/Makefile'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-3.2.0-67-generic-pae.
Unpacking linux-headers-3.2.0-67-generic-pae (from .../linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-67-generic-pae/include/config/pps/client/ldisc.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-67-generic-pae/include/config/pps/client/ldisc.h'): No space left on device
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-3.2.0-67-generic.
Unpacking linux-headers-3.2.0-67-generic (from .../linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-67-generic/include/config/sbe/2t3e3.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-67-generic/include/config/sbe/2t3e3.h'): No space left on device
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb
 /var/cache/apt/archives/linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-67_3.2.0-67.101_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

```
And the answers to the three other commands were:```
[INDENT]unick@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
unick@ubuntu:~$ uname -r
3.5.0-52-generic
unick@ubuntu:~$ ls /boot
abi-3.2.0-45-generic-pae     config-3.2.0-58-generic-pae      initrd.img-3.5.0-34-generic      System.map-3.5.0-44-generic
abi-3.2.0-48-generic-pae     config-3.2.0-59-generic-pae      initrd.img-3.5.0-36-generic      System.map-3.5.0-45-generic
abi-3.2.0-49-generic-pae     config-3.2.0-60-generic-pae      initrd.img-3.5.0-37-generic      System.map-3.5.0-46-generic
abi-3.2.0-51-generic-pae     config-3.2.0-61-generic-pae      initrd.img-3.5.0-39-generic      System.map-3.5.0-47-generic
abi-3.2.0-52-generic-pae     config-3.2.0-63-generic-pae      initrd.img-3.5.0-40-generic      System.map-3.5.0-48-generic
abi-3.2.0-53-generic-pae     config-3.2.0-64-generic-pae      initrd.img-3.5.0-41-generic      System.map-3.5.0-49-generic
abi-3.2.0-54-generic-pae     config-3.2.0-65-generic-pae      initrd.img-3.5.0-42-generic      System.map-3.5.0-51-generic
abi-3.2.0-55-generic-pae     config-3.2.0-67-generic-pae      initrd.img-3.5.0-43-generic      System.map-3.5.0-52-generic
abi-3.2.0-56-generic-pae     config-3.5.0-23-generic          initrd.img-3.5.0-44-generic      vmlinuz-3.2.0-45-generic-pae
abi-3.2.0-57-generic-pae     config-3.5.0-32-generic          initrd.img-3.5.0-45-generic      vmlinuz-3.2.0-48-generic-pae
abi-3.2.0-58-generic-pae     config-3.5.0-34-generic          initrd.img-3.5.0-46-generic      vmlinuz-3.2.0-49-generic-pae
abi-3.2.0-59-generic-pae     config-3.5.0-36-generic          initrd.img-3.5.0-47-generic      vmlinuz-3.2.0-51-generic-pae
abi-3.2.0-60-generic-pae     config-3.5.0-37-generic          initrd.img-3.5.0-48-generic      vmlinuz-3.2.0-52-generic-pae
abi-3.2.0-61-generic-pae     config-3.5.0-39-generic          initrd.img-3.5.0-49-generic      vmlinuz-3.2.0-53-generic-pae
abi-3.2.0-63-generic-pae     config-3.5.0-40-generic          initrd.img-3.5.0-51-generic      vmlinuz-3.2.0-54-generic-pae
abi-3.2.0-64-generic-pae     config-3.5.0-41-generic          initrd.img-3.5.0-52-generic      vmlinuz-3.2.0-55-generic-pae
abi-3.2.0-65-generic-pae     config-3.5.0-42-generic          memtest86+.bin                   vmlinuz-3.2.0-56-generic-pae
abi-3.2.0-67-generic-pae     config-3.5.0-43-generic          memtest86+_multiboot.bin         vmlinuz-3.2.0-57-generic-pae
abi-3.5.0-23-generic         config-3.5.0-44-generic          System.map-3.2.0-45-generic-pae  vmlinuz-3.2.0-58-generic-pae
abi-3.5.0-32-generic         config-3.5.0-45-generic          System.map-3.2.0-48-generic-pae  vmlinuz-3.2.0-59-generic-pae
abi-3.5.0-34-generic         config-3.5.0-46-generic          System.map-3.2.0-49-generic-pae  vmlinuz-3.2.0-60-generic-pae
abi-3.5.0-36-generic         config-3.5.0-47-generic          System.map-3.2.0-51-generic-pae  vmlinuz-3.2.0-61-generic-pae
abi-3.5.0-37-generic         config-3.5.0-48-generic          System.map-3.2.0-52-generic-pae  vmlinuz-3.2.0-63-generic-pae
abi-3.5.0-39-generic         config-3.5.0-49-generic          System.map-3.2.0-53-generic-pae  vmlinuz-3.2.0-64-generic-pae
abi-3.5.0-40-generic         config-3.5.0-51-generic          System.map-3.2.0-54-generic-pae  vmlinuz-3.2.0-65-generic-pae
abi-3.5.0-41-generic         config-3.5.0-52-generic          System.map-3.2.0-55-generic-pae  vmlinuz-3.2.0-67-generic-pae
abi-3.5.0-42-generic         grub                             System.map-3.2.0-56-generic-pae  vmlinuz-3.5.0-23-generic
abi-3.5.0-43-generic         initrd.img-3.2.0-45-generic-pae  System.map-3.2.0-57-generic-pae  vmlinuz-3.5.0-32-generic
abi-3.5.0-44-generic         initrd.img-3.2.0-48-generic-pae  System.map-3.2.0-58-generic-pae  vmlinuz-3.5.0-34-generic
abi-3.5.0-45-generic         initrd.img-3.2.0-49-generic-pae  System.map-3.2.0-59-generic-pae  vmlinuz-3.5.0-36-generic
abi-3.5.0-46-generic         initrd.img-3.2.0-51-generic-pae  System.map-3.2.0-60-generic-pae  vmlinuz-3.5.0-37-generic
abi-3.5.0-47-generic         initrd.img-3.2.0-52-generic-pae  System.map-3.2.0-61-generic-pae  vmlinuz-3.5.0-39-generic
abi-3.5.0-48-generic         initrd.img-3.2.0-53-generic-pae  System.map-3.2.0-63-generic-pae  vmlinuz-3.5.0-40-generic
abi-3.5.0-49-generic         initrd.img-3.2.0-54-generic-pae  System.map-3.2.0-64-generic-pae  vmlinuz-3.5.0-41-generic
abi-3.5.0-51-generic         initrd.img-3.2.0-55-generic-pae  System.map-3.2.0-65-generic-pae  vmlinuz-3.5.0-42-generic
abi-3.5.0-52-generic         initrd.img-3.2.0-56-generic-pae  System.map-3.2.0-67-generic-pae  vmlinuz-3.5.0-43-generic
config-3.2.0-45-generic-pae  initrd.img-3.2.0-57-generic-pae  System.map-3.5.0-23-generic      vmlinuz-3.5.0-44-generic
config-3.2.0-48-generic-pae  initrd.img-3.2.0-58-generic-pae  System.map-3.5.0-32-generic      vmlinuz-3.5.0-45-generic
config-3.2.0-49-generic-pae  initrd.img-3.2.0-59-generic-pae  System.map-3.5.0-34-generic      vmlinuz-3.5.0-46-generic
config-3.2.0-51-generic-pae  initrd.img-3.2.0-60-generic-pae  System.map-3.5.0-36-generic      vmlinuz-3.5.0-47-generic
config-3.2.0-52-generic-pae  initrd.img-3.2.0-61-generic-pae  System.map-3.5.0-37-generic      vmlinuz-3.5.0-48-generic
config-3.2.0-53-generic-pae  initrd.img-3.2.0-63-generic-pae  System.map-3.5.0-39-generic      vmlinuz-3.5.0-49-generic
config-3.2.0-54-generic-pae  initrd.img-3.2.0-64-generic-pae  System.map-3.5.0-40-generic      vmlinuz-3.5.0-51-generic
config-3.2.0-55-generic-pae  initrd.img-3.2.0-65-generic-pae  System.map-3.5.0-41-generic      vmlinuz-3.5.0-52-generic
config-3.2.0-56-generic-pae  initrd.img-3.5.0-23-generic      System.map-3.5.0-42-generic
config-3.2.0-57-generic-pae  initrd.img-3.5.0-32-generic      System.map-3.5.0-43-generic
[/INDENT]

```
None of which means anything to me, except that this attempt hasn't worked either.

Very grateful for any further advice.

Many thanks.

Nick

---

### Post by Raggylad on 2014-08-11
> **ajgreeny said:**
> It looks as if you have previously updated the hardware enablement stack to that of quantal, and it is that quantal version which is now EOL.

You may need to search for any other quantal packages by name that you have already installed (synaptic is excellent for that purpose) and  replace them either with the original precise versions, or probably better, newest trusty versions. Doing this will probably also remove other packages and replace them with new ones.

This recent HWE stack updating seems to have been a complete disaster for many users,with a huge number reporting the same sort of problems you have seen here.  I did not update my HWE from the original until this most recent update to the trusty version, which happened with no major problems, and now luckily for me, the whole system of 12.04 with the 14.04 HWE is running smooth as silk.

Many thanks for the help.  However, I'm sorry - my fault for being ignorant - but I didn't understand much of the advice you have given above (HWE ? Quantal ? Hardware enablement stack ? EOL ?). I've only ever updated 12.04 using what was offered by the Update Manager - I'm very much a user, not a coder.

Nick

---

### Post by kansasnoob on 2014-08-11
The first thing that jumps out at me is **[COLOR="#FF0000"]No space left on device[/COLOR]**. So we need to investigate a bit further before we decide just what to do, likely removing some kernels but we need to be extremely cautious!

So post the output of these three commands (just as typed here):

```
sudo parted -l
```

```
df -H
```

```
sudo du -sh /*
```

The latter one takes quite a while to run so be patient, and don't worry about no such file or permission denied warnings, we just need to see exactly how cramped for space you are and where it's cramped. And that is a lower case L at the end of the first command.

Oh, maybe should see if you already have synaptic installed, so also post the output of:

```
apt-cache policy synaptic
```

I'm particularly curious about that because I always use synaptic to remove kernels. There are other ways to do it but I wouldn't personally be comfortable instructing you in how to do it, someone else will though.

Actually you should be safe trying:

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

That should clear at least a bit of space but likely not enough to sustain you for long.

---

### Post by kansasnoob on 2014-08-11
> **Raggylad said:**
> Many thanks for the help.  However, I'm sorry - my fault for being ignorant - but I didn't understand much of the advice you have given above (HWE ? Quantal ? Hardware enablement stack ? EOL ?). I've only ever updated 12.04 using what was offered by the Update Manager - I'm very much a user, not a coder.

Nick

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

But right now lets concentrate on the free space issue ;)

---

### Post by Jonathan Precise on 2014-08-11
> unable to create `/usr/src/linux-headers-3.5.0-54/drivers/rapidio/devices/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-54/drivers/rapidio/devices/Makefile'): No space left on device

Is the problem. Try cleaning out some kernels from /boot.

---

### Post by Raggylad on 2014-08-11
> **kansasnoob said:**
> The first thing that jumps out at me is **[COLOR=#FF0000]No space left on device[/COLOR]**. So we need to investigate a bit further before we decide just what to do, likely removing some kernels but we need to be extremely cautious!

So post the output of these three commands (just as typed here):

```
sudo parted -l
```

```
df -H
```

```
sudo du -sh /*
```

The latter one takes quite a while to run so be patient, and don't worry about no such file or permission denied warnings, we just need to see exactly how cramped for space you are and where it's cramped. And that is a lower case L at the end of the first command.

Oh, maybe should see if you already have synaptic installed, so also post the output of:

```
apt-cache policy synaptic
```

I'm particularly curious about that because I always use synaptic to remove kernels. There are other ways to do it but I wouldn't personally be comfortable instructing you in how to do it, someone else will though.

Actually you should be safe trying:

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

That should clear at least a bit of space but likely not enough to sustain you for long.

Taking the last commands first, there was no success:```
[INDENT]unick@ubuntu:~$ sudo apt-get autoclean
sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
W: Not using locking for read only lock file /var/cache/apt/archives/lock
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
unick@ubuntu:~$ sudo apt-get clean
sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
W: Not using locking for read only lock file /var/cache/apt/archives/lock
unick@ubuntu:~$ sudo apt-get autoremove
sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
[/INDENT]

```
For the others:```
[INDENT]**sudo parted -l**
sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ntfs         boot


Model: Seagate Portable (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  ntfs         boot

[/INDENT]
[INDENT]**df -H**
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       19G   13G  4.9G  73% /
udev            2.2G  4.1k  2.2G   1% /dev
tmpfs           423M  877k  422M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            2.2G  160k  2.2G   1% /run/shm
/dev/sda1       121G   60G   61G  50% /host
/dev/sdb1       251G  159G   92G  64% /media/Expansion Drive__

**sudo du -sh /***
[/INDENT]
[INDENT]sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
8.5M    /bin
799M    /boot
4.0K    /cdrom
4.0K    /dev
14M    /etc
du: cannot access `/home/unick/.gvfs': Permission denied
903M    /home
55G    /host
0    /initrd.img
0    /initrd.img.old
4.2G    /lib
16K    /lost+found
148G    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/3513/task/3513/fd/3': No such file or directory
du: cannot access `/proc/3513/task/3513/fdinfo/3': No such file or directory
du: cannot access `/proc/3513/fd/3': No such file or directory
du: cannot access `/proc/3513/fdinfo/3': No such file or directory
0    /proc
92K    /root
1012K    /run
8.6M    /sbin
4.0K    /selinux
4.0K    /srv
0    /sys
6.9M    /tmp
*(a bit missing here - lost it as the terminal scrolled !)*
[/INDENT]
[INDENT]4.0K    /dev
14M    /etc
du: cannot access `/home/unick/.gvfs': Permission denied
903M    /home
55G    /host
0    /initrd.img
0    /initrd.img.old
4.2G    /lib
16K    /lost+found
148G    /media
4.0K    /mnt
4.0K    /opt
du: cannot access `/proc/3507/task/3507/fd/3': No such file or directory
du: cannot access `/proc/3507/task/3507/fdinfo/3': No such file or directory
du: cannot access `/proc/3507/fd/3': No such file or directory
du: cannot access `/proc/3507/fdinfo/3': No such file or directory
0    /proc
92K    /root
1012K    /run
8.6M    /sbin
4.0K    /selinux
4.0K    /srv
0    /sys
6.9M    /tmp
du: cannot access `/usr/share/doc/libisccfg82/copyright': Input/output error
5.0G    /usr
716M    /var
0    /vmlinuz
0    /vmlinuz.old

[/INDENT]
[INDENT]**apt-cache policy synaptic**

synaptic:
  Installed: (none)
  Candidate: 0.75.9ubuntu1.1
  Version table:
     0.75.9ubuntu1.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/universe i386 Packages
     0.75.9ubuntu1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
[/INDENT]

```

---

### Post by Bashing-om on 2014-08-11
Raggylad; Hello;

UnGood !
> 
sudo: unable to open /var/lib/sudo/unick/2: [color=red]Read-only file system[/color]


How bout taking a gentle poke and prod at the operating system, see what results when a 'simple' file system check is conducted ?
Terminal command - with nothing else than the terminal open/active:
```

sudo touch /forcefsck
sudo shutdown -r now

``` Which will set up the file system checks on the next boot, and the following command reboots the system.

If it runs clean then ->
Now what results from kansasnoob's commands ?

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-11
> **Bashing-om said:**
> Raggylad; Hello;

UnGood !


How bout taking a gentle poke and prod at the operating system, see what results when a 'simple' file system check is conducted ?
Terminal command - with nothing else than the terminal open/active:
```

sudo touch /forcefsck
sudo shutdown -r now

``` Which will set up the file system checks on the next boot, and the following command reboots the system.

If it runs clean then ->
Now what results from kansasnoob's commands ?[INDENT][INDENT]my bit to try and help[/INDENT]
[/INDENT]


Many thanks for the suggestion.  I ran the file sytemcheck and then kansasnoob's commands again - with no joy.  

Here's what I got;```
[INDENT]
unick@ubuntu:~$ sudo apt-get autoclean
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del librsvg2-common 2.40.2-1 [4,962 B]
Del libfontconfig1 2.11.0-0ubuntu4.1 [124 kB]
Del fontconfig-config 2.11.0-0ubuntu4.1 [47.4 kB]
Del p11-kit-modules 0.20.2-2ubuntu2 [66.1 kB]
Del libsecret-1-0 0.16-0ubuntu1 [86.9 kB]
Del libtiff5 4.0.3-7ubuntu0.1 [142 kB]
Del libnih-dbus1 1.0.3-4ubuntu25 [13.6 kB]
Del gnome-session 3.9.90-0ubuntu12 [10.4 kB]
Del gir1.2-gnomekeyring-1.0 3.8.0-2 [5,922 B]
Del unity-lens-music 6.9.0+13.10.20131011-0ubuntu1 [66.4 kB]
Del libpangoft2-1.0-0 1.36.3-1ubuntu1 [32.6 kB]
Del libcairo2 1.13.0~20140204-0ubuntu1 [550 kB]
Del gnome-bluetooth 3.8.2.1-0ubuntu4 [130 kB]
Del libcap2 1:2.24-0ubuntu2 [10.8 kB]
Del seahorse 3.10.2-0ubuntu1 [419 kB]
Del libatk1.0-data 2.10.0-2ubuntu2 [13.7 kB]
Del libgcr-ui-3-1 3.10.1-1 [128 kB]
Del libwayland-client0 1.4.0-1ubuntu1 [20.9 kB]
Del libaudit-common 1:2.3.2-2ubuntu1 [5,372 B]
Del liblcms2-2 2.5-0ubuntu4 [129 kB]
Del librsvg2-2 2.40.2-1 [90.0 kB]
Del libwayland-server0 1.4.0-1ubuntu1 [25.9 kB]
Del libgtk-3-0 3.10.8-0ubuntu1.2 [1,919 kB]
Del libgail-3-0 3.10.8-0ubuntu1.2 [20.0 kB]
Del libjson-c2 0.11-3ubuntu1.2 [22.5 kB]
Del libpangox-1.0-0 0.0.2-4ubuntu1 [40.8 kB]
Del fonts-dejavu-core 2.34-1ubuntu1 [1,024 kB]
Del glib-networking 2.40.0-1 [39.2 kB]
Del gnome-settings-daemon-schemas 3.8.6.1-0ubuntu11.2 [44.2 kB]
Del libcups2 1.7.2-0ubuntu1.1 [175 kB]
Del libxml2 2.9.1+dfsg1-3ubuntu4.3 [555 kB]
Del libqt5sql5-sqlite 5.2.1+dfsg-1ubuntu14.2 [30.8 kB]
Del libharfbuzz0b 0.9.27-1 [125 kB]
Del unity-lens-video 0.3.15+13.10.20130920-0ubuntu1 [31.8 kB]
Del gnome-keyring 3.10.1-1ubuntu4 [534 kB]
Del libcgmanager0 0.24-0ubuntu7 [25.3 kB]
Del libaccountsservice0 0.6.35-0ubuntu7.1 [67.7 kB]
Del libatk-bridge2.0-0 2.10.2-2ubuntu1 [46.6 kB]
Del libudev1 204-5ubuntu20.3 [34.3 kB]
Del gsettings-desktop-schemas 3.10.1-0ubuntu1 [24.0 kB]
Del libgnome-keyring0 3.8.0-2 [52.8 kB]
Del gtk3-engines-unico 1.0.3+14.04.20140109-0ubuntu1 [8,550 B]
Del ttf-freefont 20120503-4 [1,744 B]
Del sysv-rc 2.88dsf-41ubuntu6 [36.5 kB]
Del accountsservice 0.6.35-0ubuntu7.1 [60.6 kB]
Del libsystemd-login0 204-5ubuntu20.3 [27.2 kB]
Del libatspi2.0-0 2.10.2.is.2.10.1-0ubuntu1 [51.6 kB]
Del libxkbcommon0 0.4.1-0ubuntu1 [88.7 kB]
Del libp11-kit0 0.20.2-2ubuntu2 [71.4 kB]
Del libgcr-base-3-1 3.10.1-1 [170 kB]
Del libcolord1 1.0.6-1 [81.4 kB]
Del libgraphite2-3 1.2.4-1ubuntu1 [54.4 kB]
Del libgnome-keyring-common 3.8.0-2 [5,536 B]
Del gcr 3.10.1-1 [48.1 kB]
Del libatk1.0-0 2.10.0-2ubuntu2 [49.5 kB]
Del xserver-common 2:1.15.1-0ubuntu2 [27.2 kB]
Del libjson0 0.11-3ubuntu1.2 [1,078 B]
Del ttf-dejavu-core 2.34-1ubuntu1 [2,956 B]
Del libpangoxft-1.0-0 1.36.3-1ubuntu1 [14.9 kB]
Del metacity 1:2.34.13-0ubuntu4 [220 kB]
Del xserver-common-lts-quantal 3:6 [1,742 B]
Del glib-networking-services 2.40.0-1 [13.7 kB]
Del compiz 1:0.9.11.2+14.04.20140714-0ubuntu1 [4,048 B]
Del libgdk-pixbuf2.0-0 2.30.7-0ubuntu1 [155 kB]
Del gnome-control-center 1:3.6.3-0ubuntu56.1 [460 kB]
Del libnih1 1.0.3-4ubuntu25 [46.3 kB]
Del unity-lens-files 7.1.0+13.10.20130920-0ubuntu1 [59.3 kB]
Del libgck-1-0 3.10.1-1 [73.0 kB]
Del libwayland-cursor0 1.4.0-1ubuntu1 [9,812 B]
Del libjbig0 2.0-2ubuntu4.1 [25.1 kB]
Del unity 7.2.2+14.04.20140714-0ubuntu1.1 [1,427 kB]
Del libgtk-3-common 3.10.8-0ubuntu1.2 [167 kB]
Del liblzma5 5.1.1alpha+20120614-2ubuntu2 [84.2 kB]
Del indicator-datetime 13.10.0+14.04.20140415.3-0ubuntu1 [146 kB]
Del libtasn1-6 3.4-3ubuntu0.1 [42.7 kB]
Del libgnutls26 2.12.23-12ubuntu2.1 [374 kB]
Del p11-kit 0.20.2-2ubuntu2 [64.2 kB]
Del libgnome-desktop-3-7 3.8.4-0ubuntu3 [103 kB]
Del base-files 7.2ubuntu5.1 [62.0 kB]
Del gnome-settings-daemon 3.8.6.1-0ubuntu11.2 [482 kB]
Del libgcrypt11 1.5.3-2ubuntu4 [237 kB]
Del glib-networking-common 2.40.0-1 [9,086 B]
Del libgtk-3-bin 3.10.8-0ubuntu1.2 [18.0 kB]
Del libgcr-3-1 3.10.1-1 [1,850 B]
Del libpango1.0-0 1.36.3-1ubuntu1 [3,476 B]
Del libpangocairo-1.0-0 1.36.3-1ubuntu1 [20.0 kB]
Del gnome-desktop3-data 3.8.4-0ubuntu3 [49.7 kB]
Del libgcr-3-common 3.10.1-1 [8,482 B]
Del libibus-1.0-5 1.5.5-1ubuntu3 [109 kB]
Del insserv 1.14.0-5ubuntu2 [42.7 kB]
Del libsecret-common 0.16-0ubuntu1 [4,166 B]
Del libwacom2 0.8-1 [18.1 kB]
Del libgdk-pixbuf2.0-common 2.30.7-0ubuntu1 [8,610 B]
Del libwacom-common 0.8-1 [26.5 kB]
Del fonts-freefont-ttf 20120503-4 [4,140 kB]
unick@ubuntu:~$ sudo apt-get clean
unick@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
unick@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.2.0-60-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic
  linux-headers-3.2.0-67-generic-pae linux-headers-3.5.0-54
  linux-headers-3.5.0-54-generic linux-headers-generic
  linux-headers-generic-lts-quantal linux-headers-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic
  linux-headers-3.2.0-67-generic-pae linux-headers-3.5.0-54
  linux-headers-3.5.0-54-generic
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
4 to upgrade, 5 to newly install, 0 to remove and 110 not to upgrade.
7 not fully installed or removed.
Need to get 26.7 MB of archives.
After this operation, 149 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.5.0-54 all 3.5.0-54.81~precise1 [12.1 MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.5.0-54-generic i386 3.5.0-54.81~precise1 [934 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-lts-quantal i386 3.5.0.54.59 [2,420 B]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-generic-pae i386 3.2.0.67.79 [1,730 B]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-67 all 3.2.0-67.101 [11.7 MB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-67-generic-pae i386 3.2.0-67.101 [967 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic-pae i386 3.2.0.67.79 [2,422 B]
Get:8 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-67-generic i386 3.2.0-67.101 [964 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-generic i386 3.2.0.67.79 [2,402 B]
Fetched 26.7 MB in 1min 16s (350 kB/s)                                         
(Reading database ... 1091234 files and directories currently installed.)
Unpacking linux-headers-3.5.0-54 (from .../linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.5.0-54/security/smack': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.5.0-54-generic (from .../linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.5.0-54-generic/include/config/sensors/amc6821.h.dpkg-new' (while processing `./usr/src/linux-headers-3.5.0-54-generic/include/config/sensors/amc6821.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-67 (from .../linux-headers-3.2.0-67_3.2.0-67.101_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-67_3.2.0-67.101_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-67/sound/usb/usx2y/Makefile.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-67/sound/usb/usx2y/Makefile'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-67-generic-pae (from .../linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-67-generic-pae/include/config/rtl8187.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-67-generic-pae/include/config/rtl8187.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-67-generic (from .../linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-67-generic/include/config/ncpfs/os2/ns.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-67-generic/include/config/ncpfs/os2/ns.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb
 /var/cache/apt/archives/linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-67_3.2.0-67.101_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb
 /var/cache/apt/archives/linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

```
Not sure where to go now ?  I've also tried, without success, to upgrade to 14.04 LTS.

Please keep the advice & suggestions coming.

Many thanks

Nick

---

### Post by Raggylad on 2014-08-11
> **Jonathan Precise said:**
> Is the problem. Try cleaning out some kernels from /boot.

Many thanks for the advice.  Forgive the ignorant question, but how do I go about cleaning kernels out from boot ?  Forum search has yielded nothing that looks immediately helpful.

---

### Post by ian-weisser on 2014-08-11
> **Raggylad said:**
> how do I go about cleaning kernels out from boot ?

kansasnoob and Bashing-om have been trying to help you do precisely that.
You will get nowhere until you follow their advice to make your system read-write instead of read-only, and then follow their advice to carefully verify and remove the buildup of obsolete kernels you might have.

---

### Post by Bashing-om on 2014-08-11
Raggylad; Hey;


Looking better. Please learn to use code tags, IF you spend the hours we do looking at code, you would also appreciate the formatted/scrollable output.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Now, are we dealing with a WUBI install ( within windows ) ??
> 
f -H
Filesystem Size Used Avail Use% Mounted on
[color=red]/dev/loop0[/color] 19G 13G 4.9G 73% /
udev 2.2G 4.1k 2.2G 1% /dev
tmpfs 423M 877k 422M 1% /run
none 5.3M 0 5.3M 0% /run/lock
none 2.2G 160k 2.2G 1% /run/shm
/dev/sda1 121G 60G 61G 50% [color=red]/host[/color]
/dev/sdb1 251G 159G 92G 64% /media/Expansion Drive__

At a later point this might get to be apt as there is a ceiling on WUBI.

For now, let's look at what we can do to remove those old kernels:
again as kansasnoob requested:
```

ls -la /boot

```
And for my way of looking and for confirmation of what is installed:
```

dpkg -l | grep linux-

``` and to know what kernel you are booting - MUST not remove this one -:
```

uname -r

```

And we see what we craft up to remove the kernels.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-11
> **ian-weisser said:**
> kansasnoob and Bashing-om have been trying to help you do precisely that.
You will get nowhere until you follow their advice to make your system read-write instead of read-only, and then follow their advice to carefully verify and remove the buildup of obsolete kernels you might have.

I realise that and am deeply appreciative of their help.  Be gentle with me please - I am a mechanical engineer, not a software one and it's nearly 1am here in the UK at the end of a long day !  I'm trying to follow their advice.

---

### Post by Raggylad on 2014-08-11
> **Bashing-om said:**
> Raggylad; Hey;


Looking better. Please learn to use code tags, IF you spend the hours we do looking at code, you would also appreciate the formatted/scrollable output.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Now, are we dealing with a WUBI install ( within windows ) ??

At a later point this might get to be apt as there is a ceiling on WUBI.

For now, let's look at what we can do to remove those old kernels:
again as kansasnoob requested:
```

ls -la /boot

```
And for my way of looking and for confirmation of what is installed:
```

dpkg -l | grep linux-

``` and to know what kernel you are booting - MUST not remove this one -:
```

uname -r

```

And we see what we craft up to remove the kernels.[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Hi Bashing-om,

Thanks again for all the advice.  I guess we are dealing with a WUBI install - I have windows in a very small partition and have to select Ubuntu from a windows boot menu.

Ubuntu version is 12.04.4 and uname -r yields 3.5.0-52-generic as the kernel.

**ls -la /boot **yields the following:

```
total 813508
drwxr-xr-x  3 root root    12288 Aug 11 23:11 .
drwxr-xr-x 24 root root     4096 Aug 11 23:10 ..
-rw-r--r--  1 root root   804333 May 29  2013 abi-3.2.0-45-generic-pae
-rw-r--r--  1 root root   804552 Jun  6  2013 abi-3.2.0-48-generic-pae
-rw-r--r--  1 root root   804552 Jun 18  2013 abi-3.2.0-49-generic-pae
-rw-r--r--  1 root root   804552 Jul 24  2013 abi-3.2.0-51-generic-pae
-rw-r--r--  1 root root   804552 Jul 26  2013 abi-3.2.0-52-generic-pae
-rw-r--r--  1 root root   804726 Aug 22  2013 abi-3.2.0-53-generic-pae
-rw-r--r--  1 root root   804726 Sep 10  2013 abi-3.2.0-54-generic-pae
-rw-r--r--  1 root root   804873 Oct  2  2013 abi-3.2.0-55-generic-pae
-rw-r--r--  1 root root   804873 Oct 23  2013 abi-3.2.0-56-generic-pae
-rw-r--r--  1 root root   804938 Nov 12  2013 abi-3.2.0-57-generic-pae
-rw-r--r--  1 root root   804938 Dec  3  2013 abi-3.2.0-58-generic-pae
-rw-r--r--  1 root root   804938 Jan  8  2014 abi-3.2.0-59-generic-pae
-rw-r--r--  1 root root   804930 Feb 19 05:17 abi-3.2.0-60-generic-pae
-rw-r--r--  1 root root   804930 May  2 23:34 abi-3.2.0-61-generic-pae
-rw-r--r--  1 root root   805098 May 16 01:28 abi-3.2.0-63-generic-pae
-rw-r--r--  1 root root   805098 Jun  5 00:20 abi-3.2.0-64-generic-pae
-rw-r--r--  1 root root   805098 Jun 11 22:51 abi-3.2.0-65-generic-pae
-rw-r--r--  1 root root   805150 Jul 15 20:05 abi-3.2.0-67-generic-pae
-rw-r--r--  1 root root   856743 Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r--  1 root root   860983 May 29  2013 abi-3.5.0-32-generic
-rw-r--r--  1 root root   861067 Jun  7  2013 abi-3.5.0-34-generic
-rw-r--r--  1 root root   860873 Jun 20  2013 abi-3.5.0-36-generic
-rw-r--r--  1 root root   861363 Jul 10  2013 abi-3.5.0-37-generic
-rw-r--r--  1 root root   861474 Aug 14  2013 abi-3.5.0-39-generic
-rw-r--r--  1 root root   861648 Aug 23  2013 abi-3.5.0-40-generic
-rw-r--r--  1 root root   861789 Sep 12  2013 abi-3.5.0-41-generic
-rw-r--r--  1 root root   861789 Oct  2  2013 abi-3.5.0-42-generic
-rw-r--r--  1 root root   861854 Oct 24  2013 abi-3.5.0-43-generic
-rw-r--r--  1 root root   861854 Nov 13  2013 abi-3.5.0-44-generic
-rw-r--r--  1 root root   861854 Dec  4  2013 abi-3.5.0-45-generic
-rw-r--r--  1 root root   861854 Jan 10  2014 abi-3.5.0-46-generic
-rw-r--r--  1 root root   862198 Feb 19 22:27 abi-3.5.0-47-generic
-rw-r--r--  1 root root   862250 Mar 11 20:32 abi-3.5.0-48-generic
-rw-r--r--  1 root root   862312 May  2 22:47 abi-3.5.0-49-generic
-rw-r--r--  1 root root   862320 Jun  5 02:08 abi-3.5.0-51-generic
-rw-r--r--  1 root root   862320 Jun 11 18:39 abi-3.5.0-52-generic
-rw-r--r--  1 root root   147569 May 29  2013 config-3.2.0-45-generic-pae
-rw-r--r--  1 root root   147569 Jun  6  2013 config-3.2.0-48-generic-pae
-rw-r--r--  1 root root   147569 Jun 18  2013 config-3.2.0-49-generic-pae
-rw-r--r--  1 root root   147576 Jul 24  2013 config-3.2.0-51-generic-pae
-rw-r--r--  1 root root   147576 Jul 26  2013 config-3.2.0-52-generic-pae
-rw-r--r--  1 root root   147576 Aug 22  2013 config-3.2.0-53-generic-pae
-rw-r--r--  1 root root   147576 Sep 10  2013 config-3.2.0-54-generic-pae
-rw-r--r--  1 root root   147576 Oct  2  2013 config-3.2.0-55-generic-pae
-rw-r--r--  1 root root   147576 Oct 23  2013 config-3.2.0-56-generic-pae
-rw-r--r--  1 root root   147576 Nov 12  2013 config-3.2.0-57-generic-pae
-rw-r--r--  1 root root   147576 Dec  3  2013 config-3.2.0-58-generic-pae
-rw-r--r--  1 root root   147576 Jan  8  2014 config-3.2.0-59-generic-pae
-rw-r--r--  1 root root   147559 Feb 19 05:17 config-3.2.0-60-generic-pae
-rw-r--r--  1 root root   147559 May  2 23:34 config-3.2.0-61-generic-pae
-rw-r--r--  1 root root   147587 May 16 01:28 config-3.2.0-63-generic-pae
-rw-r--r--  1 root root   147587 Jun  5 00:20 config-3.2.0-64-generic-pae
-rw-r--r--  1 root root   147587 Jun 11 22:51 config-3.2.0-65-generic-pae
-rw-r--r--  1 root root   147588 Jul 15 20:05 config-3.2.0-67-generic-pae
-rw-r--r--  1 root root   154436 Jan 25  2013 config-3.5.0-23-generic
-rw-r--r--  1 root root   154698 May 29  2013 config-3.5.0-32-generic
-rw-r--r--  1 root root   154698 Jun  7  2013 config-3.5.0-34-generic
-rw-r--r--  1 root root   154698 Jun 20  2013 config-3.5.0-36-generic
-rw-r--r--  1 root root   154713 Jul 10  2013 config-3.5.0-37-generic
-rw-r--r--  1 root root   154713 Aug 14  2013 config-3.5.0-39-generic
-rw-r--r--  1 root root   154713 Aug 23  2013 config-3.5.0-40-generic
-rw-r--r--  1 root root   154713 Sep 12  2013 config-3.5.0-41-generic
-rw-r--r--  1 root root   154713 Oct  2  2013 config-3.5.0-42-generic
-rw-r--r--  1 root root   154713 Oct 24  2013 config-3.5.0-43-generic
-rw-r--r--  1 root root   154713 Nov 13  2013 config-3.5.0-44-generic
-rw-r--r--  1 root root   154713 Dec  4  2013 config-3.5.0-45-generic
-rw-r--r--  1 root root   154713 Jan 10  2014 config-3.5.0-46-generic
-rw-r--r--  1 root root   154696 Feb 19 22:27 config-3.5.0-47-generic
-rw-r--r--  1 root root   154724 Mar 11 20:32 config-3.5.0-48-generic
-rw-r--r--  1 root root   154724 May  2 22:47 config-3.5.0-49-generic
-rw-r--r--  1 root root   154724 Jun  5 02:08 config-3.5.0-51-generic
-rw-r--r--  1 root root   154724 Jun 11 18:39 config-3.5.0-52-generic
drwxr-xr-x  3 root root    12288 Jun 26 16:17 grub
-rw-r--r--  1 root root 19818379 Jun  2  2013 initrd.img-3.2.0-45-generic-pae
-rw-r--r--  1 root root 14205164 Jun 16  2013 initrd.img-3.2.0-48-generic-pae
-rw-r--r--  1 root root 14205355 Jul  5  2013 initrd.img-3.2.0-49-generic-pae
-rw-r--r--  1 root root 14205220 Jul 29  2013 initrd.img-3.2.0-51-generic-pae
-rw-r--r--  1 root root 14207303 Aug 20  2013 initrd.img-3.2.0-52-generic-pae
-rw-r--r--  1 root root 14207469 Sep  7  2013 initrd.img-3.2.0-53-generic-pae
-rw-r--r--  1 root root 14207535 Sep 30  2013 initrd.img-3.2.0-54-generic-pae
-rw-r--r--  1 root root 14207786 Oct 23  2013 initrd.img-3.2.0-55-generic-pae
-rw-r--r--  1 root root 14207408 Nov  8  2013 initrd.img-3.2.0-56-generic-pae
-rw-r--r--  1 root root 14208385 Dec  4  2013 initrd.img-3.2.0-57-generic-pae
-rw-r--r--  1 root root 14208473 Jan  3  2014 initrd.img-3.2.0-58-generic-pae
-rw-r--r--  1 root root 14209336 Feb 19 23:12 initrd.img-3.2.0-59-generic-pae
-rw-r--r--  1 root root 14209127 Mar  7 00:19 initrd.img-3.2.0-60-generic-pae
-rw-r--r--  1 root root 14209324 May 10 00:37 initrd.img-3.2.0-61-generic-pae
-rw-r--r--  1 root root 14209552 May 26 09:54 initrd.img-3.2.0-63-generic-pae
-rw-r--r--  1 root root 14208934 Jun  7 20:56 initrd.img-3.2.0-64-generic-pae
-rw-r--r--  1 root root 14193375 Jun 26 16:16 initrd.img-3.2.0-65-generic-pae
-rw-r--r--  1 root root 15404859 Jun  2  2013 initrd.img-3.5.0-23-generic
-rw-r--r--  1 root root 15481987 Jun  2  2013 initrd.img-3.5.0-32-generic
-rw-r--r--  1 root root 15483763 Jun 16  2013 initrd.img-3.5.0-34-generic
-rw-r--r--  1 root root 15484377 Jul  5  2013 initrd.img-3.5.0-36-generic
-rw-r--r--  1 root root 15540614 Aug  2  2013 initrd.img-3.5.0-37-generic
-rw-r--r--  1 root root 15543289 Aug 28  2013 initrd.img-3.5.0-39-generic
-rw-r--r--  1 root root 15546172 Sep  7  2013 initrd.img-3.5.0-40-generic
-rw-r--r--  1 root root 15545832 Sep 30  2013 initrd.img-3.5.0-41-generic
-rw-r--r--  1 root root 15544811 Oct 26  2013 initrd.img-3.5.0-42-generic
-rw-r--r--  1 root root 15549547 Nov 21  2013 initrd.img-3.5.0-43-generic
-rw-r--r--  1 root root 15547523 Dec  4  2013 initrd.img-3.5.0-44-generic
-rw-r--r--  1 root root 15549490 Jan 25  2014 initrd.img-3.5.0-45-generic
-rw-r--r--  1 root root 15548043 Feb 19 23:13 initrd.img-3.5.0-46-generic
-rw-r--r--  1 root root 15547022 Mar 25 00:04 initrd.img-3.5.0-47-generic
-rw-r--r--  1 root root 15548047 Apr  1 22:35 initrd.img-3.5.0-48-generic
-rw-r--r--  1 root root 15549676 May 10 00:37 initrd.img-3.5.0-49-generic
-rw-r--r--  1 root root 15549895 Jun  7 21:00 initrd.img-3.5.0-51-generic
-rw-r--r--  1 root root 15531754 Jun 26 16:16 initrd.img-3.5.0-52-generic
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2319343 May 29  2013 System.map-3.2.0-45-generic-pae
-rw-------  1 root root  2320444 Jun  6  2013 System.map-3.2.0-48-generic-pae
-rw-------  1 root root  2320444 Jun 18  2013 System.map-3.2.0-49-generic-pae
-rw-------  1 root root  2320656 Jul 24  2013 System.map-3.2.0-51-generic-pae
-rw-------  1 root root  2320656 Jul 26  2013 System.map-3.2.0-52-generic-pae
-rw-------  1 root root  2321335 Aug 22  2013 System.map-3.2.0-53-generic-pae
-rw-------  1 root root  2321477 Sep 10  2013 System.map-3.2.0-54-generic-pae
-rw-------  1 root root  2321891 Oct  2  2013 System.map-3.2.0-55-generic-pae
-rw-------  1 root root  2321891 Oct 23  2013 System.map-3.2.0-56-generic-pae
-rw-------  1 root root  2321936 Nov 12  2013 System.map-3.2.0-57-generic-pae
-rw-------  1 root root  2321986 Dec  3  2013 System.map-3.2.0-58-generic-pae
-rw-------  1 root root  2322099 Jan  8  2014 System.map-3.2.0-59-generic-pae
-rw-------  1 root root  2321933 Feb 19 05:17 System.map-3.2.0-60-generic-pae
-rw-------  1 root root  2321933 May  2 23:34 System.map-3.2.0-61-generic-pae
-rw-------  1 root root  2322710 May 16 01:28 System.map-3.2.0-63-generic-pae
-rw-------  1 root root  2323570 Jun  5 00:20 System.map-3.2.0-64-generic-pae
-rw-------  1 root root  2323677 Jun 11 22:51 System.map-3.2.0-65-generic-pae
-rw-------  1 root root  2323784 Jul 15 20:05 System.map-3.2.0-67-generic-pae
-rw-------  1 root root  2421090 Jan 25  2013 System.map-3.5.0-23-generic
-rw-------  1 root root  2419134 May 29  2013 System.map-3.5.0-32-generic
-rw-------  1 root root  2419656 Jun  7  2013 System.map-3.5.0-34-generic
-rw-------  1 root root  2419775 Jun 20  2013 System.map-3.5.0-36-generic
-rw-------  1 root root  2420011 Jul 10  2013 System.map-3.5.0-37-generic
-rw-------  1 root root  2420797 Aug 14  2013 System.map-3.5.0-39-generic
-rw-------  1 root root  2421348 Aug 23  2013 System.map-3.5.0-40-generic
-rw-------  1 root root  2421572 Sep 12  2013 System.map-3.5.0-41-generic
-rw-------  1 root root  2421572 Oct  2  2013 System.map-3.5.0-42-generic
-rw-------  1 root root  2421657 Oct 24  2013 System.map-3.5.0-43-generic
-rw-------  1 root root  2421653 Nov 13  2013 System.map-3.5.0-44-generic
-rw-------  1 root root  2421684 Dec  4  2013 System.map-3.5.0-45-generic
-rw-------  1 root root  2421781 Jan 10  2014 System.map-3.5.0-46-generic
-rw-------  1 root root  2422686 Feb 19 22:27 System.map-3.5.0-47-generic
-rw-------  1 root root  2422904 Mar 11 20:32 System.map-3.5.0-48-generic
-rw-------  1 root root  2423090 May  2 22:47 System.map-3.5.0-49-generic
-rw-------  1 root root  2423270 Jun  5 02:08 System.map-3.5.0-51-generic
-rw-------  1 root root  2423270 Jun 11 18:39 System.map-3.5.0-52-generic
-rw-------  1 root root  5024224 May 29  2013 vmlinuz-3.2.0-45-generic-pae
-rw-------  1 root root  5026432 Jun  6  2013 vmlinuz-3.2.0-48-generic-pae
-rw-------  1 root root  5026432 Jun 18  2013 vmlinuz-3.2.0-49-generic-pae
-rw-------  1 root root  5028224 Jul 24  2013 vmlinuz-3.2.0-51-generic-pae
-rw-------  1 root root  5028032 Jul 26  2013 vmlinuz-3.2.0-52-generic-pae
-rw-------  1 root root  5028480 Aug 22  2013 vmlinuz-3.2.0-53-generic-pae
-rw-------  1 root root  5028896 Sep 10  2013 vmlinuz-3.2.0-54-generic-pae
-rw-------  1 root root  5030048 Oct  2  2013 vmlinuz-3.2.0-55-generic-pae
-rw-------  1 root root  5030080 Oct 23  2013 vmlinuz-3.2.0-56-generic-pae
-rw-------  1 root root  5030880 Nov 12  2013 vmlinuz-3.2.0-57-generic-pae
-rw-------  1 root root  5031904 Dec  3  2013 vmlinuz-3.2.0-58-generic-pae
-rw-------  1 root root  5033760 Jan  8  2014 vmlinuz-3.2.0-59-generic-pae
-rw-------  1 root root  5032480 Feb 19 05:17 vmlinuz-3.2.0-60-generic-pae
-rw-------  1 root root  5031904 May  2 23:34 vmlinuz-3.2.0-61-generic-pae
-rw-------  1 root root  5034176 May 16 01:28 vmlinuz-3.2.0-63-generic-pae
-rw-------  1 root root  5036352 Jun  5 00:20 vmlinuz-3.2.0-64-generic-pae
-rw-------  1 root root  5036576 Jun 11 22:51 vmlinuz-3.2.0-65-generic-pae
-rw-------  1 root root  5037728 Jul 15 20:05 vmlinuz-3.2.0-67-generic-pae
-rw-r--r--  1 root root  5237968 Feb 13  2013 vmlinuz-3.5.0-23-generic
-rw-------  1 root root  5230128 May 29  2013 vmlinuz-3.5.0-32-generic
-rw-------  1 root root  5231600 Jun  7  2013 vmlinuz-3.5.0-34-generic
-rw-------  1 root root  5233296 Jun 20  2013 vmlinuz-3.5.0-36-generic
-rw-------  1 root root  5231920 Jul 10  2013 vmlinuz-3.5.0-37-generic
-rw-------  1 root root  5233168 Aug 14  2013 vmlinuz-3.5.0-39-generic
-rw-------  1 root root  5236048 Aug 23  2013 vmlinuz-3.5.0-40-generic
-rw-------  1 root root  5236208 Sep 12  2013 vmlinuz-3.5.0-41-generic
-rw-------  1 root root  5236208 Oct  2  2013 vmlinuz-3.5.0-42-generic
-rw-------  1 root root  5236592 Oct 24  2013 vmlinuz-3.5.0-43-generic
-rw-------  1 root root  5238160 Nov 13  2013 vmlinuz-3.5.0-44-generic
-rw-------  1 root root  5237360 Dec  4  2013 vmlinuz-3.5.0-45-generic
-rw-------  1 root root  5239504 Jan 10  2014 vmlinuz-3.5.0-46-generic
-rw-------  1 root root  5238640 Feb 19 22:27 vmlinuz-3.5.0-47-generic
-rw-------  1 root root  5238704 Mar 11 20:32 vmlinuz-3.5.0-48-generic
-rw-------  1 root root  5239920 May  2 22:47 vmlinuz-3.5.0-49-generic
-rw-------  1 root root  5241296 Jun  5 02:08 vmlinuz-3.5.0-51-generic
-rw-------  1 root root  5240880 Jun 11 18:39 vmlinuz-3.5.0-52-generic

```

and **dpkg -l | grep linux-** gives this:

```
ii  linux-firmware                               1.79.16                                          Firmware for Linux kernel drivers
iU  linux-generic-lts-quantal                    3.5.0.52.57                                      Generic Linux kernel image and headers
iU  linux-generic-pae                            3.2.0.65.77                                      Complete Generic Linux kernel
ii  linux-headers-3.2.0-48                       3.2.0-48.74                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic               3.2.0-48.74                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48-generic-pae           3.2.0-48.74                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                       3.2.0-49.75                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic               3.2.0-49.75                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49-generic-pae           3.2.0-49.75                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                       3.2.0-51.77                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic               3.2.0-51.77                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51-generic-pae           3.2.0-51.77                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                       3.2.0-52.78                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic               3.2.0-52.78                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52-generic-pae           3.2.0-52.78                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                       3.2.0-53.81                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic               3.2.0-53.81                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53-generic-pae           3.2.0-53.81                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                       3.2.0-54.82                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic               3.2.0-54.82                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54-generic-pae           3.2.0-54.82                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                       3.2.0-55.85                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic               3.2.0-55.85                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55-generic-pae           3.2.0-55.85                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57                       3.2.0-57.87                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic               3.2.0-57.87                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57-generic-pae           3.2.0-57.87                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58                       3.2.0-58.88                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic               3.2.0-58.88                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58-generic-pae           3.2.0-58.88                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59                       3.2.0-59.90                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic               3.2.0-59.90                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59-generic-pae           3.2.0-59.90                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60                       3.2.0-60.91                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic               3.2.0-60.91                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60-generic-pae           3.2.0-60.91                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-61                       3.2.0-61.93                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic               3.2.0-61.93                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-61-generic-pae           3.2.0-61.93                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-63                       3.2.0-63.95                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic               3.2.0-63.95                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-63-generic-pae           3.2.0-63.95                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-64                       3.2.0-64.97                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic               3.2.0-64.97                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-64-generic-pae           3.2.0-64.97                                      Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-32                       3.5.0-32.53~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-32-generic               3.5.0-32.53~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-34                       3.5.0-34.55~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-34-generic               3.5.0-34.55~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-36                       3.5.0-36.57~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-36-generic               3.5.0-36.57~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-37                       3.5.0-37.58~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-37-generic               3.5.0-37.58~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-39                       3.5.0-39.60~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-39-generic               3.5.0-39.60~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-40                       3.5.0-40.62~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-40-generic               3.5.0-40.62~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-41                       3.5.0-41.64~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-41-generic               3.5.0-41.64~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-42                       3.5.0-42.65~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-42-generic               3.5.0-42.65~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-43                       3.5.0-43.66~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-43-generic               3.5.0-43.66~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-44                       3.5.0-44.67~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-44-generic               3.5.0-44.67~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-45                       3.5.0-45.68~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-45-generic               3.5.0-45.68~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-46                       3.5.0-46.70~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic               3.5.0-46.70~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-47                       3.5.0-47.71~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-47-generic               3.5.0-47.71~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-48                       3.5.0-48.72~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-48-generic               3.5.0-48.72~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-49                       3.5.0-49.74~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-49-generic               3.5.0-49.74~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-51                       3.5.0-51.77~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51-generic               3.5.0-51.77~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-52                       3.5.0-52.78~precise1                             Header files related to Linux kernel version 3.5.0
iU  linux-headers-generic                        3.2.0.65.77                                      Generic Linux kernel headers
iU  linux-headers-generic-lts-quantal            3.5.0.52.57                                      Generic Linux kernel headers
iU  linux-headers-generic-pae                    3.2.0.65.77                                      Generic Linux kernel headers
ii  linux-image-3.2.0-45-generic-pae             3.2.0-45.70                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic-pae             3.2.0-48.74                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic-pae             3.2.0-49.75                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic-pae             3.2.0-51.77                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic-pae             3.2.0-52.78                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae             3.2.0-53.81                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic-pae             3.2.0-54.82                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic-pae             3.2.0-55.85                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic-pae             3.2.0-56.86                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-57-generic-pae             3.2.0-57.87                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic-pae             3.2.0-58.88                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-59-generic-pae             3.2.0-59.90                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic-pae             3.2.0-60.91                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-61-generic-pae             3.2.0-61.93                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-63-generic-pae             3.2.0-63.95                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-64-generic-pae             3.2.0-64.97                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-65-generic-pae             3.2.0-65.98                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iF  linux-image-3.2.0-67-generic-pae             3.2.0-67.101                                     Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-23-generic                 3.5.0-23.35~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-32-generic                 3.5.0-32.53~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-34-generic                 3.5.0-34.55~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-36-generic                 3.5.0-36.57~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-37-generic                 3.5.0-37.58~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-39-generic                 3.5.0-39.60~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-40-generic                 3.5.0-40.62~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-41-generic                 3.5.0-41.64~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-42-generic                 3.5.0-42.65~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-43-generic                 3.5.0-43.66~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-44-generic                 3.5.0-44.67~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-45-generic                 3.5.0-45.68~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-46-generic                 3.5.0-46.70~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-47-generic                 3.5.0-47.71~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-48-generic                 3.5.0-48.72~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-49-generic                 3.5.0-49.74~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-51-generic                 3.5.0-51.77~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-52-generic                 3.5.0-52.78~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.52.57                                      Generic Linux kernel image
iU  linux-image-generic-pae                      3.2.0.67.79                                      Generic Linux kernel image
ii  linux-libc-dev                               3.2.0-65.98                                      Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu1.1                           base package for ALSA and OSS sound systems
ii  syslinux-common                              2:4.05+dfsg-2                                    collection of boot loaders (common files)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu5                             Bootloader for Linux/i386 using MS-DOS floppies
```

Hope I got the code tag thing right.

---

### Post by Bashing-om on 2014-08-11
Raggylad; Hey;

Got you covered ( I think ). With the use of the code tags - properly done by the way - we are cooking with hot oil .

Run these to remove the images and kernels: - copy and paste to preclude error/typos -
```

sudo dpkg -P linux-image-3.2.0-{48,49,51,52,53,54,55,56,57,58,59,60,61,63,64}-generic
sudo dpkg -P linux-image-3.2.0-{48,49,51,52,53,54,55,56,57,58,59,60,61,63,64}-generic-pae
sudo dpkg -P linux-headers-3.2.0-{48,49,51,52,53,54,55,57,58,59,60,61,63,64}
sudo dpkg -P linux-headers-3.2.0-{48,49,51,52,53,54,55,57,58,59,60,61,63,64}-generic
sudo dpkg -P linux-headers-3.2.0-{48,49,51,52,53,54,55,57,58,59,60,61,63,64}-generic-pae

sudo dpkg -P linux-image-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic
sudo dpkg -P linux-image-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic-pae
sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}
sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic
sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic-pae

```
Leaving a few just for whatif's ( I did keep the oldest -32 and newer -35 kernels ).

If all that runs clean, then for cleanup/checking the consistency of the package manager, and over all status; run:
- All things after the '#' comment character are just that - comments, not to be entered with the codes -
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```
When all this is completed, you are clean as a whistle !
Now you can rest easy.

EDIT: The 3.5 series of kernels means Hardware Stack is enabled, and that series is End_Of_Life, we may have more work to do yet ! run these and we will see -> maybe yes, maybe not so yes // could be that we will have to intervene and install the trusty stack, maybe.
----------------------------------
Just a heads up-> WUBI is no longer supported, and the original intent was for WUBI to be a "try me, if you like, install" . Might consider backing up your data, and making a true dual boot with Windows, and remove the virtual ubuntu. <- food for thought for another day
-------------------------------


[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-11
> **Bashing-om said:**
> Raggylad; Hey;

Got you covered ( I think ). With the use of the code tags - properly done by the way - we are cooking with hot oil .

Run these to remove the images and kernels: - copy and paste to preclude error/typos -
```

sudo dpkg -P linux-image-3.2.0-{48,49,51,52,53,54,55,56,57,58,59,60,61,63,64}-generic
sudo dpkg -P linux-image-3.2.0-{48,49,51,52,53,54,55,56,57,58,59,60,61,63,64}-generic-pae
sudo dpkg -P linux-headers-3.2.0-{48,49,51,52,53,54,55,57,58,59,60,61,63,64}
sudo dpkg -P linux-headers-3.2.0-{48,49,51,52,53,54,55,57,58,59,60,61,63,64}-generic
sudo dpkg -P linux-headers-3.2.0-{48,49,51,52,53,54,55,57,58,59,60,61,63,64}-generic-pae

sudo dpkg -P linux-image-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic
sudo dpkg -P linux-image-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic-pae
sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}
sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic
sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic-pae

```
Leaving a few just for whatif's ( I did keep the oldest -32 and newer -35 kernels ).

If all that runs clean, then for cleanup/checking the consistency of the package manager, and over all status; run:
- All things after the '#' comment character are just that - comments, not to be entered with the codes -
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```
When all this is completed, you are clean as a whistle !
Now you can rest easy.

EDIT: The 3.5 series of kernels means Hardware Stack is enabled, and that series is End_Of_Life, we may have more work to do yet ! run these and we will see -> maybe yes, maybe not so yes // could be that we will have to intervene and install the trusty stack, maybe.
----------------------------------
Just a heads up-> WUBI is no longer supported, and the original intent was for WUBI to be a "try me, if you like, install" . Might consider backing up your data, and making a true dual boot with Windows, and remove the virtual ubuntu. <- food for thought for another day
-------------------------------[INDENT][INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]
[/INDENT]

Running the code in the first code box seemed to go well, but left me with this on the command line:

```
unick@ubuntu:~$ sudo dpkg -P linux-headers-3.5.0-{23,32,34,36,37,39,40,41,42,43,44,45,4647,48,49}-generic-pae
```

Hitting [return] gave me this:

```
dpkg: warning: there's no installed package matching linux-headers-3.5.0-23-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-32-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-34-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-36-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-37-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-39-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-40-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-41-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-42-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-43-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-44-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-45-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-4647-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-48-generic-pae
dpkg: warning: there's no installed package matching linux-headers-3.5.0-49-generic-pae
```

I then ran the commands in the second code box; results:

```
unick@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unick@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ sudo apt-get clean
unick@ubuntu:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com precise Release                               
Get:2 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://linux.dropbox.com precise Release.gpg                               
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources                      
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                    
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                    
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://linux.dropbox.com precise Release                                   
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]       
Hit http://linux.dropbox.com precise/main i386 Packages                        
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:7 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:8 http://gb.archive.ubuntu.com precise-updates/universe Sources [109 kB]   
Get:9 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:10 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]  
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [1,795 B]
Get:12 http://security.ubuntu.com precise-security/main i386 Packages [443 kB] 
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,893 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:15 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:16 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:20 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:21 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:22 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:23 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources            
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources          
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,650 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Get:25 http://gb.archive.ubuntu.com precise-updates/main Translation-en [362 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,960 kB in 9s (313 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-43
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic
  linux-headers-3.2.0-67-generic-pae linux-headers-3.5.0-54
  linux-headers-3.5.0-54-generic linux-headers-generic
  linux-headers-generic-lts-quantal linux-headers-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic
  linux-headers-3.2.0-67-generic-pae linux-headers-3.5.0-54
  linux-headers-3.5.0-54-generic
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
4 to upgrade, 5 to newly install, 0 to remove and 110 not to upgrade.
7 not fully installed or removed.
Need to get 26.7 MB of archives.
After this operation, 149 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.5.0-54 all 3.5.0-54.81~precise1 [12.1 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.5.0-54-generic i386 3.5.0-54.81~precise1 [934 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-lts-quantal i386 3.5.0.54.59 [2,420 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.67.79 [1,730 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-67 all 3.2.0-67.101 [11.7 MB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-67-generic-pae i386 3.2.0-67.101 [967 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.67.79 [2,422 B]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-67-generic i386 3.2.0-67.101 [964 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic i386 3.2.0.67.79 [2,402 B]
Fetched 26.7 MB in 1min 16s (350 kB/s)                                         
(Reading database ... 611328 files and directories currently installed.)
Unpacking linux-headers-3.5.0-54 (from .../linux-headers-3.5.0-54_3.5.0-54.81~precise1_all.deb) ...
Unpacking linux-headers-3.5.0-54-generic (from .../linux-headers-3.5.0-54-generic_3.5.0-54.81~precise1_i386.deb) ...
Unpacking linux-headers-3.2.0-67 (from .../linux-headers-3.2.0-67_3.2.0-67.101_all.deb) ...
Unpacking linux-headers-3.2.0-67-generic-pae (from .../linux-headers-3.2.0-67-generic-pae_3.2.0-67.101_i386.deb) ...
Unpacking linux-headers-3.2.0-67-generic (from .../linux-headers-3.2.0-67-generic_3.2.0-67.101_i386.deb) ...
Setting up linux-image-3.2.0-67-generic-pae (3.2.0-67.101) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-67-generic-pae
Warning: No support for locale: en_GB.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found linux image: /boot/vmlinuz-3.5.0-51-generic
Found initrd image: /boot/initrd.img-3.5.0-51-generic
Found linux image: /boot/vmlinuz-3.5.0-47-generic
Found initrd image: /boot/initrd.img-3.5.0-47-generic
Found linux image: /boot/vmlinuz-3.5.0-46-generic
Found initrd image: /boot/initrd.img-3.5.0-46-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done
Setting up linux-headers-3.5.0-54 (3.5.0-54.81~precise1) ...
Setting up linux-headers-3.5.0-54-generic (3.5.0-54.81~precise1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-52-generic; however:
  Package linux-headers-3.5.0-52-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-generic-pae (3.2.0.67.79) ...
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-headers-3.2.0-67 (3.2.0-67.101) ...
Setting up linux-headers-3.2.0-67-generic-pae (3.2.0-67.101) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-67-generic-pae /boot/vmlinuz-3.2.0-67-generic-pae
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-65-generic-pae; however:
  Package linux-headers-3.2.0-65-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.65.77); however:
  Version of linux-image-generic-pae on system is 3.2.0.67.79.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.65.77); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.2.0-67-generic (3.2.0-67.101) ...
No apport report written because MaxReports has already been reached
                                                                    Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-67-generic /boot/vmlinuz-3.2.0-67-generic
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-65-generic; however:
  Package linux-headers-3.2.0-65-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
unick@ubuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-65-generic-pae; however:
  Package linux-headers-3.2.0-65-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.65.77); however:
  Version of linux-image-generic-pae on system is 3.2.0.67.79.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.65.77); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-65-generic; however:
  Package linux-headers-3.2.0-65-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-52-generic; however:
  Package linux-headers-3.5.0-52-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal

```

Which doesn't look as though its been a total success ?

Thanks again for all this help.

EDIT: I hear you on WUBI and the benefits of moving to a true dual boot. I'm being lazy having used things that way since I moved to Linux/Ubuntu in 2009.  Not too much data to backup (except Firefox bookmarks) as I save all data to an external HD.

---

### Post by Bashing-om on 2014-08-11
Raggylad; Well.

Not too shabby at all - considering that it is true:
> 
dpkg: warning: there's no installed package matching linux-headers-3.5.0-23-generic-pae
 and my notes so reflected that, I just plain forgot not to include those. No big deal as the package manager did nothing but warn us.

OK on to the dependency issue, as you are running the 3.5 kernel, let's see if the package manager will let us install the problematic headers file.
Maybe not as that series is no longer supported. but maybe still available, let's try.
```

sudo apt-get install linux-headers-3.5.0-52-generic

```
If that flies we will deal with the -32 kernel series next.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; Well.

Not too shabby at all - considering that it is true:
 and my notes so reflected that, I just plain forgot not to include those. No big deal as the package manager did nothing but warn us.

OK on to the dependency issue, as you are running the 3.5 kernel, let's see if the package manager will let us install the problematic headers file.
Maybe not as that series is no longer supported. but maybe still available, let's try.
```

sudo apt-get install linux-headers-3.5.0-52-generic

```
If that flies we will deal with the -32 kernel series next.
[INDENT][INDENT]maybe yes[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

Hi Bashing-om,

I don't think that it flew ?  Here's what I got:

```
unick@ubuntu:~$ sudo apt-get install linux-headers-3.5.0-52-generic
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Nick

---

### Post by Jonathan Precise on 2014-08-12
Try running (again):

```
sudo apt-get -f install
```

---

### Post by Bashing-om on 2014-08-12
@ Jonathan Hi !;

Good to see you once more, always my pleasure. Let's try and satisfy the dependency issue and then run the "sudo apt-get -f install" command. See then what the package manager has to relate.

To that end:
@ Raggylad; Looking good !

> 
I don't think that it flew ? 
 It did, it did fly, you do not see the Package manager hollering about that 3.5 kernel.
Let's see what we can do now about the 3.2 kernels.
Yeah - I know - I am slow, but getting there;
Let's do:
```

uname -r ## making sure you are still booting up with the 3.5 kernel
## IF so, then do the following ##
sudo apt-get purge linux-headers-3.2.0.65-generic
sudo apt-get purge linux-headers-3.2.0.65-generic-pae
sudo apt-get purge linux-image-3.2.0.65-generic-pae
sudo apt-get update
sudo apt-get upgrade

``` where the hope is that the relative " 3.2.0.65-generic " will include the specific " Depends: linux-image-generic-pae (= 3.2.0.65.77) "


And now let's check with the package manager, and see what the status is:
```

sudo apt-get -f install

```
When that last runs, and we look at it, will do an additional check, remove some more old kernels, and then I would want to do some final clean up.
I want the system stable, at this point, prior to conducting any more operations.

[INDENT]an orderly progression
[INDENT][INDENT][INDENT]point A to point E
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> @ Jonathan Hi !;

Good to see you once more, always my pleasure. Let's try and satisfy the dependency issue and then run the "sudo apt-get -f install" command. See then what the package manager has to relate.

To that end:
@ Raggylad; Looking good !

 It did, it did fly, you do not see the Package manager hollering about that 3.5 kernel.
Let's see what we can do now about the 3.2 kernels.
Yeah - I know - I am slow, but getting there;
Let's do:
```

uname -r ## making sure you are still booting up with the 3.5 kernel
## IF so, then do the following ##
sudo apt-get purge linux-headers-3.2.0.65-generic
sudo apt-get purge linux-headers-3.2.0.65-generic-pae
sudo apt-get purge linux-image-3.2.0.65-generic-pae
sudo apt-get update
sudo apt-get upgrade

``` where the hope is that the relative " 3.2.0.65-generic " will include the specific " Depends: linux-image-generic-pae (= 3.2.0.65.77) "


And now let's check with the package manager, and see what the status is:
```

sudo apt-get -f install

```
When that last runs, and we look at it, will do an additional check, remove some more old kernels, and then I would want to do some final clean up.
I want the system stable, at this point, prior to conducting any more operations.[INDENT]an orderly progression[INDENT][INDENT][INDENT]point A to point E
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om,

Here's what I got:

```

unick@ubuntu:~$ uname -r
3.5.0-52-generic
unick@ubuntu:~$ sudo apt-get purge linux-headers-3.2.0.65-generic
[sudo] password for unick: 
Sorry, try again.
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.2.0-65-generic' for regex 'linux-headers-3.2.0.65-generic'
Note, selecting 'linux-headers-3.2.0-65-generic-pae' for regex 'linux-headers-3.2.0.65-generic'
Package linux-headers-3.2.0-65-generic is not installed, so not removed
Package linux-headers-3.2.0-65-generic-pae is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get purge linux-headers-3.2.0.65-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-3.2.0-65-generic-pae' for regex 'linux-headers-3.2.0.65-generic-pae'
Package linux-headers-3.2.0-65-generic-pae is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get purge linux-image-3.2.0.65-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.2.0-65-generic-pae' for regex 'linux-image-3.2.0.65-generic-pae'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://gb.archive.ubuntu.com precise Release.gpg                           
Get:2 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Get:3 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://gb.archive.ubuntu.com precise Release                               
Get:4 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Hit http://linux.dropbox.com precise Release.gpg                               
Get:5 http://security.ubuntu.com precise-security/main Sources [108 kB]
Hit http://linux.dropbox.com precise Release                                   
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                   
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://linux.dropbox.com precise/main i386 Packages 
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:6 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]       
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [443 kB] 
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:11 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [109 kB]  
Get:13 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:14 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:15 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:16 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Get:18 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:19 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:20 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:21 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:22 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:23 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:24 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:25 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:26 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:28 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources 
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources   
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources 
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,599 kB in 9s (267 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-43
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
4 to upgrade, 0 to newly install, 0 to remove and 110 not to upgrade.
5 not fully installed or removed.
Need to get 0 B/8,974 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-52-generic; however:
  Package linux-headers-3.5.0-52-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-65-generic-pae; however:
  Package linux-headers-3.2.0-65-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because MaxReports has already been reached
                No apport report written because MaxReports has already been reached
    dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.65.77); however:
  Version of linux-image-generic-pae on system is 3.2.0.67.79.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.65.77); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-65-generic; however:
  Package linux-headers-3.2.0-65-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
unick@ubuntu:~$ 
```

Not at all worried about speed - just want to get the system working OK.  As ever, deeply appreciative of your help.

Nick

---

### Post by Bashing-om on 2014-08-12
Raggylad; Well !

Sort of disappointed. but not real surprised:
Let's try the reverse and see:
```

apt-get update && sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.5.0-40

```

Once the package manger is in a happy state, we can then remove those un-needed kernels.

[INDENT][INDENT]If at first you do not succeed
[INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; Well !

Sort of disappointed. but not real surprised:
Let's try the reverse and see:
```

apt-get update && sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.5.0-40

```

Once the package manger is in a happy state, we can then remove those un-needed kernels.
[INDENT][INDENT]If at first you do not succeed[INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

That last produced this:
```

unick@ubuntu:~$ apt-get update && sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.5.0-40
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
unick@ubuntu:~$ sudo apt-get update && sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.5.0-40
[sudo] password for unick: 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com precise Release                               
Get:2 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://linux.dropbox.com precise Release.gpg                               
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://linux.dropbox.com precise Release             
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]       
Hit http://linux.dropbox.com precise/main i386 Packages                        
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [443 kB] 
Get:11 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:18 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:20 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:21 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:22 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:23 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:24 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://gb.archive.ubuntu.com precise-backports/main Sources     
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources            
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Get:25 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [144 kB]
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,743 kB in 8s (317 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.5.0-40 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-3.2.0-65-generic : Depends: linux-headers-3.2.0-65 but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

Or russian roulette ?

Nick

---

### Post by Bashing-om on 2014-08-12
Raggylad; Sheeshj!

I was not paying good enough attention to what we are doing !

Try again:
```

sudo apt-get update
sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.2.0-65

```
See if that output is not more meaningful, and see If I can now make heads or tails out of this !
Now, I must consider this a possibly the End_Of_Life support for the hardware stacks // to be seen yet.

[INDENT][INDENT][INDENT]try try again
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; Sheeshj!

I was not paying good enough attention to what we are doing !

Try again:
```

sudo apt-get update
sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.2.0-65

```
See if that output is not more meaningful, and see If I can now make heads or tails out of this !
Now, I must consider this a possibly the End_Of_Life support for the hardware stacks // to be seen yet.
[INDENT][INDENT][INDENT]try try again
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

Here's the result:
```

unick@ubuntu:~$ sudo apt-get update
[sudo] password for unick: 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]      
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://gb.archive.ubuntu.com precise Release                               
Get:3 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]        
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://gb.archive.ubuntu.com precise-backports Release               
Get:5 http://security.ubuntu.com precise-security/main Sources [108 kB]  
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                  
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://linux.dropbox.com precise Release                                  
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Get:6 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]
Hit http://linux.dropbox.com precise/main i386 Packages                        
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [443 kB] 
Get:11 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:18 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:20 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources            
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,587 kB in 7s (326 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ sudo apt-get install linux-image-3.2.0-65-generic-pae linux-headers-3.2.0-65-generic linux-headers-3.2.0-65
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-12
Raggylad; Shucks,

I will be away from the keyboard for a bit // give me some time to consider this sloppyation.

Right now looks like
[INDENT][INDENT][INDENT]can't go forward,
[INDENT][INDENT][INDENT][INDENT]can't go back
[INDENT][INDENT][INDENT][INDENT][INDENT]we going sideways, some how
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
Bashing-om,

Whenever you're able. I'm on for about another 4 hours. Time zones !  Thanks again.

Nick

---

### Post by Bashing-om on 2014-08-12
Raggylad; OK.

Looking at the way to go sideways. what have we got installed now ?
Show us:
```

dpkg -l | grep linux-

``` shows all the kernels installed.

And as we need to get away from the 3.5 kernel that is EOL anyway, and get up on the current 3.13 kernel; let's look at where we stand on HWE:
```

hwe-support-status --verbose 

```

Maybe the best way is to jump way forward to the 'trusty' HardWare Enablement stack, sooner than later.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; OK.

Looking at the way to go sideways. what have we got installed now ?
Show us:
```

dpkg -l | grep linux-

``` shows all the kernels installed.

And as we need to get away from the 3.5 kernel that is EOL anyway, and get up on the current 3.13 kernel; let's look at where we stand on HWE:
```

hwe-support-status --verbose 

```

Maybe the best way is to jump way forward to the 'trusty' HardWare Enablement stack, sooner than later.
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]

Bashing-om,

Here's the results of the above bits of code - 2nd one not so good ?
```

unick@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                               1.79.16                                          Firmware for Linux kernel drivers
iU  linux-generic-lts-quantal                    3.5.0.52.57                                      Generic Linux kernel image and headers
iU  linux-generic-pae                            3.2.0.65.77                                      Complete Generic Linux kernel
pi  linux-headers-3.2.0-48                       3.2.0-48.74                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-49                       3.2.0-49.75                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-51                       3.2.0-51.77                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-52                       3.2.0-52.78                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-53                       3.2.0-53.81                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-54                       3.2.0-54.82                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-55                       3.2.0-55.85                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-57                       3.2.0-57.87                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-58                       3.2.0-58.88                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-59                       3.2.0-59.90                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-60                       3.2.0-60.91                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-61                       3.2.0-61.93                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-63                       3.2.0-63.95                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-64                       3.2.0-64.97                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67                       3.2.0-67.101                                     Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic               3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67-generic-pae           3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-32                       3.5.0-32.53~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-34                       3.5.0-34.55~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-36                       3.5.0-36.57~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-37                       3.5.0-37.58~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-39                       3.5.0-39.60~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-40                       3.5.0-40.62~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-41                       3.5.0-41.64~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-42                       3.5.0-42.65~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-43                       3.5.0-43.66~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-44                       3.5.0-44.67~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-45                       3.5.0-45.68~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46                       3.5.0-46.70~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic               3.5.0-46.70~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-47                       3.5.0-47.71~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-47-generic               3.5.0-47.71~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-48                       3.5.0-48.72~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-49                       3.5.0-49.74~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51                       3.5.0-51.77~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51-generic               3.5.0-51.77~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-52                       3.5.0-52.78~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54                       3.5.0-54.81~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54-generic               3.5.0-54.81~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
iU  linux-headers-generic                        3.2.0.65.77                                      Generic Linux kernel headers
iU  linux-headers-generic-lts-quantal            3.5.0.52.57                                      Generic Linux kernel headers
iU  linux-headers-generic-pae                    3.2.0.65.77                                      Generic Linux kernel headers
ii  linux-image-3.2.0-45-generic-pae             3.2.0-45.70                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-65-generic-pae             3.2.0-65.98                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-67-generic-pae             3.2.0-67.101                                     Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-46-generic                 3.5.0-46.70~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-47-generic                 3.5.0-47.71~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-51-generic                 3.5.0-51.77~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-52-generic                 3.5.0-52.78~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.52.57                                      Generic Linux kernel image
ii  linux-image-generic-pae                      3.2.0.67.79                                      Generic Linux kernel image
ii  linux-libc-dev                               3.2.0-65.98                                      Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu1.1                           base package for ALSA and OSS sound systems
ii  syslinux-common                              2:4.05+dfsg-2                                    collection of boot loaders (common files)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu5                             Bootloader for Linux/i386 using MS-DOS floppies
unick@ubuntu:~$ hwe-support-status --verbose
hwe-support-status: command not found

```

---

### Post by Bashing-om on 2014-08-12
Raggylad; Humm ??

What in the world is going on here ?
I sure am glad we looked ! In that output the first column 'pi' says the kernel is (p)urged , but some files remain (i)nstalled. I have never encountered the situation where "dpkg - P" did not remove all files related ... hummm ( again !)

Alright, attack from another direction IF we have the head room to operate in.
What now results from:
```

df -h
df -i
ls -la /lib/modules

```
And let's see if we can progress onward.

Now addressing HWE .. as it is NOT enabled, how did you install 3.5 series kernels ? Why did not the system go ahead and upgrade the kernel to 'raring' (3.11) from the 3.5 series ... hummmm ...

Before proceeding further, let's clean up behind us.

[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; Humm ??

What in the world is going on here ?
I sure am glad we looked ! In that output the first column 'pi' says the kernel is (p)urged , but some files remain (i)nstalled. I have never encountered the situation where "dpkg - P" did not remove all files related ... hummm ( again !)

Alright, attack from another direction IF we have the head room to operate in.
What now results from:
```

df -h
df -i
ls -la /lib/modules

```
And let's see if we can progress onward.

Now addressing HWE .. as it is NOT enabled, how did you install 3.5 series kernels ? Why did not the system go ahead and upgrade the kernel to 'raring' (3.11) from the 3.5 series ... hummmm ...

Before proceeding further, let's clean up behind us.
[INDENT][INDENT][INDENT]which way did he go, George
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

This is what we got:```


unick@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G  7.8G  8.5G  48% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           403M  848K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  156K  2.0G   1% /run/shm
/dev/sda1       112G   56G   57G  50% /host
/dev/sdb1       233G  149G   85G  64% /media/Expansion Drive__
unick@ubuntu:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/loop0      1136464 714304   422160   63% /
udev             208702    522   208180    1% /dev
tmpfs            212685    434   212251    1% /run
none             212685      3   212682    1% /run/lock
none             212685      7   212678    1% /run/shm
/dev/sda1      59646492  75991 59570501    1% /host
/dev/sdb1      88468884  47383 88421501    1% /media/Expansion Drive__
unick@ubuntu:~$ ls -la /lib/modules
total 104
drwxr-xr-x 26 root root 4096 Aug 12 02:14 .
drwxr-xr-x 21 root root 4096 Jan 25  2014 ..
drwxr-xr-x  4 root root 4096 Aug 11  2013 3.2.0-45-generic-pae
drwxr-xr-x  3 root root 4096 Aug 12 01:55 3.2.0-48-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:55 3.2.0-49-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-51-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-52-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-53-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-54-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-55-generic
drwxr-xr-x  3 root root 4096 Mar  7 01:08 3.2.0-56-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-57-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-58-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-59-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-60-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-61-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-63-generic
drwxr-xr-x  3 root root 4096 Aug 12 01:56 3.2.0-64-generic
drwxr-xr-x  4 root root 4096 Jun 26 16:16 3.2.0-65-generic-pae
drwxr-xr-x  3 root root 4096 Aug 12 02:16 3.2.0-67-generic
drwxr-xr-x  5 root root 4096 Aug 12 02:14 3.2.0-67-generic-pae
drwxr-xr-x  5 root root 4096 Feb 19 23:13 3.5.0-46-generic
drwxr-xr-x  5 root root 4096 Mar  7 00:19 3.5.0-47-generic
drwxr-xr-x  5 root root 4096 Jun  7 21:00 3.5.0-51-generic
drwxr-xr-x  4 root root 4096 Jun 26 16:16 3.5.0-52-generic
drwxr-xr-x  3 root root 4096 Aug 12 02:15 3.5.0-54-generic
unick@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-12
Raggylad; Hey !

We got head room !
However, all those old kernels should have been removed from "/lib/modules".
Makes we real concerned as to what is failing and where !
Let's see if the system will clean out some of the cruft for us:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```
and now a new looksee:
```

dpkg -l | grep linux-

```

And then we sic apt-get on what is left.

[INDENT][INDENT][INDENT]poke at it long enough
[INDENT][INDENT][INDENT][INDENT]something is going to give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; Hey !

We got head room !
However, all those old kernels should have been removed from "/lib/modules".
Makes we real concerned as to what is failing and where !
Let's see if the system will clean out some of the cruft for us:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```
and now a new looksee:
```

dpkg -l | grep linux-

```


And then we sic apt-get on what is left.
[INDENT][INDENT][INDENT]poke at it long enough[INDENT][INDENT][INDENT][INDENT]something is going to give
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing-om,

Here's what happened:```

unick@ubuntu:~$ sudo apt-get autoclean
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unick@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ sudo apt-get clean
unick@ubuntu:~$ dpkg -l | grep linux-
ii   linux-firmware                                1.79.16                                          Firmware for Linux  kernel drivers
iU  linux-generic-lts-quantal                     3.5.0.52.57                                      Generic Linux kernel  image and headers
iU  linux-generic-pae                            3.2.0.65.77                                      Complete Generic Linux kernel
pi   linux-headers-3.2.0-48                        3.2.0-48.74                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-49                        3.2.0-49.75                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-51                        3.2.0-51.77                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-52                        3.2.0-52.78                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-53                        3.2.0-53.81                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-54                        3.2.0-54.82                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-55                        3.2.0-55.85                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-57                        3.2.0-57.87                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-58                        3.2.0-58.88                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-59                        3.2.0-59.90                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-60                        3.2.0-60.91                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-61                        3.2.0-61.93                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-63                        3.2.0-63.95                                      Header files related to  Linux kernel version 3.2.0
pi   linux-headers-3.2.0-64                        3.2.0-64.97                                      Header files related to  Linux kernel version 3.2.0
ii   linux-headers-3.2.0-67                        3.2.0-67.101                                     Header files related to  Linux kernel version 3.2.0
ii   linux-headers-3.2.0-67-generic                3.2.0-67.101                                     Linux kernel headers  for version 3.2.0 on 32 bit x86 SMP
ii   linux-headers-3.2.0-67-generic-pae            3.2.0-67.101                                     Linux kernel headers  for version 3.2.0 on 32 bit x86 SMP
pi   linux-headers-3.5.0-32                        3.5.0-32.53~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-34                        3.5.0-34.55~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-36                        3.5.0-36.57~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-37                        3.5.0-37.58~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-39                        3.5.0-39.60~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-40                        3.5.0-40.62~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-41                        3.5.0-41.64~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-42                        3.5.0-42.65~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-43                        3.5.0-43.66~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-44                        3.5.0-44.67~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-45                        3.5.0-45.68~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-46                        3.5.0-46.70~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-46-generic                3.5.0-46.70~precise1                             Linux kernel headers  for version 3.5.0 on 32 bit x86 SMP
ii   linux-headers-3.5.0-47                        3.5.0-47.71~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-47-generic                3.5.0-47.71~precise1                             Linux kernel headers  for version 3.5.0 on 32 bit x86 SMP
pi   linux-headers-3.5.0-48                        3.5.0-48.72~precise1                             Header files related to  Linux kernel version 3.5.0
pi   linux-headers-3.5.0-49                        3.5.0-49.74~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-51                        3.5.0-51.77~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-51-generic                3.5.0-51.77~precise1                             Linux kernel headers  for version 3.5.0 on 32 bit x86 SMP
ii   linux-headers-3.5.0-52                        3.5.0-52.78~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-54                        3.5.0-54.81~precise1                             Header files related to  Linux kernel version 3.5.0
ii   linux-headers-3.5.0-54-generic                3.5.0-54.81~precise1                             Linux kernel headers  for version 3.5.0 on 32 bit x86 SMP
iU  linux-headers-generic                        3.2.0.65.77                                      Generic Linux kernel headers
iU  linux-headers-generic-lts-quantal            3.5.0.52.57                                      Generic Linux kernel headers
iU  linux-headers-generic-pae                    3.2.0.65.77                                      Generic Linux kernel headers
ii   linux-image-3.2.0-45-generic-pae              3.2.0-45.70                                      Linux kernel image for  version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-65-generic-pae              3.2.0-65.98                                      Linux kernel image for  version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.2.0-67-generic-pae              3.2.0-67.101                                     Linux kernel image for  version 3.2.0 on 32 bit x86 SMP
ii   linux-image-3.5.0-46-generic                  3.5.0-46.70~precise1                             Linux kernel image for  version 3.5.0 on 32 bit x86 SMP
ii   linux-image-3.5.0-47-generic                  3.5.0-47.71~precise1                             Linux kernel image for  version 3.5.0 on 32 bit x86 SMP
ii   linux-image-3.5.0-51-generic                  3.5.0-51.77~precise1                             Linux kernel image for  version 3.5.0 on 32 bit x86 SMP
ii   linux-image-3.5.0-52-generic                  3.5.0-52.78~precise1                             Linux kernel image for  version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.52.57                                      Generic Linux kernel image
ii  linux-image-generic-pae                      3.2.0.67.79                                      Generic Linux kernel image
ii   linux-libc-dev                                3.2.0-65.98                                      Linux Kernel Headers  for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu1.1                           base package for ALSA  and OSS sound systems
ii   syslinux-common                               2:4.05+dfsg-2                                    collection of boot  loaders (common files)
ii   syslinux-legacy                               2:3.63+dfsg-2ubuntu5                             Bootloader for  Linux/i386 using MS-DOS floppies
unick@ubuntu:~$ 

```

---

### Post by Bashing-om on 2014-08-12
Raggylad; Well;;

That was non-productive ! OK, The more I mess with this the more confused I get.

What in the world are you doing with the 3.5 kernel series on your install ??????? How did it get there ?
> 
Those running virtual or cloud images should not need these newer enablement stacks and are thus recommended to remain on the original Precise stack. To remain on the original Precise stack there are a few options:

where WUBI is a virtual install within Windows.

Do we in deed have a hybrid HWE here, or none at all .. and HWE is of no concern to us:
```

ls -al /usr/bin/hwe-support-status

```

If it comes to it .. I am prepared to go into the operating system and manually remove the old kernel files .. and then repair the package manager .. cause that action will cause all kinds of consternation to the package manager. Believe me, that is a means of last resort.

Not that it will tell us a lot but:
```

dpkg -l update-manager-core

``` to see what version is installed.

Then it is review what has been done to this time, what might be done better .. and then do something.

[INDENT][INDENT]right, wrong, or otherwise
[INDENT][INDENT][INDENT]do something, that leads to the next thing to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-12
> **Bashing-om said:**
> Raggylad; Well;;

That was non-productive ! OK, The more I mess with this the more confused I get.

What in the world are you doing with the 3.5 kernel series on your install ??????? How did it get there ?

where WUBI is a virtual install within Windows.

Do we in deed have a hybrid HWE here, or none at all .. and HWE is of no concern to us:
```

ls - al /usr/bin/hwe-support-status

```

If it comes to it .. I am prepared to go into the operating system and manually remove the old kernel files .. and then repair the package manager .. cause that action will cause all kinds of consternation to the package manager. Believe me, that is a means of last resort.

Not that it will tell us a lot but:
```

dpkg -l update-manager-core

``` to see what version is installed.

Then it is review what has been done to this time, what might be done better .. and then do something.
[INDENT][INDENT]right, wrong, or otherwise[INDENT][INDENT][INDENT]do something, that leads to the next thing to do
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

No idea how the 3.5 kernel got there. I'm a user, not a coder, so I just run Update Manager once a week and let it install what it suggests !

Results from the last two commands:
```

unick@ubuntu:~$ ls - al /usr/bin/hwe-support-status
ls: cannot access -: No such file or directory
ls: cannot access al: No such file or directory
ls: cannot access /usr/bin/hwe-support-status: No such file or directory
unick@ubuntu:~$ dpkg -l update-manager-core
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  update-manager 1:0.156.14.13  manage release upgrades
unick@ubuntu:~$ 
```

'fraid I've got to go now - it's nearly 0100 here and sleep beckons before the working day starts at 0730 !

Thanks again for all the help.

Nick

---

### Post by Jonathan Precise on 2014-08-12
Typo! It's:
```
ls **-al** /usr/bin/hwe-support-status
```

EDIT: I now see that it's now irrelevant as /usr/bin/hwe-support-status is non-existant.

---

### Post by Bashing-om on 2014-08-12
Raggylad; Hey;

I messed that one up too ( silly little space ).
The command should be:
```

ls -al /usr/bin/hwe-support-status

```
But I really do not expect that file to exist.
As HWE is not a factor, 3.5 kernel is EOL and has no support, the thing to do - as we can not revert to a 3.2 system - is to install the 3.13 kernel.
That will be a process in and of it's self and I do not see why it can not work in the WUBI as you are already up on the 3.5 kernel .
Once we are up on the 3.13 Kernel and all secure and comfy - then we can go back to getting rid of these old kernels.

Now I will be out of town ( doctors appointment ) 'till about 10:00 GMT tomorrow and that may not allow the time to finish once the process is started. Will have to play it by ear and see what works out.

[INDENT][INDENT]hope all agree
[INDENT][INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-13
Bash-om,

Good morning !  That, indeed, sounds like a plan.  I'm now in and out but will leave the machine live and logged in and check it whenever I can.

Nick

---

### Post by kansasnoob on 2014-08-13
> **Raggylad said:**
> Bash-om,

Good morning !  That, indeed, sounds like a plan.  I'm now in and out but will leave the machine live and logged in and check it whenever I can.

Nick

I think you mentioned in a much earlier post that the only thing you needed to backup from that Ubuntu install was bookmarks, is that right? If so I assume you mean Firefox bookmarks???

If so you can backup the entire Firefox profile very easily. First close Firefox - it's very important that Firefox be closed!!!! Then open Home, click on View > Show hidden files, and then you can just copy .mozilla in it's entirety to some external source.

I only mention that just in case things go south on you requiring a fresh install ;)

@Bashing-om,

I'm booted into a Precise + Saucy HWE right now trying to figure out an unrelated issue and have done a wee bit of studying - starting here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

They don't yet show a CLI process for installing the Trusty HWE (only Quantal, Raring, and Saucy) but they use "sudo apt-get install --install-recommends +proper_pkgs" so I looked at a few CLI options with the hwe-support-status tool (**[COLOR="#FF0000"]these are only examples[/COLOR]**):

```
lance@lance-desktop:~$ **[COLOR="#FF0000"]hwe-support-status --show-all-unsupported[/COLOR]**
xserver-xorg-video-modesetting-lts-saucy 
xserver-xorg-video-trident-lts-saucy 
xserver-xorg-video-cirrus-lts-saucy 
xserver-xorg-video-sisusb-lts-saucy 
xserver-xorg-video-fbdev-lts-saucy linux-image-generic-lts-saucy 
libgbm1-lts-saucy libegl1-mesa-drivers-lts-saucy 
libgl1-mesa-glx-lts-saucy xserver-xorg-input-vmmouse-lts-saucy 
xserver-xorg-video-savage-lts-saucy linux-generic-lts-saucy 
xserver-xorg-video-all-lts-saucy xserver-xorg-video-intel-lts-saucy 
xserver-xorg-lts-saucy linux-image-3.11.0-26-generic 
xserver-xorg-video-tdfx-lts-saucy xserver-xorg-video-r128-lts-saucy 
xserver-common-lts-saucy xserver-xorg-video-sis-lts-saucy 
x11-xserver-utils-lts-saucy xserver-xorg-video-radeon-lts-saucy 
linux-headers-3.11.0-15 libxatracker1-lts-saucy 
xserver-xorg-input-synaptics-lts-saucy 
xserver-xorg-video-vesa-lts-saucy 
xserver-xorg-video-siliconmotion-lts-saucy libglapi-mesa-lts-saucy 
xserver-xorg-video-neomagic-lts-saucy linux-headers-3.11.0-26-generic 
xserver-xorg-input-evdev-lts-saucy libopenvg1-mesa-lts-saucy 
xserver-xorg-video-vmware-lts-saucy xserver-xorg-video-mga-lts-saucy 
linux-headers-3.11.0-26 linux-headers-generic-lts-saucy 
libegl1-mesa-lts-saucy xserver-xorg-video-nouveau-lts-saucy 
linux-image-3.11.0-15-generic xserver-xorg-input-mouse-lts-saucy 
libgl1-mesa-dri-lts-saucy xserver-xorg-core-lts-saucy 
xserver-xorg-glamoregl-lts-saucy xserver-xorg-input-all-lts-saucy 
xserver-xorg-video-ati-lts-saucy xserver-xorg-video-s3-lts-saucy 
xserver-xorg-input-wacom-lts-saucy 
xserver-xorg-video-mach64-lts-saucy linux-headers-3.11.0-15-generic 
xserver-xorg-video-openchrome-lts-saucy 

lance@lance-desktop:~$ **[COLOR="#FF0000"]hwe-support-status --show-replacements[/COLOR]**
linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

```

So based on that info, and using -s to only simulate what would happen:

```
lance@lance-desktop:~$ **[COLOR="#FF0000"]sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty -s[/COLOR]**
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  libegl1-mesa-drivers-lts-trusty libegl1-mesa-lts-trusty libgbm1-lts-trusty
  libgl1-mesa-dri-lts-trusty libglamor-ltst0 libglapi-mesa-lts-trusty
  libllvm3.4 libopenvg1-mesa-lts-trusty libwayland-egl1-mesa-lts-trusty
  libwayland-ltst-client0 libwayland-ltst-server0 libxatracker2-lts-trusty
  libxrandr-ltst2 linux-headers-3.13.0-33 linux-headers-3.13.0-33-generic
  linux-headers-generic-lts-trusty linux-image-3.13.0-33-generic
  x11-xserver-utils-lts-trusty xserver-common-lts-trusty
  xserver-xorg-core-lts-trusty xserver-xorg-input-all-lts-trusty
  xserver-xorg-input-evdev-lts-trusty xserver-xorg-input-mouse-lts-trusty
  xserver-xorg-input-synaptics-lts-trusty
  xserver-xorg-input-vmmouse-lts-trusty xserver-xorg-input-wacom-lts-trusty
  xserver-xorg-video-all-lts-trusty xserver-xorg-video-ati-lts-trusty
  xserver-xorg-video-cirrus-lts-trusty xserver-xorg-video-fbdev-lts-trusty
  xserver-xorg-video-glamoregl-lts-trusty xserver-xorg-video-intel-lts-trusty
  xserver-xorg-video-mach64-lts-trusty xserver-xorg-video-mga-lts-trusty
  xserver-xorg-video-modesetting-lts-trusty
  xserver-xorg-video-neomagic-lts-trusty xserver-xorg-video-nouveau-lts-trusty
  xserver-xorg-video-openchrome-lts-trusty xserver-xorg-video-r128-lts-trusty
  xserver-xorg-video-radeon-lts-trusty xserver-xorg-video-s3-lts-trusty
  xserver-xorg-video-savage-lts-trusty
  xserver-xorg-video-siliconmotion-lts-trusty
  xserver-xorg-video-sis-lts-trusty xserver-xorg-video-sisusb-lts-trusty
  xserver-xorg-video-tdfx-lts-trusty xserver-xorg-video-trident-lts-trusty
  xserver-xorg-video-vesa-lts-trusty xserver-xorg-video-vmware-lts-trusty
Suggested packages:
  libglide3 fdutils linux-lts-trusty-doc-3.13.0 linux-lts-trusty-source-3.13.0
  linux-lts-trusty-tools nickle cairo-5c xfonts-100dpi xfonts-75dpi
  gpointing-device-settings touchfreeze firmware-linux
The following packages will be REMOVED:
  libegl1-mesa-drivers-lts-saucy libegl1-mesa-lts-saucy libgbm1-lts-saucy
  libgl1-mesa-dri-lts-saucy libgl1-mesa-glx-lts-saucy libglamor-ltss0
  libglapi-mesa-lts-saucy libopenvg1-mesa-lts-saucy libxatracker1-lts-saucy
  x11-xserver-utils-lts-saucy xserver-common-lts-saucy
  xserver-xorg-core-lts-saucy xserver-xorg-glamoregl-lts-saucy
  xserver-xorg-input-all-lts-saucy xserver-xorg-input-evdev-lts-saucy
  xserver-xorg-input-mouse-lts-saucy xserver-xorg-input-synaptics-lts-saucy
  xserver-xorg-input-vmmouse-lts-saucy xserver-xorg-input-wacom-lts-saucy
  xserver-xorg-lts-saucy xserver-xorg-video-all-lts-saucy
  xserver-xorg-video-ati-lts-saucy xserver-xorg-video-cirrus-lts-saucy
  xserver-xorg-video-fbdev-lts-saucy xserver-xorg-video-intel-lts-saucy
  xserver-xorg-video-mach64-lts-saucy xserver-xorg-video-mga-lts-saucy
  xserver-xorg-video-modesetting-lts-saucy
  xserver-xorg-video-neomagic-lts-saucy xserver-xorg-video-nouveau-lts-saucy
  xserver-xorg-video-openchrome-lts-saucy xserver-xorg-video-r128-lts-saucy
  xserver-xorg-video-radeon-lts-saucy xserver-xorg-video-s3-lts-saucy
  xserver-xorg-video-savage-lts-saucy
  xserver-xorg-video-siliconmotion-lts-saucy xserver-xorg-video-sis-lts-saucy
  xserver-xorg-video-sisusb-lts-saucy xserver-xorg-video-tdfx-lts-saucy
  xserver-xorg-video-trident-lts-saucy xserver-xorg-video-vesa-lts-saucy
  xserver-xorg-video-vmware-lts-saucy
The following NEW packages will be installed:
  libegl1-mesa-drivers-lts-trusty libegl1-mesa-lts-trusty libgbm1-lts-trusty
  libgl1-mesa-dri-lts-trusty libgl1-mesa-glx-lts-trusty libglamor-ltst0
  libglapi-mesa-lts-trusty libllvm3.4 libopenvg1-mesa-lts-trusty
  libwayland-egl1-mesa-lts-trusty libwayland-ltst-client0
  libwayland-ltst-server0 libxatracker2-lts-trusty libxrandr-ltst2
  linux-generic-lts-trusty linux-headers-3.13.0-33
  linux-headers-3.13.0-33-generic linux-headers-generic-lts-trusty
  linux-image-3.13.0-33-generic linux-image-generic-lts-trusty
  x11-xserver-utils-lts-trusty xserver-common-lts-trusty
  xserver-xorg-core-lts-trusty xserver-xorg-input-all-lts-trusty
  xserver-xorg-input-evdev-lts-trusty xserver-xorg-input-mouse-lts-trusty
  xserver-xorg-input-synaptics-lts-trusty
  xserver-xorg-input-vmmouse-lts-trusty xserver-xorg-input-wacom-lts-trusty
  xserver-xorg-lts-trusty xserver-xorg-video-all-lts-trusty
  xserver-xorg-video-ati-lts-trusty xserver-xorg-video-cirrus-lts-trusty
  xserver-xorg-video-fbdev-lts-trusty xserver-xorg-video-glamoregl-lts-trusty
  xserver-xorg-video-intel-lts-trusty xserver-xorg-video-mach64-lts-trusty
  xserver-xorg-video-mga-lts-trusty xserver-xorg-video-modesetting-lts-trusty
  xserver-xorg-video-neomagic-lts-trusty xserver-xorg-video-nouveau-lts-trusty
  xserver-xorg-video-openchrome-lts-trusty xserver-xorg-video-r128-lts-trusty
  xserver-xorg-video-radeon-lts-trusty xserver-xorg-video-s3-lts-trusty
  xserver-xorg-video-savage-lts-trusty
  xserver-xorg-video-siliconmotion-lts-trusty
  xserver-xorg-video-sis-lts-trusty xserver-xorg-video-sisusb-lts-trusty
  xserver-xorg-video-tdfx-lts-trusty xserver-xorg-video-trident-lts-trusty
  xserver-xorg-video-vesa-lts-trusty xserver-xorg-video-vmware-lts-trusty
0 upgraded, 53 newly installed, 42 to remove and 0 not upgraded.
Remv libegl1-mesa-drivers-lts-saucy [9.2.1-1ubuntu3~precise1]
Inst libllvm3.4 (1:3.4-1ubuntu3~precise1 Ubuntu:12.04/precise-updates [i386])
Remv xserver-xorg-video-vmware-lts-saucy [1:13.0.1-0ubuntu2~precise1] [xserver-xorg-video-all-lts-saucy:i386 ]
Remv libxatracker1-lts-saucy [9.2.1-1ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 ]
Remv xserver-xorg-video-ati-lts-saucy [1:7.2.0-0ubuntu10~precise2] [xserver-xorg-video-all-lts-saucy:i386 ]
Remv xserver-xorg-glamoregl-lts-saucy [0.5.1-0ubuntu4.2~precise2] [xserver-xorg-video-all-lts-saucy:i386 ]
Remv libegl1-mesa-lts-saucy [9.2.1-1ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 ]
Remv libgbm1-lts-saucy [9.2.1-1ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 ]
Remv libgl1-mesa-dri-lts-saucy [9.2.1-1ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-trident-lts-saucy [1:1.3.6-0ubuntu4~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-tdfx-lts-saucy [1:1.4.5-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-sisusb-lts-saucy [1:0.9.6-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-sis-lts-saucy [1:0.10.7-0ubuntu4~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-siliconmotion-lts-saucy [1:1.7.7-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-savage-lts-saucy [1:2.3.6-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-s3-lts-saucy [1:0.6.5-0ubuntu3.1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-radeon-lts-saucy [1:7.2.0-0ubuntu10~precise2] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-r128-lts-saucy [6.9.1-0ubuntu2~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-openchrome-lts-saucy [1:0.3.1-0ubuntu2.1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-nouveau-lts-saucy [1:1.0.9-2ubuntu1~precise2] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-neomagic-lts-saucy [1:1.2.7-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-modesetting-lts-saucy [0.8.0-0ubuntu1.1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-mga-lts-saucy [1:1.6.2-0ubuntu2~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-mach64-lts-saucy [6.9.3-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-intel-lts-saucy [2:2.99.904-0ubuntu2.1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-fbdev-lts-saucy [1:0.4.3-0ubuntu3~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-video-cirrus-lts-saucy [1:1.5.2-0ubuntu2~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-input-all-lts-saucy [1:7.7+1ubuntu6~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-input-wacom-lts-saucy [1:0.20.0-0ubuntu1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-input-vmmouse-lts-saucy [1:12.9.0-0ubuntu4~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-input-synaptics-lts-saucy [1.7.1-0ubuntu1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-input-mouse-lts-saucy [1:1.7.2-3build1~precise1] [xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-input-evdev-lts-saucy [1:2.7.3-0ubuntu3.1~precise1] [xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-xorg-core-lts-saucy [2:1.14.6-0ubuntu1~precise2] [xserver-xorg-video-vesa-lts-saucy:i386 xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv xserver-common-lts-saucy [2:1.14.6-0ubuntu1~precise2] [xserver-xorg-video-vesa-lts-saucy:i386 xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv x11-xserver-utils-lts-saucy [7.7+0ubuntu2~precise1] [xserver-xorg-video-vesa-lts-saucy:i386 xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv libopenvg1-mesa-lts-saucy [9.2.1-1ubuntu3~precise1] [xserver-xorg-video-vesa-lts-saucy:i386 xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv libglamor-ltss0 [0.5.1-0ubuntu4.2~precise2] [xserver-xorg-video-vesa-lts-saucy:i386 xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 ]
Remv libglapi-mesa-lts-saucy [9.2.1-1ubuntu3~precise1] [xserver-xorg-video-vesa-lts-saucy:i386 xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 libgl1-mesa-glx-lts-saucy:i386 ]
Remv xserver-xorg-video-vesa-lts-saucy [1:2.3.2-0ubuntu3~precise1] [xserver-xorg-lts-saucy:i386 xserver-xorg-video-all-lts-saucy:i386 xorg:i386 libgl1-mesa-glx-lts-saucy:i386 ]
Remv xserver-xorg-video-all-lts-saucy [1:7.7+1ubuntu6~precise1] [xserver-xorg-lts-saucy:i386 xorg:i386 libgl1-mesa-glx-lts-saucy:i386 ]
Remv xserver-xorg-lts-saucy [1:7.7+1ubuntu6~precise1] [xorg:i386 libgl1-mesa-glx-lts-saucy:i386 ]
Remv libgl1-mesa-glx-lts-saucy [9.2.1-1ubuntu3~precise1] [unity:i386 libqt4-opengl:i386 x11-utils:i386 libglew1.6:i386 libglu1-mesa:i386 libglewmx1.6:i386 libgnome-desktop-3-2:i386 compiz-plugins-default:i386 compiz-plugins-main-default:i386 gnome-session-bin:i386 libnux-2.0-0:i386 xorg:i386 nux-tools:i386 libvisual-0.4-plugins:i386 ]
Inst libglapi-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [unity:i386 libqt4-opengl:i386 x11-utils:i386 libglew1.6:i386 libglu1-mesa:i386 libglewmx1.6:i386 libgnome-desktop-3-2:i386 compiz-plugins-default:i386 compiz-plugins-main-default:i386 gnome-session-bin:i386 libnux-2.0-0:i386 xorg:i386 nux-tools:i386 libvisual-0.4-plugins:i386 ]
Inst libgl1-mesa-glx-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libglapi-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libgl1-mesa-glx-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-common-lts-trusty (2:1.15.1-0ubuntu2~precise2 Ubuntu:12.04/precise-updates [all]) [xorg:i386 ]
Inst xserver-xorg-core-lts-trusty (2:1.15.1-0ubuntu2~precise2 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libglamor-ltst0 (0.6.0-0ubuntu4~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libwayland-ltst-client0 (1.4.0-1ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libwayland-ltst-server0 (1.4.0-1ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libgbm1-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libegl1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libgl1-mesa-dri-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libllvm3.4 (1:3.4-1ubuntu3~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libgl1-mesa-dri-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libwayland-ltst-client0 (1.4.0-1ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libwayland-ltst-server0 (1.4.0-1ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libgbm1-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Conf libegl1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-glamoregl-lts-trusty (0.6.0-0ubuntu4~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-r128-lts-trusty (6.9.2-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-mach64-lts-trusty (6.9.4-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-radeon-lts-trusty (1:7.3.0-1ubuntu3.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-ati-lts-trusty (1:7.3.0-1ubuntu3.1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-cirrus-lts-trusty (1:1.5.2-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-fbdev-lts-trusty (1:0.4.4-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-intel-lts-trusty (2:2.99.910-0ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-mga-lts-trusty (1:1.6.3-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-modesetting-lts-trusty (0.8.1-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-neomagic-lts-trusty (1:1.2.8-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-nouveau-lts-trusty (1:1.0.10-1ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-openchrome-lts-trusty (1:0.3.3-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-s3-lts-trusty (1:0.6.5-0ubuntu4~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-savage-lts-trusty (1:2.3.7-2ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-siliconmotion-lts-trusty (1:1.7.7-2build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-sis-lts-trusty (1:0.10.7-0ubuntu6~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-sisusb-lts-trusty (1:0.9.6-2build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-tdfx-lts-trusty (1:1.4.5-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-trident-lts-trusty (1:1.3.6-0ubuntu5~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-vesa-lts-trusty (1:2.3.3-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-video-all-lts-trusty (1:7.7+1ubuntu8~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-input-evdev-lts-trusty (1:2.8.2-1ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-input-synaptics-lts-trusty (1.7.4-0ubuntu1~precise2 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-input-mouse-lts-trusty (1:1.9.0-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-input-vmmouse-lts-trusty (1:13.0.0-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst libxrandr-ltst2 (2:1.4.2-1~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-input-wacom-lts-trusty (1:0.23.0-0ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-input-all-lts-trusty (1:7.7+1ubuntu8~precise1 Ubuntu:12.04/precise-updates [i386]) [xorg:i386 ]
Inst xserver-xorg-lts-trusty (1:7.7+1ubuntu8~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-common-lts-trusty (2:1.15.1-0ubuntu2~precise2 Ubuntu:12.04/precise-updates [all]) []
Conf xserver-xorg-core-lts-trusty (2:1.15.1-0ubuntu2~precise2 Ubuntu:12.04/precise-updates [i386]) []
Conf libglamor-ltst0 (0.6.0-0ubuntu4~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-glamoregl-lts-trusty (0.6.0-0ubuntu4~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-r128-lts-trusty (6.9.2-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-mach64-lts-trusty (6.9.4-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-radeon-lts-trusty (1:7.3.0-1ubuntu3.1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-ati-lts-trusty (1:7.3.0-1ubuntu3.1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-cirrus-lts-trusty (1:1.5.2-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-fbdev-lts-trusty (1:0.4.4-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-intel-lts-trusty (2:2.99.910-0ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-mga-lts-trusty (1:1.6.3-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-modesetting-lts-trusty (0.8.1-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-neomagic-lts-trusty (1:1.2.8-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-nouveau-lts-trusty (1:1.0.10-1ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-openchrome-lts-trusty (1:0.3.3-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-s3-lts-trusty (1:0.6.5-0ubuntu4~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-savage-lts-trusty (1:2.3.7-2ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-siliconmotion-lts-trusty (1:1.7.7-2build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-sis-lts-trusty (1:0.10.7-0ubuntu6~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-sisusb-lts-trusty (1:0.9.6-2build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-tdfx-lts-trusty (1:1.4.5-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-trident-lts-trusty (1:1.3.6-0ubuntu5~precise1 Ubuntu:12.04/precise-updates [i386]) []
Conf xserver-xorg-video-vesa-lts-trusty (1:2.3.3-1build1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Inst xserver-xorg-video-vmware-lts-trusty (1:13.0.2-2ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386]) []
Inst libxatracker2-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf libxatracker2-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-video-vmware-lts-trusty (1:13.0.2-2ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-video-all-lts-trusty (1:7.7+1ubuntu8~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-input-evdev-lts-trusty (1:2.8.2-1ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-input-synaptics-lts-trusty (1.7.4-0ubuntu1~precise2 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-input-mouse-lts-trusty (1:1.9.0-1build1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-input-vmmouse-lts-trusty (1:13.0.0-1build1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf libxrandr-ltst2 (2:1.4.2-1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-input-wacom-lts-trusty (1:0.23.0-0ubuntu2~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-input-all-lts-trusty (1:7.7+1ubuntu8~precise1 Ubuntu:12.04/precise-updates [i386])
Conf xserver-xorg-lts-trusty (1:7.7+1ubuntu8~precise1 Ubuntu:12.04/precise-updates [i386])
Inst libopenvg1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Inst libwayland-egl1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Inst libegl1-mesa-drivers-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Inst linux-image-3.13.0-33-generic (3.13.0-33.58~precise1 Ubuntu:12.04/precise-updates [i386])
Inst linux-image-generic-lts-trusty (3.13.0.33.29 Ubuntu:12.04/precise-updates [i386])
Inst linux-headers-3.13.0-33 (3.13.0-33.58~precise1 Ubuntu:12.04/precise-updates [all])
Inst linux-headers-3.13.0-33-generic (3.13.0-33.58~precise1 Ubuntu:12.04/precise-updates [i386])
Inst linux-headers-generic-lts-trusty (3.13.0.33.29 Ubuntu:12.04/precise-updates [i386])
Inst linux-generic-lts-trusty (3.13.0.33.29 Ubuntu:12.04/precise-updates [i386])
Inst x11-xserver-utils-lts-trusty (7.7+2ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf libopenvg1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf libwayland-egl1-mesa-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf libegl1-mesa-drivers-lts-trusty (10.1.3-0ubuntu0.1~precise1 Ubuntu:12.04/precise-updates [i386])
Conf linux-image-3.13.0-33-generic (3.13.0-33.58~precise1 Ubuntu:12.04/precise-updates [i386])
Conf linux-image-generic-lts-trusty (3.13.0.33.29 Ubuntu:12.04/precise-updates [i386])
Conf linux-headers-3.13.0-33 (3.13.0-33.58~precise1 Ubuntu:12.04/precise-updates [all])
Conf linux-headers-3.13.0-33-generic (3.13.0-33.58~precise1 Ubuntu:12.04/precise-updates [i386])
Conf linux-headers-generic-lts-trusty (3.13.0.33.29 Ubuntu:12.04/precise-updates [i386])
Conf linux-generic-lts-trusty (3.13.0.33.29 Ubuntu:12.04/precise-updates [i386])
Conf x11-xserver-utils-lts-trusty (7.7+2ubuntu1~precise1 Ubuntu:12.04/precise-updates [i386])
lance@lance-desktop:~$ 

```

Not sure if that info might be helpful at all or not :redface:

I could probably run through that procedure on a Precise + Quantal HWE install in the next 24 hours if you'd like to wait but I think the same basic procedure would apply.

---

### Post by Raggylad on 2014-08-13
> **kansasnoob said:**
> I think you mentioned in a much earlier post that the only thing you needed to backup from that Ubuntu install was bookmarks, is that right? If so I assume you mean Firefox bookmarks???

If so you can backup the entire Firefox profile very easily. First close Firefox - it's very important that Firefox be closed!!!! Then open Home, click on View > Show hidden files, and then you can just copy .mozilla in it's entirety to some external source.

I only mention that just in case things go south on you requiring a fresh install ;)



Kansanoob,

Great advice, many thanks.  I've just done it.

---

### Post by kansasnoob on 2014-08-13
> **Raggylad said:**
> Kansanoob,

Great advice, many thanks.  I've just done it.

Cool, I stayed out of the way until now because I've always taken the lazy way out cleaning up old kernels by using synaptic .............. and it looked like you were having a lot of fun anyway :biggrin:

Just out of curiosity what version of Windows are you running?

I've been warning everyone I can about this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I always hate having to tell someone that they wiped out their Windows :shock:

---

### Post by Raggylad on 2014-08-13
> **kansasnoob said:**
> Cool, I stayed out of the way until now because I've always taken the lazy way out cleaning up old kernels by using synaptic .............. and it looked like you were having a lot of fun anyway :biggrin:

Just out of curiosity what version of Windows are you running?

I've been warning everyone I can about this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I always hate having to tell someone that they wiped out their Windows :shock:

The fun continues !

Windows is Vista Professional - I've only kept it as a precaution but seldom, if ever, use it.

Thanks for pointing me to the bug.  I'll be aware, but it's not a total disaster if I loose Windows.

---

### Post by kansasnoob on 2014-08-13
> **Raggylad said:**
> The fun continues !

Windows is Vista Professional - I've only kept it as a precaution but seldom, if ever, use it.

Thanks for pointing me to the bug.  I'll be aware, but it's not a total disaster if I loose Windows.

I still have one older PC dual-booting with XP that I use for some antiquated genealogy software. Someday I'll ditch it but I figure if what I have works why change it? I never open a browser in XP so the burglars shouldn't be able to steal much - in fact if they looked at my bank account they'd probably feel sorry for me and leave a donation :lol:

---

### Post by Raggylad on 2014-08-13
Yes, I never browse from Windows.  Mine is an ex-business laptop I bought specifically for Linux use - just came with Vista installed.

I have XP on an old Asus Eee - used to run car (auto ?) ignition tuning software which is XP based - dual booted with a lite (Lubuntu) version of Ubuntu.

---

### Post by Bashing-om on 2014-08-13
@ kansasnoob; sure glad you popped in and lending a hand.

Messing about and in WUBI is a totally new experience with me, not certain of what to expect in that virtual world.

@ Raggylad; Making progress, huh !

Show us the updated status/condition:
```

lsb_release -a
uname -a
dpkg  -l | grep linux-

```
so we see what there is to do.

[INDENT][INDENT]proceeding merrily along the way
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-13
> **Bashing-om said:**
> @ kansasnoob; sure glad you popped in and lending a hand.

Messing about and in WUBI is a totally new experience with me, not certain of what to expect in that virtual world.

@ Raggylad; Making progress, huh !

Show us the updated status/condition:
```

lsb_release -a
uname -a
dpkg  -l | grep linux-

```
so we see what there is to do.
[INDENT][INDENT]proceeding merrily along the way
[/INDENT]
[/INDENT]

Bashing-om,

Here's what occurred:

```
unick@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
unick@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-52-generic #78~precise1-Ubuntu SMP Wed Jun 11 17:17:30 UTC 2014 i686 i686 i386 GNU/Linux
unick@ubuntu:~$ dpkg  -l | grep linux-
ii  linux-firmware                               1.79.16                                          Firmware for Linux kernel drivers
iU  linux-generic-lts-quantal                    3.5.0.52.57                                      Generic Linux kernel image and headers
iU  linux-generic-pae                            3.2.0.65.77                                      Complete Generic Linux kernel
pi  linux-headers-3.2.0-48                       3.2.0-48.74                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-49                       3.2.0-49.75                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-51                       3.2.0-51.77                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-52                       3.2.0-52.78                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-53                       3.2.0-53.81                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-54                       3.2.0-54.82                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-55                       3.2.0-55.85                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-57                       3.2.0-57.87                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-58                       3.2.0-58.88                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-59                       3.2.0-59.90                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-60                       3.2.0-60.91                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-61                       3.2.0-61.93                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-63                       3.2.0-63.95                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-64                       3.2.0-64.97                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67                       3.2.0-67.101                                     Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic               3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67-generic-pae           3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-32                       3.5.0-32.53~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-34                       3.5.0-34.55~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-36                       3.5.0-36.57~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-37                       3.5.0-37.58~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-39                       3.5.0-39.60~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-40                       3.5.0-40.62~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-41                       3.5.0-41.64~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-42                       3.5.0-42.65~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-43                       3.5.0-43.66~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-44                       3.5.0-44.67~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-45                       3.5.0-45.68~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46                       3.5.0-46.70~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic               3.5.0-46.70~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-47                       3.5.0-47.71~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-47-generic               3.5.0-47.71~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-48                       3.5.0-48.72~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-49                       3.5.0-49.74~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51                       3.5.0-51.77~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51-generic               3.5.0-51.77~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-52                       3.5.0-52.78~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54                       3.5.0-54.81~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54-generic               3.5.0-54.81~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
iU  linux-headers-generic                        3.2.0.65.77                                      Generic Linux kernel headers
iU  linux-headers-generic-lts-quantal            3.5.0.52.57                                      Generic Linux kernel headers
iU  linux-headers-generic-pae                    3.2.0.65.77                                      Generic Linux kernel headers
ii  linux-image-3.2.0-45-generic-pae             3.2.0-45.70                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-65-generic-pae             3.2.0-65.98                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-67-generic-pae             3.2.0-67.101                                     Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-46-generic                 3.5.0-46.70~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-47-generic                 3.5.0-47.71~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-51-generic                 3.5.0-51.77~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-52-generic                 3.5.0-52.78~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.52.57                                      Generic Linux kernel image
ii  linux-image-generic-pae                      3.2.0.67.79                                      Generic Linux kernel image
ii  linux-libc-dev                               3.2.0-65.98                                      Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu1.1                           base package for ALSA and OSS sound systems
ii  syslinux-common                              2:4.05+dfsg-2                                    collection of boot loaders (common files)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu5                             Bootloader for Linux/i386 using MS-DOS floppies
unick@ubuntu:~$ 


```

---

### Post by Bashing-om on 2014-08-13
Raggylad; Welp;

Nothing has changed ! // I recon you used the '-s' switch to "simulate" what would happen if the packages were upgraded to 'trusty'.
I trust you did not observe anything disconcerting, and -> 
kansasnoob's method has great merit and I do, I do prefer that over what I had in mind ( wget the files from packages.com and "dpkg -i" them to get onto the 'trusty' kernel). But the package manager is not at 100% ; so I do have some small amount of reservations.... but we do know it will work well enough for installs. I am all for:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

```
As that not only gets you the kernel, but also a compatible xserver to go along with the new kernel and also updated graphics drivers. Doing all of this within ubuntu's package management system controls - I like that !

Reboot for the new 'trusty' kernel to take effect, and let's see what kernel you have in the grub boot menu, and what kernel you boot up !

When up on the 'trusty' kernel, we go back to :
a) removing all those old kernels - one way or another;
b) repairing the package manager if removing those kernels does not resolve the issue.

[INDENT][INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-13
> **Bashing-om said:**
> Raggylad; Welp;

Nothing has changed ! // I recon you used the '-s' switch to "simulate" what would happen if the packages were upgraded to 'trusty'.
I trust you did not observe anything disconcerting, and -> 
kansasnoob's method has great merit and I do, I do prefer that over what I had in mind ( wget the files from packages.com and "dpkg -i" them to get onto the 'trusty' kernel). But the package manager is not at 100% ; so I do have some small amount of reservations.... but we do know it will work well enough for installs. I am all for:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

```
As that not only gets you the kernel, but also a compatible xserver to go along with the new kernel and also updated graphics drivers. Doing all of this within ubuntu's package management system controls - I like that !

Reboot for the new 'trusty' kernel to take effect, and let's see what kernel you have in the grub boot menu, and what kernel you boot up !

When up on the 'trusty' kernel, we go back to :
a) removing all those old kernels - one way or another;
b) repairing the package manager if removing those kernels does not resolve the issue.
[INDENT][INDENT][INDENT]where there are solutions[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

Taking it line by line, the first command gives me this:
```
unick@ubuntu:~$ sudo apt-get update
[sudo] password for unick: 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com precise Release                               
Get:2 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://linux.dropbox.com precise Release             
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]       
Hit http://linux.dropbox.com precise/main i386 Packages                        
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [443 kB] 
Get:11 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://linux.dropbox.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:18 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:20 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources            
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,587 kB in 8s (321 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ 
```

Second line next .....

---

### Post by Raggylad on 2014-08-13
> **Raggylad said:**
> Bashing-om,

Taking it line by line, the first command gives me this:
```
unick@ubuntu:~$ sudo apt-get update
[sudo] password for unick: 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com precise Release                               
Get:2 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://linux.dropbox.com precise Release             
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]       
Hit http://linux.dropbox.com precise/main i386 Packages                        
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [443 kB] 
Get:11 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [855 kB]
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://linux.dropbox.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:18 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:20 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources            
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,587 kB in 8s (321 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ 
```

Second line next .....

```
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ 
```

Now for the third line and reboot.

---

### Post by Raggylad on 2014-08-13
> **Raggylad said:**
> ```
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ 
```

Now for the third line and reboot.

Results of third line:```

unick@ubuntu:~$ sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libgl1-mesa-glx-lts-quantal : Recommends: libtxc-dxtn-s2tc0 but it is not going to be installed
                               Conflicts: libgl1
                               Conflicts: libgl1-mesa-glx
 libgl1-mesa-glx-lts-trusty : Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but it is not going to be installed
                              Recommends: libgl1-mesa-dri-lts-trusty (>= 7.2) but it is not going to be installed
                              Conflicts: libgl1
                              Conflicts: libgl1-mesa-glx
                              Conflicts: xorg-renamed-package-lts-quantal
 linux-generic-lts-trusty : Depends: linux-headers-generic-lts-trusty but it is not going to be installed
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
 linux-image-generic-lts-trusty : Depends: linux-image-3.13.0-33-generic but it is not going to be installed
 xserver-xorg-lts-quantal : Conflicts: xserver-xorg
 xserver-xorg-lts-trusty : Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but it is not going to be installed
                           Depends: xserver-xorg-input-evdev-lts-trusty but it is not going to be installed
                           Recommends: libgl1-mesa-dri-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-input-all-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-video-all-lts-trusty but it is not going to be installed
                           Recommends: x11-xserver-utils-lts-trusty but it is not going to be installed
                           Conflicts: xorg-renamed-package-lts-quantal
                           Conflicts: xserver-xorg
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

Not good ?  Will go for reboot anyway.

---

### Post by Raggylad on 2014-08-13
Bashing-om,

I'm back after reboot.  FWIW, after selecting Ubuntu from the Windows Boot Manager screen, Grub (?) showed me as still using a 3.5 kernel.

---

### Post by Bashing-om on 2014-08-13
Raggylad; Well sheesshh !

OK, looks like for sure we have to fix the kernel issue before we can do anything other.

So back up to where we were, get a clean look at things -> "TRY" and use the package manager to remove the old kernels, then it is back to doing it the hard manual way. - then go back and fix the PM, yuk -

awaiting to see ya back up from the reboot.


[INDENT][INDENT]what I think !
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-13
> **Raggylad said:**
> Bashing-om,

I'm back after reboot.  FWIW, after selecting Ubuntu from the Windows Boot Manager screen, Grub (?) showed me as still using a 3.5 kernel.

I'm back !

---

### Post by Raggylad on 2014-08-13
Bashing-om,

'Fraid I've got to knock it on the head for tonight.  Continue tomorrow, I hope ?

---

### Post by Bashing-om on 2014-08-13
Raggylad; Yeah !

In for a penny, in for a pound ! We are this far into it and have put forth a lot of effort;
You best believe you are stuck with me 'till death do us part OR we come up with a solution.

Let's take a poke at it like so:
```

sudo apt-get --purge remove linux-headers-3.5.0-32

```
short term; - I would really prefer a solution -

see what happens. or additional info we can garner.

[INDENT][INDENT][INDENT]look'n for that better way
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-14
> **Bashing-om said:**
> Raggylad; Yeah !

In for a penny, in for a pound ! We are this far into it and have put forth a lot of effort;
You best believe you are stuck with me 'till death do us part OR we come up with a solution.

Let's take a poke at it like so:
```

sudo apt-get --purge remove linux-headers-3.5.0-32

```
short term; - I would really prefer a solution -

see what happens. or additional info we can garner.
[INDENT][INDENT][INDENT]look'n for that better way
[/INDENT]
[/INDENT]
[/INDENT]


Good Morning Bashing-om,

Here's the result:
```

unick@ubuntu:~$ sudo apt-get --purge remove linux-headers-3.5.0-32
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

Or perhaps we are looking for something 'safer than the known way'?

---

### Post by Jonathan Precise on 2014-08-14
What it seems is that apt-get isn't going to turn any other result unless apt-get -f install is run:

```
**E: Unmet dependencies. Try 'apt-get -f install' with no packages** (or specify a solution).
```

So unless one wants to run apt-get -f install, apt-get does not seem like a solution.

---

### Post by kansasnoob on 2014-08-14
There have been indications all along that when the system ran out of free space some packages failed to upgrade and/or install properly so I'd jump in with:

```
sudo apt-get dist-upgrade --fix-missing
```

```
sudo apt-get dist-upgrade --fix-broken
```

Then also:

```
sudo apt-get -f install
```

I am of course assuming that we now have sufficient free space.

---

### Post by Bashing-om on 2014-08-14
@ Raggylad; Morning !

Here we go again. yeah that last from me is disappointing .
Let's take kansasnoob's / Jonathon's  direction, and give it a whirl .. won't hurt to try .. I say again manually doing the removals is the last thing I want to do .. though I know It can be done, the recovery might prove to be equally painful. I much prefer to remain within the realm of the package manager.

Let's do the kansasnoob thing from the last post - we know we now have that needed headroom.

[INDENT][INDENT]anything worth doing
[INDENT][INDENT][INDENT][INDENT]is worth doing right
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-14
I'm back here ! Just working through Kansanoob's commands and will report back with results shortly.

---

### Post by Raggylad on 2014-08-14
> **Bashing-om said:**
> @ Raggylad; Morning !

Here we go again. yeah that last from me is disappointing .
Let's take kansasnoob's / Jonathon's  direction, and give it a whirl .. won't hurt to try .. I say again manually doing the removals is the last thing I want to do .. though I know It can be done, the recovery might prove to be equally painful. I much prefer to remain within the realm of the package manager.

Let's do the kansasnoob thing from the last post - we know we now have that needed headroom.
[INDENT][INDENT]anything worth doing[INDENT][INDENT][INDENT][INDENT]is worth doing right
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

Here's the last part of what we got (the stuff before it has gone ?!):
```

.17_i386.deb) ...
Unpacking replacement openssl ...
Preparing to replace parted 2.3-8ubuntu5.1 (using .../parted_2.3-8ubuntu5.2_i386.deb) ...
Unpacking replacement parted ...
Preparing to replace wget 1.13.4-2ubuntu1 (using .../wget_1.13.4-2ubuntu1.1_i386.deb) ...
Unpacking replacement wget ...
Preparing to replace acpi-support 0.140.1 (using .../acpi-support_0.140.2_i386.deb) ...
Unpacking replacement acpi-support ...
Preparing to replace compiz-gnome 1:0.9.7.12-0ubuntu3 (using .../compiz-gnome_1%3a0.9.7.12-0ubuntu4_i386.deb) ...
Unpacking replacement compiz-gnome ...
Preparing to replace compiz-plugins-default 1:0.9.7.12-0ubuntu3 (using .../compiz-plugins-default_1%3a0.9.7.12-0ubuntu4_i386.deb) ...
Unpacking replacement compiz-plugins-default ...
Preparing to replace libdecoration0 1:0.9.7.12-0ubuntu3 (using .../libdecoration0_1%3a0.9.7.12-0ubuntu4_i386.deb) ...
Unpacking replacement libdecoration0 ...
Preparing to replace compiz-core 1:0.9.7.12-0ubuntu3 (using .../compiz-core_1%3a0.9.7.12-0ubuntu4_i386.deb) ...
Unpacking replacement compiz-core ...
Preparing to replace compiz 1:0.9.7.12-0ubuntu3 (using .../compiz_1%3a0.9.7.12-0ubuntu4_all.deb) ...
Unpacking replacement compiz ...
Preparing to replace dbus-x11 1.4.18-1ubuntu1.4 (using .../dbus-x11_1.4.18-1ubuntu1.5_i386.deb) ...
Unpacking replacement dbus-x11 ...
Preparing to replace firefox 30.0+build1-0ubuntu0.12.04.3 (using .../firefox_31.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 30.0+build1-0ubuntu0.12.04.3 (using .../firefox-globalmenu_31.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 30.0+build1-0ubuntu0.12.04.3 (using .../firefox-locale-en_31.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace flashplugin-installer 11.2.202.378ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.400ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace grub-pc 1.99-21ubuntu3.14 (using .../grub-pc_1.99-21ubuntu3.16_i386.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-pc-bin 1.99-21ubuntu3.14 (using .../grub-pc-bin_1.99-21ubuntu3.16_i386.deb) ...
Unpacking replacement grub-pc-bin ...
Preparing to replace grub2-common 1.99-21ubuntu3.14 (using .../grub2-common_1.99-21ubuntu3.16_i386.deb) ...
Unpacking replacement grub2-common ...
Preparing to replace grub-common 1.99-21ubuntu3.14 (using .../grub-common_1.99-21ubuntu3.16_i386.deb) ...
Unpacking replacement grub-common ...
Preparing to replace libgpgme11 1.2.0-1.4ubuntu2 (using .../libgpgme11_1.2.0-1.4ubuntu2.1_i386.deb) ...
Unpacking replacement libgpgme11 ...
Preparing to replace liblightdm-gobject-1-0 1.2.3-0ubuntu2.4 (using .../liblightdm-gobject-1-0_1.2.3-0ubuntu2.5_i386.deb) ...
Unpacking replacement liblightdm-gobject-1-0 ...
Preparing to replace libminiupnpc8 1.6-3ubuntu1 (using .../libminiupnpc8_1.6-3ubuntu1.1_i386.deb) ...
Unpacking replacement libminiupnpc8 ...
Preparing to replace libreoffice-emailmerge 1:3.5.7-0ubuntu5 (using .../libreoffice-emailmerge_1%3a3.5.7-0ubuntu6.1_all.deb) ...
Unpacking replacement libreoffice-emailmerge ...
Preparing to replace libreoffice-l10n-en-gb 1:3.5.7-0ubuntu5 (using .../libreoffice-l10n-en-gb_1%3a3.5.7-0ubuntu6.1_all.deb) ...
Unpacking replacement libreoffice-l10n-en-gb ...
Preparing to replace libreoffice-help-en-gb 1:3.5.7-0ubuntu5 (using .../libreoffice-help-en-gb_1%3a3.5.7-0ubuntu6.1_all.deb) ...
Unpacking replacement libreoffice-help-en-gb ...
Preparing to replace libreoffice-help-en-us 1:3.5.7-0ubuntu5 (using .../libreoffice-help-en-us_1%3a3.5.7-0ubuntu6.1_all.deb) ...
Unpacking replacement libreoffice-help-en-us ...
Preparing to replace linux-headers-3.5.0-52 3.5.0-52.78~precise1 (using .../linux-headers-3.5.0-52_3.5.0-52.79~precise1_all.deb) ...
Unpacking replacement linux-headers-3.5.0-52 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.10 (using .../smbclient_2%3a3.6.3-2ubuntu2.11_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.10 (using .../samba-common_2%3a3.6.3-2ubuntu2.11_all.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-common-bin 2:3.6.3-2ubuntu2.10 (using .../samba-common-bin_2%3a3.6.3-2ubuntu2.11_i386.deb) ...
Unpacking replacement samba-common-bin ...
Preparing to replace thunderbird-locale-en 1:24.6.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a31.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 1:24.6.0+build1-0ubuntu0.12.04.1 (using .../thunderbird_1%3a31.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 1:24.6.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-gnome-support_1%3a31.0+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Preparing to replace thunderbird-locale-en-gb 1:24.6.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-gb_1%3a31.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-gb ...
Preparing to replace thunderbird-locale-en-us 1:24.6.0+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a31.0+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace transmission-common 2.51-0ubuntu1.3 (using .../transmission-common_2.51-0ubuntu1.4_all.deb) ...
Unpacking replacement transmission-common ...
Preparing to replace transmission-gtk 2.51-0ubuntu1.3 (using .../transmission-gtk_2.51-0ubuntu1.4_i386.deb) ...
Unpacking replacement transmission-gtk ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up linux-image-3.5.0-54-generic (3.5.0-54.81~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-54-generic
Warning: No support for locale: en_GB.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-54-generic /boot/vmlinuz-3.5.0-54-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found linux image: /boot/vmlinuz-3.5.0-51-generic
Found initrd image: /boot/initrd.img-3.5.0-51-generic
Found linux image: /boot/vmlinuz-3.5.0-47-generic
Found initrd image: /boot/initrd.img-3.5.0-47-generic
Found linux image: /boot/vmlinuz-3.5.0-46-generic
Found initrd image: /boot/initrd.img-3.5.0-46-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done
Setting up linux-image-generic-lts-quantal (3.5.0.54.59) ...
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-52-generic; however:
  Package linux-headers-3.5.0-52-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-65-generic-pae; however:
  Package linux-headers-3.2.0-65-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.65.77); however:
  Version of linux-image-generic-pae on system is 3.2.0.67.79.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.65.77); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-65-generic; however:
  Package linux-headers-3.2.0-65-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libc-dev-bin (2.15-0ubuntu10.6) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Setting up linux-libc-dev (3.2.0-67.101) ...
Setting up libc6-dev (2.15-0ubuntu10.6) ...
Setting up libdbus-1-3 (1.4.18-1ubuntu1.5) ...
Setting up libdrm2 (2.4.52-1~precise1) ...
Setting up libdrm-intel1 (2.4.52-1~precise1) ...
Setting up libdrm-nouveau1a (2.4.52-1~precise1) ...
Setting up libdrm-radeon1 (2.4.52-1~precise1) ...
Setting up apparmor (2.7.102-0ubuntu3.10) ...
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libkrb5support0 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libk5crypto3 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libkrb5-3 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libgssapi-krb5-2 (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up libparted0debian1 (2.3-8ubuntu5.2) ...
Setting up libtasn1-3 (2.10-1ubuntu1.2) ...
Setting up libcups2 (1.5.3-0ubuntu8.4) ...
Setting up libcupsmime1 (1.5.3-0ubuntu8.4) ...
Setting up libcupscgi1 (1.5.3-0ubuntu8.4) ...
Setting up libcupsimage2 (1.5.3-0ubuntu8.4) ...
Setting up libcupsppdc1 (1.5.3-0ubuntu8.4) ...
Setting up cups-common (1.5.3-0ubuntu8.4) ...
Setting up cups-client (1.5.3-0ubuntu8.4) ...
Setting up cups-bsd (1.5.3-0ubuntu8.4) ...
Setting up cups-ppdc (1.5.3-0ubuntu8.4) ...
Setting up cups (1.5.3-0ubuntu8.4) ...
cups start/running, process 27783
Updating PPD files for cups ...
Setting up libavutil51 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libpostproc52 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libswscale2 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libavcodec53 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libavformat53 (4:0.8.15-0ubuntu0.12.04.1) ...
Setting up libcupsdriver1 (1.5.3-0ubuntu8.4) ...
Setting up libdrm-nouveau2 (2.4.52-1~precise1) ...
Setting up libjpeg-turbo8 (1.1.90+svn733-0ubuntu4.4) ...
Setting up libnspr4 (4.9.5-0ubuntu0.12.04.3) ...
Setting up libnspr4-0d (4.9.5-0ubuntu0.12.04.3) ...
Setting up fonts-opensymbol (2:102.2+LibO3.5.7-0ubuntu6.1) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.11) ...
Setting up dbus (1.4.18-1ubuntu1.5) ...
Setting up lightdm (1.2.3-0ubuntu2.5) ...
Setting up linux-image-3.2.0-65-generic-pae (3.2.0-65.99) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-65.98 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-65.98 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
Error! Your kernel headers for kernel 3.2.0-65-generic-pae cannot be found.
Please install the linux-headers-3.2.0-65-generic-pae package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-65-generic-pae
Warning: No support for locale: en_GB.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-65-generic-pae /boot/vmlinuz-3.2.0-65-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found linux image: /boot/vmlinuz-3.5.0-51-generic
Found initrd image: /boot/initrd.img-3.5.0-51-generic
Found linux image: /boot/vmlinuz-3.5.0-47-generic
Found initrd image: /boot/initrd.img-3.5.0-47-generic
Found linux image: /boot/vmlinuz-3.5.0-46-generic
Found initrd image: /boot/initrd.img-3.5.0-46-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done
Setting up linux-image-3.5.0-52-generic (3.5.0-52.79~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.5.0-52.78~precise1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.5.0-52.78~precise1 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.5.0-52-generic /boot/vmlinuz-3.5.0-52-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.5.0-52-generic /boot/vmlinuz-3.5.0-52-generic
Error! Your kernel headers for kernel 3.5.0-52-generic cannot be found.
Please install the linux-headers-3.5.0-52-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-52-generic /boot/vmlinuz-3.5.0-52-generic
update-initramfs: Generating /boot/initrd.img-3.5.0-52-generic
Warning: No support for locale: en_GB.utf8
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.5.0-52-generic /boot/vmlinuz-3.5.0-52-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.5.0-52-generic /boot/vmlinuz-3.5.0-52-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.5.0-52-generic /boot/vmlinuz-3.5.0-52-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found linux image: /boot/vmlinuz-3.5.0-51-generic
Found initrd image: /boot/initrd.img-3.5.0-51-generic
Found linux image: /boot/vmlinuz-3.5.0-47-generic
Found initrd image: /boot/initrd.img-3.5.0-47-generic
Found linux image: /boot/vmlinuz-3.5.0-46-generic
Found initrd image: /boot/initrd.img-3.5.0-46-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done
Setting up update-manager-core (1:0.156.14.17) ...
Setting up update-manager (1:0.156.14.17) ...
Setting up update-notifier-common (0.119ubuntu8.7) ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.400.orig.tar.gz
Installing from local file /tmp/tmpIwHo8F.gz
Flash Plugin installed.
Setting up update-notifier (0.119ubuntu8.7) ...
Setting up libsmbclient (2:3.6.3-2ubuntu2.11) ...
Setting up libmagic1 (5.09-2ubuntu0.4) ...
Setting up file (5.09-2ubuntu0.4) ...
Setting up dmidecode (2.11-4ubuntu0.1) ...
Setting up krb5-locales (1.10+dfsg~beta1-2ubuntu0.5) ...
Setting up openssl (1.0.1-4ubuntu5.17) ...
Setting up parted (2.3-8ubuntu5.2) ...
Setting up wget (1.13.4-2ubuntu1.1) ...
Setting up acpi-support (0.140.2) ...
Installing new version of config file /etc/acpi/power.sh ...
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Setting up libdecoration0 (1:0.9.7.12-0ubuntu4) ...
Setting up compiz-core (1:0.9.7.12-0ubuntu4) ...
Setting up compiz-plugins-default (1:0.9.7.12-0ubuntu4) ...
Setting up compiz-gnome (1:0.9.7.12-0ubuntu4) ...
Setting up compiz (1:0.9.7.12-0ubuntu4) ...
Setting up dbus-x11 (1.4.18-1ubuntu1.5) ...
Setting up firefox (31.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (31.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (31.0+build1-0ubuntu0.12.04.1) ...
Setting up flashplugin-installer (11.2.202.400ubuntu0.12.04.1) ...
Setting up grub-common (1.99-21ubuntu3.16) ...
Setting up grub2-common (1.99-21ubuntu3.16) ...
Setting up grub-pc-bin (1.99-21ubuntu3.16) ...
Setting up grub-pc (1.99-21ubuntu3.16) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found linux image: /boot/vmlinuz-3.5.0-51-generic
Found initrd image: /boot/initrd.img-3.5.0-51-generic
Found linux image: /boot/vmlinuz-3.5.0-47-generic
Found initrd image: /boot/initrd.img-3.5.0-47-generic
Found linux image: /boot/vmlinuz-3.5.0-46-generic
Found initrd image: /boot/initrd.img-3.5.0-46-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done
Setting up libgpgme11 (1.2.0-1.4ubuntu2.1) ...
Setting up liblightdm-gobject-1-0 (1.2.3-0ubuntu2.5) ...
Setting up libminiupnpc8 (1.6-3ubuntu1.1) ...
Setting up libreoffice-l10n-en-gb (1:3.5.7-0ubuntu6.1) ...
Setting up linux-headers-3.5.0-52 (3.5.0-52.79~precise1) ...
Setting up samba-common (2:3.6.3-2ubuntu2.11) ...
Setting up smbclient (2:3.6.3-2ubuntu2.11) ...
Setting up samba-common-bin (2:3.6.3-2ubuntu2.11) ...
Setting up thunderbird (1:31.0+build1-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-locale-en (1:31.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-gnome-support (1:31.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-gb (1:31.0+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:31.0+build1-0ubuntu0.12.04.1) ...
Setting up transmission-common (2.51-0ubuntu1.4) ...
Setting up transmission-gtk (2.51-0ubuntu1.4) ...
Setting up libreoffice-style-human (1:3.5.7-0ubuntu6.1) ...
Setting up ure (3.5.7-0ubuntu6.1) ...
Setting up uno-libs3 (3.5.7-0ubuntu6.1) ...
Setting up libreoffice-style-tango (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-common (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-core (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-base-core (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-writer (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-calc (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-draw (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-impress (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-gtk (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-gnome (1:3.5.7-0ubuntu6.1) ...
Setting up python-uno (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-math (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-help-en-gb (1:3.5.7-0ubuntu6.1) ...
Setting up libreoffice-help-en-us (1:3.5.7-0ubuntu6.1) ...
Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.7-0ubuntu6.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
unick@ubuntu:~$ sudo apt-get -f install
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-43
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
4 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
5 not fully installed or removed.
Need to get 0 B/8,974 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-52-generic; however:
  Package linux-headers-3.5.0-52-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-65-generic-pae; however:
  Package linux-headers-3.2.0-65-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.65.77); however:
  Version of linux-image-generic-pae on system is 3.2.0.67.79.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.65.77); however:
  Package linux-headers-generic-pae is not configured yet.No apport report written because MaxReports has already been reached
                                              No apport report written because MaxReports has already been reached

dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-65-generic; however:
  Package linux-headers-3.2.0-65-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
unick@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-14
Raggylad: K;

Awaiting with baited breath.

fingers crossed. no hope to die

---

### Post by kansasnoob on 2014-08-14
I see we've not gained anything:

```
Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

To be honest I wonder if it's worth the time to try and recover this old Wubi install???

What's everyone else thinking?

---

### Post by Raggylad on 2014-08-15
I've downloaded and made a copy of 14.04.  If you guys' expert advice is that we are chasing will(s ?) o' the wisp and that the law of diminishing returns applies, then I will remove 12.04 from my system and do a fresh install of 14.04.

I've really appreciated all the help and advice given so far - I hope that the challenge has been enjoyable for you.

Nick

---

### Post by kansasnoob on 2014-08-15
Well, one of my major concerns is the long term viability of Wubi itself:

[http://askubuntu.com/questions/449486/windows-installer-for-ubuntu-14-04-lts-onwards](http://askubuntu.com/questions/449486/windows-installer-for-ubuntu-14-04-lts-onwards)

But if you want to keep trying we'll keep trying :)

Based on that last chunk of output we need to fix:

```
linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
```

And probably purge:

```
linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
```

Then clean up (purge) all kernels except 3.5.0-54.

Then finally upgrade to the Trusty HWE:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Is it worth that much work? Or should we go for a fresh install?

---

### Post by Raggylad on 2014-08-15
I'm thinking fresh install but I'd like to hear Bashing-om's view ?

If I do go for a fresh install, the question for me is whether or not to hang on to Windows or go for the totally Linux option ..... just need to see if I can create a Vista recovery disk.

---

### Post by Bashing-om on 2014-08-15
et al :

My 2 pounds worth,
All we have here is the package manager requiring a bit of help to sort this out and I am all for continuing to sort this out; if for no other reason than the learning experience.
Now that said, even if we get the 'trusty' kernel installed, this operating system is over and done with in April of 2017, so yes there is a bit of life left to operate in the manner that Nick is accustomed to .. BUT a true dual boot would get you out from under Window's thumb - in the event that something happens to the Window's install, will give you lots more elbow room for ubuntu operations, will be much easier to trouble shoot IF/When ubuntu does experience a hiccup , security is much better as a separate install, and better file management can be obtained between the two systems.

IF we can fix this WUBI install, there is no hurry about implementing the true dual boot.

I do, I do enjoy a good puzzle and look forward to any occasion that I learn from; and this is for sure "one" of those .

But, Nick, it boils down to this, what do you want to do ?
It is your time, your effort, and your system but -again -> Wubi's trial period should have long passed, and ready for a true dual boot for ubuntu.

If you pound long enough
[INDENT][INDENT][INDENT]something is gonna give
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-15
Bashing-om, Kansasnoob,

I'm happy to press on as we were for a bit, if B-O is happy to continue.  From the point of view of my use of the system, it's still usable (if a little buggy round the edges at times) and I know that I've got the fresh install option available if need be.  I've got about another week before work circumstances are going to make evenings on the laptop difficult, so can continue for that long - if we haven't cracked it well before then.

I'm glad you are enjoying the puzzle - I'm learning too, though at a much more basic level.

WRT the wubi issue (and this will expose my only basic level of understanding !); when I installed 12.04, I opted for 'Install Ubuntu alongside Windows' (as I have for every version of Ubuntu since I first started in 2009, gradually reducing the size of the Windows partition with each Ubuntu upgrade).  On boot up this gives me the 'Windows Boot Manager' screen on which I have the option of two OS - Vista or Ubuntu; selecting Ubuntu takes me into Grub.

Is this a Wubi or a dual boot setup ?  If the latter, then I apologise for confusing the issue.

Nick

---

### Post by Bashing-om on 2014-08-15
Raggylad; Hello, Yeah, I like

Let's get this question of WUBI behind us once and for all:

From your outputs: 
```

sudo parted -l
sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 120GB 120GB primary [color=red]ntfs[/color] boot


Model: Seagate Portable (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 250GB 250GB primary [color=red]ntfs[/color] boot
df -H
Filesystem Size Used Avail Use% Mounted on
[color=red]/dev/loop0[/color] 19G 13G 4.9G 73% /
udev 2.2G 4.1k 2.2G 1% /dev
tmpfs 423M 877k 422M 1% /run
none 5.3M 0 5.3M 0% /run/lock
none 2.2G 160k 2.2G 1% /run/shm
/dev/sda1 121G 60G 61G 50%[color=red] /host[/color]
/dev/sdb1 251G 159G 92G 64% /media/Expansion Drive__

```
Which shows a single ntfs partition on the 1st hard drive (sda);
and shows a single ntfs partition  on the 2ndhard drive (sdb);
Where ntfs = Windows:
Nowhere do we see "ext4", which is the default partition for 'buntu.
additionally we have "[color=red]/dev/loop0[/color] && /dev/sda1 121G 60G 61G 50%[color=red] /host[/color]
Which is certainly indicative that ubuntu is installed within that 1st hard drive that is a Windows partition (ntfs). The only way that could happen- so far as I am aware -  is if we do have ubuntu installed as WUBI.

compare to my output, where I am quadruple booting 'buntus

--------------------------
```

sysop@1404mini:~$ sudo parted -l
[sudo] password for sysop: 
Model: ATA WDC WD5000ABYS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  5244MB  5243MB  primary   ext4            boot
 2      5245MB  15.7GB  10.5GB  primary   ext4
 3      17.5GB  500GB   483GB   extended
 8      17.5GB  22.8GB  5243MB  logical   ext4
 5      227GB   227GB   8193kB  logical   linux-swap(v1)
 6      227GB   306GB   78.6GB  logical   ext4
 7      306GB   500GB   194GB   logical   ext4


Model: ATA WDC WD5000ABYS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext4


Model: ATA WDC WD5000ABYS-0 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  52.4GB  52.4GB  primary  ext4
 2      52.4GB  105GB   52.4GB  primary  ext4         boot

sysop@1404mini:~$

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  2.6G  1.9G  58% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  736K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   21M  2.0G   2% /run/shm
none            100M  4.0K  100M   1% /run/user
/dev/sda2       9.5G  1.3G  7.8G  14% /home
/dev/sda8       4.7G  1.5G  3.0G  34% /var
sysop@1404mini:~$


sysop@1404mini:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             

```
---------------------------------------------
Let's see your output for 'fdisk' .
```

sudo fdisk -lu

```

And then we go back to trying to satisfy the kernel dependency issue. Find out what component is missing and either add it back in, or remove the other components and "fix" the package manager.

This ain't no needle in a hay stack, just have not looked in the right place from the correct perspective - to this time.

[INDENT][INDENT][INDENT]our inquiring minds
[INDENT][INDENT][INDENT][INDENT]we want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-16
Hi Bashing-om,

Here's the output:

```
unick@ubuntu:~$ sudo fdisk -lu
[sudo] password for unick: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234439599   117218776    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c9b80f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392127   244196032+   7  HPFS/NTFS/exFAT
unick@ubuntu:~$
```

---

### Post by kansasnoob on 2014-08-16
I knew it was Wubi just from this way back when we started:

> df -H
Filesystem Size Used Avail Use% Mounted on
/dev/loop0 19G 13G 4.9G 73% /
udev 2.2G 4.1k 2.2G 1% /dev
tmpfs 423M 877k 422M 1% /run
none 5.3M 0 5.3M 0% /run/lock
none 2.2G 160k 2.2G 1% /run/shm
**/dev/sda1 121G 60G 61G 50% /[COLOR="#FF0000"]host[/COLOR]**
/dev/sdb1 251G 159G 92G 64% /media/Expansion Drive__

If you do ever reach a point where you decide to get rid of the Wubi install and perform an actual dual-boot you need to be acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

To put it in a nut shell; if or when you reach that point shout at someone that really knows how to dual-boot! At this point the automated *replace* and *alongside* options just can't be trusted so you'll need some guidance. You can just send me a PM if you wish.

---

### Post by Raggylad on 2014-08-16
> **kansasnoob said:**
> 


If you do ever reach a point where you decide to get rid of the Wubi install and perform an actual dual-boot you need to be acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

To put it in a nut shell; if or when you reach that point shout at someone that really knows how to dual-boot! At this point the automated *replace* and *alongside* options just can't be trusted so you'll need some guidance. You can just send me a PM if you wish.

Thank you, that's a very kind offer.  We'll see where we go over the next few days, after which I may well be in touch.

---

### Post by Raggylad on 2014-08-16
> **kansasnoob said:**
> 

If you do ever reach a point where you decide to get rid of the Wubi install and perform an actual dual-boot you need to be acutely aware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

To put it in a nut shell; if or when you reach that point shout at someone that really knows how to dual-boot! At this point the automated *replace* and *alongside* options just can't be trusted so you'll need some guidance. You can just send me a PM if you wish.

Thank you, that's a very kind offer.  We'll see where we go over the next few days - I may well be in touch after that.

---

### Post by Bashing-om on 2014-08-16
Raggylad; Guys;

Going back to work on this "missing component". we have the advisory :
> 
Please install the linux-headers-3.2.0-65-generic-pae package,
-AND-
Error! Your kernel headers for kernel 3.5.0-52-generic cannot be found.
Please install the linux-headers-3.5.0-52-generic package
-AND-
Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
-AND-
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
-same same ? -
 Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

------------------------
and we are full circle back to kansasnoob's pot #67.
> 
Based on that last chunk of output we need to fix:

Code:
linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
-----------------
And probably purge:

Code:
linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
Then clean up (purge) all kernels except 3.5.0-54.

=====================
Now for the specifics to see:
Do the installs of: and maybe quit beating around the bush of the -52 and -65 headers files.
```

sudo apt-get install linux-headers-generic-lts-quantal
sudo apt-get install linux-generic-lts-quantal
sudo apt-get install linux-headers-generic-pae
sudo apt-get install linux-generic-pae
sudo apt-get install linux-headers-generic

sudo apt-get install linux-headers-3.5.0-52-generic
sudo apt-get install linux-headers-3.2.0-65-generic-pae

```
A shotgun approach in an attempt to make the package manager happy, Then once the package manager is happy we can remove all these unwanted-unneeded components; safely !

Again, in this instance, I do prefer to let the package manager handle the situation - if at all possible. Let's see if I am putting the chicken before the egg here in attempting to install specific headers files afterward.

[INDENT][INDENT][INDENT]poke at it 'til we know
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-16
Results for first line:
```

unick@ubuntu:~$ sudo apt-get install linux-headers-generic-lts-quantal
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-16
Second line:

```
unick@ubuntu:~$ sudo apt-get install linux-generic-lts-quantal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-16
Third line:

```
unick@ubuntu:~$ sudo apt-get install linux-headers-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-16
Fourth line:

```
unick@ubuntu:~$ sudo apt-get install linux-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.67.79) but 3.2.0.65.77 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 

```

---

### Post by Raggylad on 2014-08-16
Fifth line:

```
unick@ubuntu:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-16
Sixth line:

```
unick@ubuntu:~$ sudo apt-get install linux-headers-3.5.0-52-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-16
Last line:

```
unick@ubuntu:~$ sudo apt-get install linux-headers-3.2.0-65-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-3.2.0-65-generic-pae : Depends: linux-headers-3.2.0-65 but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-16
Raggylad; Shucks ;

Disappointed once more, but no less shocked.
Another exercise in futility, as it yells (tells) us nothing that we did not already know.

Round robin, can not go forward, (install); can not go back (purge/remove). So we gonna find a way to go sideways.

Looks as this situation is caused by the inclusion of the 'quantal' kernel in the 'precise' install and HWE was not and is not incorporated.

@ kansasnoob, as a thought, IF we were to boot with the precise kernel, would the results of installing/removing the 'quantal' kernels be any different ?

Another thought - as the steam fogs up my glasses - how about we clear the cache directories and delete the package list, then see what we can install/remove ?

Maybe troll through "/var/lib/dpkg/status" ( about 30 stanzas, yikes - what a chore ), see if we can see why the package manager is not being cooperative.

OR now just bite the bullet, pull the rug out from under the package manager and do this manually, and with the kernels, images, headers removed - manually - and then fix the package manager ?????????


[INDENT][INDENT]Are we out of patience yet ?[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-16
> **Bashing-om said:**
> 
[INDENT][INDENT]Are we out of patience yet ?[/INDENT]
[/INDENT]


Bashing-om,

You are grinding the organ here - I'm just the monkey pressing the keys.  My aim is to have a working system - that is the 'essential'; the 'highly desirable' is to fix what I've got currently.  I'm happy to go on pressing the keys for a few more days in pursuit of the latter, if you have the inclination, patience and time to do the expert work.

At whatever stage we decide to call it a day, I know that I have the viable option of doing a fresh install (taking Kansasnoob's advice on how to achieve a successful true dual boot) of 14.04.1 - so there's always that Plan Z to use while we work through A to Y.

Nick

(EDIT: BTW, I have no backup PC where I am at the moment - so if something catastrophic happens to this one I'll be communicating by smartphone which will slow things down a bit)

---

### Post by ian-weisser on 2014-08-16
What about?
```

sudo apt-get clean              (already done above, I know)
sudo apt-get update            (be sure the cache is updated)
sudo apt-get install --reinstall linux-headers-generic    (fresh download and reinstall starting at the bottom of the dependency chain)
```

---

### Post by Bashing-om on 2014-08-16
ian-weisser; Hi ! 

Appreciate your wise council . I have yet another thought too.

How do you feel about using "update-initramfs -d -k <kernel_version> see if that will remove these problematic kernels ?? And, still keep the package manager in a happy state.

[INDENT][INDENT][INDENT]still in that 
[INDENT][INDENT][INDENT][INDENT]process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-08-16
> **Bashing-om said:**
> update-initramfs -d -k <kernel_version>

Have not tried it. I suspect it will delete an initramfs file...thereby causing a problem later when the kernel removal hook doesn't find the file.
Perhaps worth a try if space were still the issue, but looks like space is no longer the problem.

---

### Post by Bashing-om on 2014-08-16
> **ian-weisser said:**
> Have not tried it. I suspect it will delete an initramfs file...thereby causing a problem later when the kernel removal hook doesn't find the file.
Perhaps worth a try if space were still the issue, but looks like space is no longer the problem.

@ Ian .. OK,. Thanks, it was a thought, best to keep things simple.

@ Raggylad; Hey,

While we await kansasnoob to arrive on the scene once more, let's by all means follow Ian's lead here and do  as per his advisement.  
Can not hurt, and may indeed be the answer !

[INDENT][INDENT]cheap price to pay
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-16
Results from Ian's first two commands:
```

unick@ubuntu:~$ sudo apt-get clean
unick@ubuntu:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com precise Release.gpg
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://gb.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security Release                      
Hit http://gb.archive.ubuntu.com precise-updates Release                       
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://gb.archive.ubuntu.com precise/restricted Sources          
Hit http://gb.archive.ubuntu.com precise/universe Sources            
Hit http://gb.archive.ubuntu.com precise/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://linux.dropbox.com precise Release.gpg                     
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/main Sources        
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources    
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/main Sources      
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources  
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://linux.dropbox.com precise Release   
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB      
Hit http://gb.archive.ubuntu.com precise/main Translation-en         
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://linux.dropbox.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://linux.dropbox.com precise/main TranslationIndex
Ign http://linux.dropbox.com precise/main Translation-en_GB
Ign http://linux.dropbox.com precise/main Translation-en
Reading package lists... Done
unick@ubuntu:~$ 
```

Third to follow in a bit.

Last bit:

```

unick@ubuntu:~$ sudo apt-get install --reinstall linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$  
```

---

### Post by Bashing-om on 2014-08-16
Raggylad; Yeah, yeah !

OK just to cover the base:
```

sudo dpkg --purge linux-image-3.2.0.67-generic-pae

``` and maybe then we can deal with the -65 kernel (??) .

Still think'n we are going to have to wade into the "/var/lib/dpkg/status " file !

still athin'n

---

### Post by kansasnoob on 2014-08-16
I'd like to see the output of these two commands:

```
sudo apt-get purge --ignore-missing linux-image-3.2.0-67-generic-pae linux-image-3.2.0-65-generic-pae linux-image-3.2.0-45-generic-pae -s
```

Don't try it without the -s suffix though until we've evaluated that output.

Go ahead and also include the output of:

```
uname -r
```

Just playing it safe ;)

---

### Post by Raggylad on 2014-08-17
> **Bashing-om said:**
> Raggylad; Yeah, yeah !

OK just to cover the base:
```

sudo dpkg --purge linux-image-3.2.0.67-generic-pae

``` and maybe then we can deal with the -65 kernel (??) .

Still think'n we are going to have to wade into the "/var/lib/dpkg/status " file !

still athin'n

Here's the result:

```
unick@ubuntu:~$ sudo dpkg --purge linux-image-3.2.0.67-generic-pae
[sudo] password for unick: 
dpkg: warning: there's no installed package matching linux-image-3.2.0.67-generic-pae
unick@ubuntu:~$
```

---

### Post by Raggylad on 2014-08-17
> **kansasnoob said:**
> I'd like to see the output of these two commands:

```
sudo apt-get purge --ignore-missing linux-image-3.2.0-67-generic-pae linux-image-3.2.0-65-generic-pae linux-image-3.2.0-45-generic-pae -s
```

Don't try it without the -s suffix though until we've evaluated that output.

Go ahead and also include the output of:

```
uname -r
```

Just playing it safe ;)

And the results of those two commands:
```

unick@ubuntu:~$ sudo apt-get purge --ignore-missing linux-image-3.2.0-67-generic-pae linux-image-3.2.0-65-generic-pae linux-image-3.2.0-45-generic-pae -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-67-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ uname -r
3.5.0-54-generic
unick@ubuntu:~$ 
```

---

### Post by kansasnoob on 2014-08-17
Clear back in [post #63]("http://ubuntuforums.org/showthread.php?t=2238992&page=7&p=13098584#post13098584") some of the terminal output was truncated so we're going to try some commands again and print the output to .txt files in your Home folder:

```
sudo apt-get update
```

Unless you've changed something in regards to your software sources we don't care about that output but we always want to start by updating the software cache.

```
sudo apt-get -m dist-upgrade > dist_up.txt
```

```
sudo apt-get -f install > f_in.txt
```

Then you'll find those files in Home and you can copy the full text and paste it here.

---

### Post by Raggylad on 2014-08-17
> **kansasnoob said:**
> Clear back in [post #63]("http://ubuntuforums.org/showthread.php?t=2238992&page=7&p=13098584#post13098584") some of the terminal output was truncated so we're going to try some commands again and print the output to .txt files in your Home folder:

```
sudo apt-get update
```

Unless you've changed something in regards to your software sources we don't care about that output but we always want to start by updating the software cache.

```
sudo apt-get -m dist-upgrade > dist_up.txt
```

```
sudo apt-get -f install > f_in.txt
```

Then you'll find those files in Home and you can copy the full text and paste it here.

Here's the text outputs:

Reading package lists...
Building dependency tree...
Reading state information...
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-43
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
4 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
5 not fully installed or removed.
Need to get 8,974 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by Bashing-om on 2014-08-17
Raggylad; Well !

That do look promising !


Hit 'y' and let's see !

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-17
That may have been what the text says, however, this is what terminal says:

```
unick@ubuntu:~$ sudo apt-get -f install > f_in.txt

No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        No apport report written because the error message indicates it's a follow-up error from a previous failure.
    No apport report written because MaxReports has already been reached
                                                                        No apport report written because MaxReports has already been reached
                                                            E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2014-08-17
Raggylad; Well,

Let's see what was written to the text file.

```

cat  f_in.txt

```
???
[OR, post that as a 'file' back here ]

[INDENT][INDENT]is this the definition of a 'may' pole 
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-17
> **Bashing-om said:**
> Raggylad; Well,

Let's see what was written to the text file.

```

cat  f_in.txt

```
???
[OR, post that as a 'file' back here ]
[INDENT][INDENT]is this the definition of a 'may' pole 
[/INDENT]
[/INDENT]


This is what terminal says to that:

```
unick@ubuntu:~$ cat  f_in.txt
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.5.0-43
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
The following packages will be upgraded:
  linux-generic-pae linux-headers-generic linux-headers-generic-lts-quantal
  linux-headers-generic-pae
4 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
5 not fully installed or removed.
Need to get 0 B/8,974 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? dpkg: dependency problems prevent configuration of linux-headers-generic-lts-quantal:
 linux-headers-generic-lts-quantal depends on linux-headers-3.5.0-52-generic; however:
  Package linux-headers-3.5.0-52-generic is not installed.
dpkg: error processing linux-headers-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-headers-generic-lts-quantal; however:
  Package linux-headers-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-65-generic-pae; however:
  Package linux-headers-3.2.0-65-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.65.77); however:
  Version of linux-image-generic-pae on system is 3.2.0.67.79.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.65.77); however:
  Package linux-headers-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-65-generic; however:
  Package linux-headers-3.2.0-65-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic-lts-quantal
 linux-generic-lts-quantal
 linux-headers-generic-pae
 linux-generic-pae
 linux-headers-generic
unick@ubuntu:~$ 
```

File also attached:

[ATTACH]255564[/ATTACH]

---

### Post by Bashing-om on 2014-08-17
Raggylad; Sheesshh !

round and around we go. I think it is time we gave the package manager a helping hand and a bit of direction.

Maybe this is the source and we need to look at it ?
Fire up a text editor to " /var/lib/dpkg/status"
search on the term: "Package: linux-headers-generic-lts-quantal" - note there is a space before 'linux' -
And post back that stanza for examination.

As a place to start looking.

[INDENT][INDENT][INDENT]I think, I think
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-18
Bashing-om,

Good morning:

Here's what I got to that last:

Package: linux-headers-generic-lts-quantal
Status: install ok unpacked
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.52.57
Config-Version: 3.5.0.51.56
Depends: linux-headers-3.5.0-52-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers
 available.

---

### Post by Bashing-om on 2014-08-18
Raggylad; UMphh ...

Do I not like what I see:
> 
Status: install ok [color=red]unpacked[/color]
##which means it is not installed##
Section: [color=red]devel[/color]
Source: linux-meta-lts-quantal
Version: 3.5.0.52.57
Config-Version: [color=red]3.5.0.51.56[/color]
Depends: linux-headers-[color=red]3.5.0-52-generic[/color]
##should not all the versions be the same ?##

This package will always depend on the latest generic 12.10 kernel headers
available.
##Then why is not the latest kernel installed, and in use ?##
Note " Section: devel " why not  "kernel" as the section location ? -- What have we done here ??


------------------------------
For reference, a similar output from my system; booting the 3.13.0.34.40 kernel:
```


Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 3.13.0.34.40
Depends: linux-headers-3.13.0-34-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers
 available.

```


Then what to do what to do !

Let's get a new listing of the kernels;
```

dpkg -l | grep linux-

```
Just for consideration of IF and HOW we are going to edit this stanza, and maybe others too !- And believe me, I may be getting into a learning situation here also (?). We already know this was a deep issue, now looking like it is even deeper !

And also; is there a stanza for "Source: linux-meta-lts-quantal" ?
See what you can find in the status file for the heading : Package: linux-meta-lts-quantal .

[INDENT][INDENT][INDENT]are we having fun now ??
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-18
> **Bashing-om said:**
> 
Let's get a new listing of the kernels;
```

dpkg -l | grep linux-

```

Here's the kernel list:

```
unick@ubuntu:~$ dpkg -l | grep linux-
ii  linux-firmware                               1.79.16                                          Firmware for Linux kernel drivers
iU  linux-generic-lts-quantal                    3.5.0.52.57                                      Generic Linux kernel image and headers
iU  linux-generic-pae                            3.2.0.65.77                                      Complete Generic Linux kernel
pi  linux-headers-3.2.0-48                       3.2.0-48.74                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-49                       3.2.0-49.75                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-51                       3.2.0-51.77                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-52                       3.2.0-52.78                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-53                       3.2.0-53.81                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-54                       3.2.0-54.82                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-55                       3.2.0-55.85                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-57                       3.2.0-57.87                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-58                       3.2.0-58.88                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-59                       3.2.0-59.90                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-60                       3.2.0-60.91                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-61                       3.2.0-61.93                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-63                       3.2.0-63.95                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-64                       3.2.0-64.97                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67                       3.2.0-67.101                                     Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic               3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67-generic-pae           3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-32                       3.5.0-32.53~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-34                       3.5.0-34.55~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-36                       3.5.0-36.57~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-37                       3.5.0-37.58~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-39                       3.5.0-39.60~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-40                       3.5.0-40.62~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-41                       3.5.0-41.64~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-42                       3.5.0-42.65~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-43                       3.5.0-43.66~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-44                       3.5.0-44.67~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-45                       3.5.0-45.68~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46                       3.5.0-46.70~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic               3.5.0-46.70~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-47                       3.5.0-47.71~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-47-generic               3.5.0-47.71~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-48                       3.5.0-48.72~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-49                       3.5.0-49.74~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51                       3.5.0-51.77~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51-generic               3.5.0-51.77~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-52                       3.5.0-52.79~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54                       3.5.0-54.81~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54-generic               3.5.0-54.81~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
iU  linux-headers-generic                        3.2.0.65.77                                      Generic Linux kernel headers
iU  linux-headers-generic-lts-quantal            3.5.0.52.57                                      Generic Linux kernel headers
iU  linux-headers-generic-pae                    3.2.0.65.77                                      Generic Linux kernel headers
ii  linux-image-3.2.0-45-generic-pae             3.2.0-45.70                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-65-generic-pae             3.2.0-65.99                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-67-generic-pae             3.2.0-67.101                                     Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-46-generic                 3.5.0-46.70~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-47-generic                 3.5.0-47.71~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-51-generic                 3.5.0-51.77~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-52-generic                 3.5.0-52.79~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-54-generic                 3.5.0-54.81~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.54.59                                      Generic Linux kernel image
ii  linux-image-generic-pae                      3.2.0.67.79                                      Generic Linux kernel image
ii  linux-libc-dev                               3.2.0-67.101                                     Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu1.1                           base package for ALSA and OSS sound systems
ii  syslinux-common                              2:4.05+dfsg-2                                    collection of boot loaders (common files)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu5                             Bootloader for Linux/i386 using MS-DOS floppies
unick@ubuntu:~$
```

---

### Post by Raggylad on 2014-08-18
> **Bashing-om said:**
> 
And also; is there a stanza for "Source: linux-meta-lts-quantal" ?


Package: linux-image-generic-lts-quantal
Status: install ok installed
Priority: optional
Section: metapackages
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
**Source: linux-meta-lts-quantal**
Version: 3.5.0.54.59
Depends: linux-image-3.5.0-54-generic, linux-firmware
Description: Generic Linux kernel image
 This package will always depend on the latest generic 12.10 kernel image
 available.

---

### Post by Raggylad on 2014-08-18
Bashing-om

> **Bashing-om said:**
> 
See what you can find in the status file for the heading : Package: linux-meta-lts-quantal .
[INDENT][INDENT][INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Nothing shows up searching the status file for that.

> are we having fun now ?? 

I think so !

---

### Post by Bashing-om on 2014-08-18
Raggylad; Think'n

As:
> 
This package will always depend on the latest generic 12.10 kernel image
available.

And we have for the 'latest'"
> 
ii  linux-headers-3.5.0-54


So now, is 3.5.0-54 a member of the 12.10 release family ??// - here lately HWE has really messed with my mind as to what/how kernels are related to the distribution in question.



I have not talked myself out of editing the status file; looking more and more like the thing to do.
I think we should make the versions in the stanza "Package: linux-headers-generic-lts-quantal" match with " Package: linux-image-generic-lts-quantal".

Let's ponder on this and see if we can come up with a reason NOT TO do this edit.

An edit; ->
[INDENT][INDENT][INDENT]sure looks reasonable to me
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-18
Bashing-om,

I'm still with you - I think

---

### Post by Bashing-om on 2014-08-18
et al ; It is !

@ Raggylad;
> 
Linux kernel 3.5.5

The Ubuntu 12.10 Quantal Quetzal release includes the 3.5.0-17.28 Ubuntu Linux kernel which was based on the v3.5.5 upstream Linux kernel. This is an update from the 3.2.0-23.36 Ubuntu Linux kernel which shipped in Ubuntu 12.04 LTS Precise Pangolin and was based on the v3.2 upstream Linux kernel. Other notable changes with the Ubuntu 12.10 Quantal Quetzal kernel include:
<snip>


I do think that edit is in order. But let's wait for kansasnoob and Ian to catch up with us, as we do not want to leave them behind. See then if they concur with my thought process.

[INDENT][INDENT]is that light we see
[INDENT][INDENT][INDENT]at the end of this tunnel
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-18
Bashing-om,

> **Bashing-om said:**
> et al ; It is !

@ Raggylad;


I do think that edit is in order. But let's wait for kansasnoob and Ian to catch up with us, as we do not want to leave them behind. See then if they concur with my thought process.[INDENT][INDENT]
[/INDENT]
[/INDENT]


I'm still with you.

> is that light we see at the end of this tunnel 

So long as it's not the 9.52 from London or Little Rock !

Got to get my head down now; I'll check what you three think in the morning.  'Night.

---

### Post by kansasnoob on 2014-08-18
> **Bashing-om said:**
> et al ; It is !

@ Raggylad;


I do think that edit is in order. But let's wait for kansasnoob and Ian to catch up with us, as we do not want to leave them behind. See then if they concur with my thought process.

[INDENT][INDENT]is that light we see
[INDENT][INDENT][INDENT]at the end of this tunnel
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

I've been reading along but I'm stumped. If it would be helpful I do have both a Precise with only the original 3.2 series kernel installed as well as a Precise with the Quantal 3.5 series. I had all of those installed to test bug fixes from [this debacle]("http://iso.qa.ubuntu.com/qatracker/milestones/318/builds/73744/testcases"). That was a fun time ;)

---

### Post by Bashing-om on 2014-08-18
@ kansasnoob;

Yeah, I too will be glad to have HWE behind us with all the release upgrade problems.
As to here and now, as you do have 'quantal' installed, would be a comfort to compare the stanza you have:
"/var/lib/dpkg/status"
and see what your "Package: linux-headers-generic-lts-quantal" stanza is as far as ALL versions listed matching one another.
Which I think is the source of our bottle neck.

[INDENT][INDENT][INDENT]confirmation is nice
[INDENT][INDENT][INDENT]I was wrong once before
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Weidbrewer on 2014-08-18
Just posting to say that I am having a similar frustration with my upgrade.  If there is anything I canrun and paste from my side that might help (or at least to gather more data), let me know.

---

### Post by Bashing-om on 2014-08-18
Weidbrewer; Hi !

Be careful here, as the solution I am going to propose is specific to this situation and and very unlikely to fit your needs.  Not at all to say you are not welcome to follow along and try and adapt what we are doing in this thread to what you need. You may assist if you have the 'quantal' kernels installed - be aware they are End_Of_Live and as such should no longer be on your system ( if ya been taking care ).
Else: if you have that kernel series and will post the corresponding stanza for confirmation. would sure be nice.

If your situation is too different, start your own thread. and we will attend to your issue there.

I think my mind is pretty well made up and I am resolved to edit the control file as a measure to render aid to the package manager. 

This is not a normal thing to do.

BUT;
[INDENT][INDENT]sometimes we all need a little help,
[INDENT][INDENT][INDENT][INDENT]package managers too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-18
> **Bashing-om said:**
> @ kansasnoob;

Yeah, I too will be glad to have HWE behind us with all the release upgrade problems.
As to here and now, as you do have 'quantal' installed, would be a comfort to compare the stanza you have:
"/var/lib/dpkg/status"
and see what your "Package: linux-headers-generic-lts-quantal" stanza is as far as ALL versions listed matching one another.
Which I think is the source of our bottle neck.

[INDENT][INDENT][INDENT]confirmation is nice
[INDENT][INDENT][INDENT]I was wrong once before
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

```
Package: linux-headers-generic-lts-quantal
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.54.59
Depends: linux-headers-3.5.0-54-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers
 available.
```

Just to be clear, that's a fully updated Precise that was installed with the 12.04.2 media so it has only the Quantal HWE. Since it was a recent install for follow up testing it has only the original and latest kernels:

```
lance@lance-desktop:~$ ls /boot
abi-3.5.0-23-generic         memtest86+.bin
abi-3.5.0-54-generic         memtest86+_multiboot.bin
config-3.5.0-23-generic      System.map-3.5.0-23-generic
config-3.5.0-54-generic      System.map-3.5.0-54-generic
grub                         vmlinuz-3.5.0-23-generic
initrd.img-3.5.0-23-generic  vmlinuz-3.5.0-54-generic
initrd.img-3.5.0-54-generic

```

---

### Post by kansasnoob on 2014-08-18
> **Bashing-om said:**
> Weidbrewer; Hi !

Be careful here, as the solution I am going to propose is specific to this situation and and very unlikely to fit your needs.  Not at all to say you are not welcome to follow along and try and adapt what we are doing in this thread to what you need. You may assist if you have the 'quantal' kernels installed - be aware they are End_Of_Live and as such should no longer be on your system ( if ya been taking care ).
Else: if you have that kernel series and will post the corresponding stanza for confirmation. would sure be nice.

If your situation is too different, start your own thread. and we will attend to your issue there.

I think my mind is pretty well made up and I am resolved to edit the control file as a measure to render aid to the package manager. 

This is not a normal thing to do.

BUT;
[INDENT][INDENT]sometimes we all need a little help,
[INDENT][INDENT][INDENT][INDENT]package managers too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

There is a thread:

[http://ubuntuforums.org/showthread.php?t=2240033](http://ubuntuforums.org/showthread.php?t=2240033)

I was just scared to jump into another :redface:

---

### Post by Weidbrewer on 2014-08-18
Actually did start one yesterday: [http://ubuntuforums.org/showthread.php?t=2240033](http://ubuntuforums.org/showthread.php?t=2240033)

---

### Post by kansasnoob on 2014-08-18
> **Weidbrewer said:**
> Actually did start one yesterday: [http://ubuntuforums.org/showthread.php?t=2240033](http://ubuntuforums.org/showthread.php?t=2240033)

I just replied there again :D

---

### Post by Bashing-om on 2014-08-18
Raggylad; Hey !

I am pretty well set in my mind what we are going to do:
as
"Config-Version: 3.5.0.51.56"
does not exist on the system, AND "This package will always depend on the latest generic 12.10 kernel headers
available."

Then let's make it so => 3.5.0-54.
3.5.0-54 headers and images are fully installed ( beats me then why you are booting a -52 kernel !) and are the latest available on the system.

I am going to sleep on this tonight and advise on the edits in the AM, and then we take some pokes and prods at removing kernels and headers; see what happens when trying to remove !


[INDENT][INDENT]I can not believe
[INDENT][INDENT][INDENT]-though it is so -
[INDENT][INDENT][INDENT][INDENT]the package manager is lying !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-19
> **Bashing-om said:**
> 

[INDENT][INDENT]I can not believe[INDENT][INDENT][INDENT]-though it is so -[INDENT][INDENT][INDENT][INDENT]the package manager is lying !
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


@ Bashing-om,

Somewhere there must be a binary situation (or series of them) which causes it to appear to lie - it's just a machine processing ones & zeroes, after all !  Trick is, finding 'em.

---

### Post by Bashing-om on 2014-08-19
Raggyladl Yeah, so true !

But, let's try and tell the package manager the truth. Let's edit the status file to what is true.
Backup the file just for whatever may perchance, and then we can revert back to this state of affairs.
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-19aug2014

```

Fire up your text editor and make the changes:
```

gksudo gedit /var/lib/dpkg/status

```
Find the stanza we are going to operate on:
search term: Package: "linux-headers-generic-lts-quantal"

Here is another example of what that stanza should resemble:
> 
Package: linux-headers-generic-lts-raring
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 27
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta-lts-raring
Version: 3.8.0.44.44
Depends: linux-headers-3.8.0-44-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers  available.
 as a reassurance to you.
-------------------------------
Your current stanza that we will edit:
> 
Here's what I got to that last:

Package: linux-headers-generic-lts-quantal
Status: install ok unpacked
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.52.57
Config-Version: 3.5.0.51.56
Depends: linux-headers-3.5.0-52-generic
Description: Generic Linux kernel headers
This package will always depend on the latest generic 12.10 kernel headers
available.

1) Change the line "Status: install ok unpacked" to install ok install
2) Change the version in the line "Version: 3.5.0.52.57" to 3.5.0.54.81
3) Remove the line: "Config-Version: 3.5.0.51.56"  That version does not exist, and as curios as I am as to how it got there, I am not going to worry over it.
4) Change the line "Depends: linux-headers-3.5.0-52-generic" to 3.5.0.54-generic


Save what we have, and next change the stanza: Package: linux-image-generic-lts-quantal
change the line: "Version: 3.5.0.54.59" to 3.5.0.54.81
Because version 3.5.0.54.59 also does not exist on the system

Save the file once more, and exit back to terminal:

At this point, let's clean things up and get a new look:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean

```

what now results from:
```

sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```

I think I have thought this through and ->
IF ALL goes well, then next let's try and remove one of those problematic kernels !

[INDENT][INDENT]we are gonna whoop this
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-19
Bashing-om,

Here's the results from the clean up code (2nd code box from last):

```
unick@ubuntu:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-19aug2014
[sudo] password for unick: 
unick@ubuntu:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-19aug2014
unick@ubuntu:~$ gksudo gedit /var/lib/dpkg/status
unick@ubuntu:~$ sudo rm -fr /var/lib/apt/lists
unick@ubuntu:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory `/var/lib/apt/lists'
mkdir: created directory `/var/lib/apt/lists/partial'
unick@ubuntu:~$ sudo apt-get autoclean
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing linux-headers-generic-lts-quantal (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
unick@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing linux-headers-generic-lts-quantal (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
unick@ubuntu:~$ sudo apt-get clean
unick@ubuntu:~$ 

```

Not good ?  Probably the result of my poor 'monkey see  ... monkey do' technique, though I make max use of cut & paste.

Results of last code box to follow next.

---

### Post by Raggylad on 2014-08-19
The results from the first line:

```
unick@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://gb.archive.ubuntu.com precise Release.gpg [198 B]               
Get:3 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:4 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:5 http://security.ubuntu.com precise-security Release [50.7 kB]            
Get:6 http://gb.archive.ubuntu.com precise Release [49.6 kB]                   
Get:7 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:8 http://linux.dropbox.com precise Release.gpg [489 B]                     
Get:9 http://security.ubuntu.com precise-security/main Sources [108 kB]        
Get:10 http://gb.archive.ubuntu.com precise-backports Release [50.8 kB]        
Get:11 http://linux.dropbox.com precise Release [2,603 B]                      
Get:12 http://gb.archive.ubuntu.com precise/main Sources [934 kB]              
Get:13 http://linux.dropbox.com precise/main i386 Packages [1,143 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:14 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:15 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]  
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [444 kB] 
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:20 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:21 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Get:23 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:24 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:25 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:26 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:27 http://security.ubuntu.com precise-security/main Translation-en [190 kB]
Get:28 http://security.ubuntu.com precise-security/multiverse Translation-en [1,299 B]
Get:29 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:30 http://security.ubuntu.com precise-security/universe Translation-en [59.8 kB]
Get:31 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:32 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:33 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:34 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:35 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:36 http://gb.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Get:37 http://gb.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:38 http://gb.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:39 http://gb.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:40 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]      
Get:41 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:42 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:43 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:44 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [856 kB]
Get:45 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:46 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:47 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:48 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:49 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:50 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:51 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:52 http://gb.archive.ubuntu.com precise-backports/main Sources [5,145 B]   
Get:53 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:54 http://gb.archive.ubuntu.com precise-backports/universe Sources [39.4 kB]
Get:55 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]
Get:56 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]
Get:57 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:58 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [42.2 kB]
Get:59 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:60 http://gb.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:61 http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:62 http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:63 http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Get:64 http://gb.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]   
Get:65 http://gb.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:66 http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]
Get:67 http://gb.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:68 http://gb.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]
Get:69 http://gb.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:70 http://gb.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]
Get:71 http://gb.archive.ubuntu.com precise/universe Translation-en [3,341 kB] 
Get:72 http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB [96.4 kB]
Get:73 http://gb.archive.ubuntu.com precise-updates/main Translation-en [362 kB]
Get:74 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [79.8 kB]
Get:75 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]
Get:76 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB [2,406 B]
Get:77 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en [3,027 B]
Get:78 http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB [5,492 B]
Get:79 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [144 kB]
Get:80 http://gb.archive.ubuntu.com precise-backports/main Translation-en [5,882 B]
Get:81 http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]
Get:82 http://gb.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:83 http://gb.archive.ubuntu.com precise-backports/universe Translation-en [33.8 kB]
Fetched 20.5 MB in 59s (344 kB/s)                                              
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing linux-headers-generic-lts-quantal (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-19
The results from the second line (my browser - Firefox - crashed while doing this):

```
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Malformed 3rd word in the Status line
E: Error occurred while processing linux-headers-generic-lts-quantal (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-19
And from the final line:

```
unick@ubuntu:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-54-generic
Found initrd image: /boot/initrd.img-3.5.0-54-generic
Found linux image: /boot/vmlinuz-3.5.0-52-generic
Found initrd image: /boot/initrd.img-3.5.0-52-generic
Found linux image: /boot/vmlinuz-3.5.0-51-generic
Found initrd image: /boot/initrd.img-3.5.0-51-generic
Found linux image: /boot/vmlinuz-3.5.0-47-generic
Found initrd image: /boot/initrd.img-3.5.0-47-generic
Found linux image: /boot/vmlinuz-3.5.0-46-generic
Found initrd image: /boot/initrd.img-3.5.0-46-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-65-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-65-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found Windows Vista (loader) on /dev/sda1
Skipping Windows Vista (loader) on Wubi system
done
unick@ubuntu:~$ 

```

---

### Post by Bashing-om on 2014-08-19
Raggylad; Well !

Package manager definitely does not accept that the package "linux-headers-generic-lts-quantal" is installed.

OK go back with the text editor and change the one line that the package manager is unhappy with:
Status: install ok install
Back to :
Status: install ok unpacked
And let's see what results from:
```

sudo apt-get install --reinstall linux-headers-generic-lts-quantal

``` ( fingers crossed that the repository still holds it !)

Except for that little miss-instance .. looking pretty good .

[INDENT][INDENT][INDENT]we poke some more
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-19
Basing-om,

Not sure this is good ?

```
unick@ubuntu:~$ sudo apt-get install --reinstall linux-headers-generic-lts-quantal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-headers-generic-lts-quantal is not possible, it cannot be downloaded.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-19
Raggylad; UMMpphh !

Looks like that End_Of_Life package IS no longer available ..
Maybe check and see what returns:
```

apt-cache show linux-headers-generic-lts-quantal

```
Just to verify and make sure.

Then if indeed the package is not available ->
How about we "TRY" this.
Boot with the original precise kernel, purge all the 'quantal' kernels, and then -if the purge works out - install the 'trusty' kernels ?

What have we got to work with ?
```

ls -la /boot
dpkg -l | grep linux-

```

Bear in mind that the 3.2 kernels having issues do bother me greatly.
If you can boot on 'precise' and we can/do purge 'quantal' maybe then we can fix the 3.2 dependencies ??

Mind you it is a thought, but

[INDENT][INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-19
Bashing-om,

This is what results from the check:

```
unick@ubuntu:~$ apt-cache show linux-headers-generic-lts-quantal
Package: linux-headers-generic-lts-quantal
Status: install ok unpacked
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.54.81
Depends: linux-headers-3.5.0.54-generic
Description-en: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers
 available.

Package: linux-headers-generic-lts-quantal
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.54.59
Depends: linux-headers-3.5.0-54-generic
Filename: pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.54.59_i386.deb
Size: 2420
MD5sum: a34e9dd0344da5e44cd12fb909d67d64
SHA1: 834e095205b966e05e4e64b5fa72be4cf58257b2
SHA256: ea819625de5721b1ac831752a1ba8ef10e2dc5440ae66e919dab609b4735ccb4
Description-en: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers
 available.
Description-md5: 49b52776080593de169d30338dd93a48
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m

unick@ubuntu:~$ 

```

I'll wait until you check this before pressing on with the next steps you suggested.

---

### Post by Bashing-om on 2014-08-19
Raggylad; Welp ;

Presently I am torn as to what to do:
> 
Package linux-headers-generic-lts-quantal

precise-updates (devel): Generic Linux kernel headers 
3.5.0.54.59: amd64 i386

Not only is that package available in the repository - that the package manager will not mess with; it is also available in the archives// BUT the version in the archives is a lower one (surprise surprise) !

Think'n -- lemme check the back post, best I recall version .59 is not installed ( reason for the change in the status file stanzas). Maybe we can get this file and 'dpkg -i' to get it installed.

But I still like the thought of booting the 3.2 precise kernel, purging quantal all together -may have to get real fancy, then, with grub's symlinks in /. -> install trusty kernel.
Grub ! May not be such a great thought after all.

[INDENT][INDENT][INDENT]thin'n
[INDENT][INDENT][INDENT][INDENT]what to do, what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

-------------------Hold every thing I have another 'better thought' !----------------

Not sure you pasted the complete output of:
```

apt-cache show linux-headers-generic-lts-quantal

```
need to check once more:
BUT:
this from the last seems to indicate we need to edit the 'status' file again:
> 
Version: 3.5.0.54.81
Depends: linux-headers-3.5.0.54-generic
 and make sure that the .54 version of the image and headers are installed !

a much better course of action, 
[INDENT][INDENT]see what results
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-19
Bashing-om,

Here's the complete output of running 

```
apt-cache show linux-headers-generic-lts-quantal
```

again:

```
unick@ubuntu:~$ apt-cache show linux-headers-generic-lts-quantal
Package: linux-headers-generic-lts-quantal
Status: install ok unpacked
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.54.81
Depends: linux-headers-3.5.0.54-generic
Description-en: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers
 available.

Package: linux-headers-generic-lts-quantal
Priority: optional
Section: devel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta-lts-quantal
Version: 3.5.0.54.59
Depends: linux-headers-3.5.0-54-generic
Filename: pool/main/l/linux-meta-lts-quantal/linux-headers-generic-lts-quantal_3.5.0.54.59_i386.deb
Size: 2420
MD5sum: a34e9dd0344da5e44cd12fb909d67d64
SHA1: 834e095205b966e05e4e64b5fa72be4cf58257b2
SHA256: ea819625de5721b1ac831752a1ba8ef10e2dc5440ae66e919dab609b4735ccb4
Description-en: Generic Linux kernel headers
 This package will always depend on the latest generic 12.10 kernel headers
 available.
Description-md5: 49b52776080593de169d30338dd93a48
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m

unick@ubuntu:~$ 
```

I need to go now - early start tomorrow - leave you to think about it all.

Thanks again.

---

### Post by Bashing-om on 2014-08-19
Raggylad; Hey !

I just looked back, and you DO have headers/images for 3.5.0.54 installed !
SO OK, edit the 'status' files:
 "Package: linux-headers-generic-lts-quantal"
and change the "Depends: linux-headers-3.5.0-52-generic (as was originally) to: "linux-headers-3.5.0.54-generic"

Also revert the changes made to stanza "Package: linux-image-generic-lts-quantal" and put it back to: "Version: 3.5.0.54.59"
NOW let's see what the package manager reports when the data bases are synced up again:
Save all and exit back to terminal.

```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```


all we want is something stable
[INDENT][INDENT][INDENT]not too much to ask
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-20
> **Bashing-om said:**
> Raggylad; Hey !

I just looked back, and you DO have headers/images for 3.5.0.54 installed !
SO OK, edit the 'status' files:
 "Package: linux-headers-generic-lts-quantal"
and change the "Depends: linux-headers-3.5.0-52-generic (as was originally) to: "linux-headers-3.5.0.54-generic"

Also revert the changes made to stanza "Package: linux-image-generic-lts-quantal" and put it back to: "Version: 3.5.0.54.59"
NOW let's see what the package manager reports when the data bases are synced up again:
Save all and exit back to terminal.

```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```


all we want is something stable[INDENT][INDENT][INDENT]not too much to ask
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

Here's what we got this time:

```
unick@ubuntu:~$ gksudo gedit /var/lib/dpkg/status
unick@ubuntu:~$ sudo rm -fr /var/lib/apt/lists
unick@ubuntu:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory `/var/lib/apt/lists'
mkdir: created directory `/var/lib/apt/lists/partial'
unick@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://gb.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:4 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:5 http://security.ubuntu.com precise-security Release [50.7 kB]            
Get:6 http://gb.archive.ubuntu.com precise Release [49.6 kB]                   
Get:7 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:8 http://linux.dropbox.com precise Release.gpg [489 B]                     
Get:9 http://security.ubuntu.com precise-security/main Sources [108 kB]        
Get:10 http://gb.archive.ubuntu.com precise-backports Release [50.8 kB]        
Get:11 http://linux.dropbox.com precise Release [2,603 B]                      
Get:12 http://gb.archive.ubuntu.com precise/main Sources [934 kB]              
Get:13 http://linux.dropbox.com precise/main i386 Packages [1,143 B]           
Get:14 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:15 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]  
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [444 kB] 
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:20 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:21 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Get:23 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:24 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:25 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:26 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:27 http://security.ubuntu.com precise-security/main Translation-en [190 kB]
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:28 http://security.ubuntu.com precise-security/multiverse Translation-en [1,299 B]
Get:29 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:30 http://security.ubuntu.com precise-security/universe Translation-en [59.8 kB]
Get:31 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:32 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:33 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:34 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:35 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:36 http://gb.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Get:37 http://gb.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:38 http://gb.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:39 http://gb.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:40 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]      
Get:41 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:42 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:43 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:44 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [856 kB]
Get:45 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:46 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:47 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:48 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:49 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:50 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:51 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:52 http://gb.archive.ubuntu.com precise-backports/main Sources [5,145 B]   
Get:53 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:54 http://gb.archive.ubuntu.com precise-backports/universe Sources [39.4 kB]
Get:55 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]
Get:56 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]
Get:57 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:58 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [42.2 kB]
Get:59 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:60 http://gb.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:61 http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:62 http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:63 http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Get:64 http://gb.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]   
Get:65 http://gb.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:66 http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]
Get:67 http://gb.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:68 http://gb.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]
Get:69 http://gb.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:70 http://gb.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]
Get:71 http://gb.archive.ubuntu.com precise/universe Translation-en [3,341 kB]
Get:72 http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB [96.4 kB]
Get:73 http://gb.archive.ubuntu.com precise-updates/main Translation-en [362 kB]
Get:74 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [79.8 kB]
Get:75 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]
Get:76 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB [2,406 B]
Get:77 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en [3,027 B]
Get:78 http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB [5,492 B]
Get:79 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [144 kB]
Get:80 http://gb.archive.ubuntu.com precise-backports/main Translation-en [5,882 B]
Get:81 http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]
Get:82 http://gb.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:83 http://gb.archive.ubuntu.com precise-backports/universe Translation-en [33.8 kB]
Fetched 20.5 MB in 58s (349 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ 
```

3.5.0.54 not installable ?

---

### Post by kansasnoob on 2014-08-20
> **Raggylad said:**
> Bashing-om,

Here's what we got this time:

```
unick@ubuntu:~$ gksudo gedit /var/lib/dpkg/status
unick@ubuntu:~$ sudo rm -fr /var/lib/apt/lists
unick@ubuntu:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory `/var/lib/apt/lists'
mkdir: created directory `/var/lib/apt/lists/partial'
unick@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://gb.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:4 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Get:5 http://security.ubuntu.com precise-security Release [50.7 kB]            
Get:6 http://gb.archive.ubuntu.com precise Release [49.6 kB]                   
Get:7 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:8 http://linux.dropbox.com precise Release.gpg [489 B]                     
Get:9 http://security.ubuntu.com precise-security/main Sources [108 kB]        
Get:10 http://gb.archive.ubuntu.com precise-backports Release [50.8 kB]        
Get:11 http://linux.dropbox.com precise Release [2,603 B]                      
Get:12 http://gb.archive.ubuntu.com precise/main Sources [934 kB]              
Get:13 http://linux.dropbox.com precise/main i386 Packages [1,143 B]           
Get:14 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:15 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]  
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [444 kB] 
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Get:20 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:21 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Get:23 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:24 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:25 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:26 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:27 http://security.ubuntu.com precise-security/main Translation-en [190 kB]
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:28 http://security.ubuntu.com precise-security/multiverse Translation-en [1,299 B]
Get:29 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:30 http://security.ubuntu.com precise-security/universe Translation-en [59.8 kB]
Get:31 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:32 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:33 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:34 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:35 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:36 http://gb.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Get:37 http://gb.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:38 http://gb.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:39 http://gb.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:40 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]      
Get:41 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:42 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:43 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:44 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [856 kB]
Get:45 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:46 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Get:47 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:48 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:49 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:50 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:51 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:52 http://gb.archive.ubuntu.com precise-backports/main Sources [5,145 B]   
Get:53 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:54 http://gb.archive.ubuntu.com precise-backports/universe Sources [39.4 kB]
Get:55 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]
Get:56 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [6,420 B]
Get:57 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:58 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [42.2 kB]
Get:59 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:60 http://gb.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:61 http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:62 http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:63 http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Get:64 http://gb.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]   
Get:65 http://gb.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:66 http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]
Get:67 http://gb.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:68 http://gb.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]
Get:69 http://gb.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:70 http://gb.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]
Get:71 http://gb.archive.ubuntu.com precise/universe Translation-en [3,341 kB]
Get:72 http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB [96.4 kB]
Get:73 http://gb.archive.ubuntu.com precise-updates/main Translation-en [362 kB]
Get:74 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [79.8 kB]
Get:75 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]
Get:76 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB [2,406 B]
Get:77 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en [3,027 B]
Get:78 http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB [5,492 B]
Get:79 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [144 kB]
Get:80 http://gb.archive.ubuntu.com precise-backports/main Translation-en [5,882 B]
Get:81 http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]
Get:82 http://gb.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:83 http://gb.archive.ubuntu.com precise-backports/universe Translation-en [33.8 kB]
Fetched 20.5 MB in 58s (349 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ 
```

3.5.0.54 not installable ?

I'm sure this won't magically fix things but I'm curious what the terminal will tell us if we're brutally specific (notice I'm using the -s suffix to only simulate):

```
sudo apt-get install linux-headers-3.5.0.54-generic -s
```

In fact, since we're simulating, might as well see the output of:

```
sudo apt-get install linux-image-generic-pae -s
```

And:

```
sudo apt-get install linux-headers-3.2.0-65-generic -s
```

And one more:

```
sudo apt-get install linux-headers-3.2.0-65-generic-pae -s
```

This situation has me super curious :)

---

### Post by Bashing-om on 2014-08-20
Yeah: I am more than intrigued !
This is getting my goat.

OK, we know that the stanza for "Package: linux-headers-generic-lts-quantal" was, and perhaps still is, in an inconsistent state. Now that makes me question what other control files for the kernels are in a bad way.
I think you, kansasnoob, has the slant on finding out. We know from past experience we can not go forward, we can not go back .. we need to find out the why. The only way to do this is poke at it and follow the signs.

Do as kansasnoob advises ->
[INDENT][INDENT][INDENT]let's find out for 
[INDENT][INDENT][INDENT]future's sake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-20
> **Bashing-om said:**
> Yeah: I am more than intrigued !
This is getting my goat.

OK, we know that the stanza for "Package: linux-headers-generic-lts-quantal" was, and perhaps still is, in an inconsistent state. Now that makes me question what other control files for the kernels are in a bad way.
I think you, kansasnoob, has the slant on finding out. We know from past experience we can not go forward, we can not go back .. we need to find out the why. The only way to do this is poke at it and follow the signs.

Do as kansasnoob advises ->
[INDENT][INDENT][INDENT]let's find out for 
[INDENT][INDENT][INDENT]future's sake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Well you've already knocked at least one brick out of the blockade:

**Now:**

```
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
```

**Post #94:**

```
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0-52-generic but it is not going to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-67-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

It's no longer puking over  *linux-image-generic-pae* :guitar:

---

### Post by Bashing-om on 2014-08-20
@ kansasnoob; Yeah !

Only goes to show we are not stuck stuck;
We just need to find the way forward !
Awaiting the results of your last request .. and off we go again.

[INDENT][INDENT][INDENT]where there is a will there is a way ->
[INDENT][INDENT][INDENT][INDENT]it's ubuntu !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-20
> **kansasnoob said:**
> I'm sure this won't magically fix things but I'm curious what the terminal will tell us if we're brutally specific (notice I'm using the -s suffix to only simulate):

```
sudo apt-get install linux-headers-3.5.0.54-generic -s
```

In fact, since we're simulating, might as well see the output of:

```
sudo apt-get install linux-image-generic-pae -s
```

And:

```
sudo apt-get install linux-headers-3.2.0-65-generic -s
```

And one more:

```
sudo apt-get install linux-headers-3.2.0-65-generic-pae -s
```

This situation has me super curious :)

Hi Kansanoob, Bashing-om,

Here's the results:
```

unick@ubuntu:~$ sudo apt-get install linux-headers-3.5.0.54-generic -s
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.5.0.54-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-3.5.0.54-generic' has no installation candidate
unick@ubuntu:~$ sudo apt-get install linux-image-generic-pae -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-generic-pae is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get install linux-headers-3.2.0-65-generic -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-3.2.0-65-generic : Depends: linux-headers-3.2.0-65 but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get install linux-headers-3.2.0-65-generic-pae -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-3.2.0-65-generic-pae : Depends: linux-headers-3.2.0-65 but it is not going to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by kansasnoob on 2014-08-20
> E: Package 'linux-headers-3.5.0.54-generic' has no installation candidate

So maybe repeat that after running:

```
sudo apt-get update
```

---

### Post by Bashing-om on 2014-08-20
Raggylad; Humm ??

Package manager still not too happy with " linux-headers-3.5.0.54-generic ", along with the other 3 !

Package manager say "Try 'apt-get -f install' with no packages (or specify a solution).". well we know '-f install' is fruitless, so let's ->
Specify a solution !
Let's try this:
get a updated/close view on the current installed kernel statuses:
```

dpkg -l | grep linux

```
And we know the the reference headers and images ( 3.5.0.54 ) are installed !, try and find out why the system does not think so.

Once more make up a reference copy of the stanza in the status file for "Package: linux-headers-generic-lts-quantal"" as we are going to use the package manager to mess with it, and want to compare the results:
```

sudo dpkg-reconfigure linux-headers-3.5.0.54-generic

```
Sorta unorthodox (??) and I can foresee that the system will want some direction ->With many packages, you&#8217;ll be prompted with some configuration questions you may not have known were there. You are flying here by the seat of your pants as I expect you will be  presented with a "wizard" on configuring issues in Ubuntu. We can only offer here our best guess/advise.

Hoping that the PM works it's magic or at least we get info of where to look to help the PM .

Now, if/done with -reconfigure, let's see if there is a change:
```

dpkg-l | grep linux

``` and let's compare to what was.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-20
> **kansasnoob said:**
> So maybe repeat that after running:

```
sudo apt-get update
```

Should I do this before what Bashing-om suggests in #140, or after ?  Or not at all ?

---

### Post by Raggylad on 2014-08-20
Bashing-om,

??:

```
unick@ubuntu:~$ dpkg-l | grep linux
dpkg-l: command not found
unick@ubuntu:~$ 
```

(Reference copy of current status file has been made)

---

### Post by Bashing-om on 2014-08-20
Raggylad; Fingers not keeping up with mind !
Should be:
```

dpkg -l | grep linux

``` that silly little space is important,

as to my procedure, I would just as soon postpone that - as it does have un-fore-seeable consequences . We can try come 'cleaner' ways to get the information we need. Might be best for now to keep to things we have control over . BUT, it sure will be interesting to see what does happen !

Go ahead and run the update and let's see what results:
Then:
```

apt-cache policy linux-headers-3.5.0.54-generic

```
and we will put the -reconfigure thing back in our back pocket for later use .
We poke and prod at 3.5.0..54 some more in other ways.
As we try and knock these 4 issues off, one at a time.

Now that is 
[INDENT][INDENT][INDENT]jut my thought, what say kansasnoob
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-20
Results from the first line:

```
unick@ubuntu:~$ dpkg -l | grep linux
ii  libselinux1                                  2.1.0-4.1ubuntu1                                 SELinux runtime shared libraries
ii  libv4l-0                                     0.8.6-1ubuntu2                                   Collection of video4linux support libraries
ii  libv4lconvert0                               0.8.6-1ubuntu2                                   Video4linux frame format conversion library
ii  linux-firmware                               1.79.16                                          Firmware for Linux kernel drivers
iU  linux-generic-lts-quantal                    3.5.0.52.57                                      Generic Linux kernel image and headers
iU  linux-generic-pae                            3.2.0.65.77                                      Complete Generic Linux kernel
pi  linux-headers-3.2.0-48                       3.2.0-48.74                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-49                       3.2.0-49.75                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-51                       3.2.0-51.77                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-52                       3.2.0-52.78                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-53                       3.2.0-53.81                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-54                       3.2.0-54.82                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-55                       3.2.0-55.85                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-57                       3.2.0-57.87                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-58                       3.2.0-58.88                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-59                       3.2.0-59.90                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-60                       3.2.0-60.91                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-61                       3.2.0-61.93                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-63                       3.2.0-63.95                                      Header files related to Linux kernel version 3.2.0
pi  linux-headers-3.2.0-64                       3.2.0-64.97                                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67                       3.2.0-67.101                                     Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic               3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-67-generic-pae           3.2.0-67.101                                     Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-32                       3.5.0-32.53~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-34                       3.5.0-34.55~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-36                       3.5.0-36.57~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-37                       3.5.0-37.58~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-39                       3.5.0-39.60~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-40                       3.5.0-40.62~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-41                       3.5.0-41.64~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-42                       3.5.0-42.65~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-43                       3.5.0-43.66~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-44                       3.5.0-44.67~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-45                       3.5.0-45.68~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46                       3.5.0-46.70~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-46-generic               3.5.0-46.70~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-47                       3.5.0-47.71~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-47-generic               3.5.0-47.71~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
pi  linux-headers-3.5.0-48                       3.5.0-48.72~precise1                             Header files related to Linux kernel version 3.5.0
pi  linux-headers-3.5.0-49                       3.5.0-49.74~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51                       3.5.0-51.77~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-51-generic               3.5.0-51.77~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
ii  linux-headers-3.5.0-52                       3.5.0-52.79~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54                       3.5.0-54.81~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54-generic               3.5.0-54.81~precise1                             Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
iU  linux-headers-generic                        3.2.0.65.77                                      Generic Linux kernel headers
iU  linux-headers-generic-lts-quantal            3.5.0.54.81                                      Generic Linux kernel headers
iU  linux-headers-generic-pae                    3.2.0.65.77                                      Generic Linux kernel headers
ii  linux-image-3.2.0-45-generic-pae             3.2.0-45.70                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-65-generic-pae             3.2.0-65.99                                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-67-generic-pae             3.2.0-67.101                                     Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-46-generic                 3.5.0-46.70~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-47-generic                 3.5.0-47.71~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-51-generic                 3.5.0-51.77~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-52-generic                 3.5.0-52.79~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-54-generic                 3.5.0-54.81~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.54.59                                      Generic Linux kernel image
ii  linux-image-generic-pae                      3.2.0.67.79                                      Generic Linux kernel image
ii  linux-libc-dev                               3.2.0-67.101                                     Linux Kernel Headers for development
ii  linux-sound-base                             1.0.25+dfsg-0ubuntu1.1                           base package for ALSA and OSS sound systems
ii  pptp-linux                                   1.7.2-6                                          Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                     2:4.05+dfsg-2                                    collection of boot loaders
ii  syslinux-common                              2:4.05+dfsg-2                                    collection of boot loaders (common files)
ii  syslinux-legacy                              2:3.63+dfsg-2ubuntu5                             Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                   2.20.1-1ubuntu3.1                                Miscellaneous system utilities
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-20
Update results:

```
unick@ubuntu:~$ sudo apt-get update
[sudo] password for unick: 
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://gb.archive.ubuntu.com precise Release                               
Get:2 http://gb.archive.ubuntu.com precise-updates Release [98.7 kB]           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://security.ubuntu.com precise-security Release [50.7 kB]            
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://linux.dropbox.com precise Release                                   
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [477 kB]       
Hit http://linux.dropbox.com precise/main i386 Packages                        
Get:6 http://security.ubuntu.com precise-security/main Sources [108 kB]
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [32.7 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,786 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [444 kB] 
Get:11 http://gb.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:12 http://gb.archive.ubuntu.com precise-updates/universe Sources [110 kB]  
Get:13 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,881 B]
Get:14 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [856 kB]
Ign http://linux.dropbox.com precise/main Translation-en_GB                    
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [102 kB]
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,644 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Get:18 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [253 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:20 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://gb.archive.ubuntu.com precise-backports/main Sources                
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources            
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 2,590 kB in 8s (321 kB/s)                                              
Reading package lists... Done
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-20
And here's the reaction to that second line:

```
unick@ubuntu:~$ apt-cache policy linux-headers-3.5.0.54-generic
linux-headers-3.5.0.54-generic:
  Installed: (none)
  Candidate: (none)
  Version table:
unick@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-08-20
Raggylad; When I do not know;

I am in a place where I might learn something !
> 
ii  linux-headers-3.5.0-54                       3.5.0-54.81~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-54-generic <snip>

ii  linux-image-3.5.0-54-generic                 3.5.0-54.81~precise1                             Linux kernel image for version 3.5.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-quantal              3.5.0.54.59                                      Generic Linux kernel image


See ! It is installed ! .. Why oh why does not the package manager recognize that fact ??
Is there nothing in the status file ?
Look in '/var/lib/dpkg/status -> "Package: linux-headers-3.5.0-54" and "Package: linux-headers-3.5.0-54-generic" and "Package: linux-image-3.5.0-54-generic" // see what is listed in those stanzas. See if we can trace this anomaly down !

Look about and see, follow the trail
[INDENT][INDENT][INDENT]where is that hound dog when we need him
[/INDENT][/INDENT][/INDENT]


[INDENT][INDENT][INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-21
Bashing-om,

Here's what I found in the Status file;


Package: linux-headers-3.5.0-54
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 57499
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: all
Source: linux-lts-quantal
Version: 3.5.0-54.81~precise1
Depends: coreutils | fileutils (>= 4.0)
Description: Header files related to Linux kernel version 3.5.0
 This package provides kernel header files for version 3.5.0, for sites
 that want the latest kernel headers. Please read
 /usr/share/doc/linux-lts-quantal-headers-3.5.0-54/debian.README.gz for details


Package: linux-headers-3.5.0-54-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 11048
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-lts-quantal
Version: 3.5.0-54.81~precise1
Provides: linux-headers, linux-headers-3.0
Depends: linux-headers-3.5.0-54, libc6 (>= 2.11)
Description: Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
 This package provides kernel header files for version 3.5.0 on


Package: linux-image-3.5.0-54-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 116107
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-lts-quantal
Version: 3.5.0-54.81~precise1
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-lts-quantal-doc-3.5.0 | linux-lts-quantal-source-3.5.0, linux-lts-quantal-tools, linux-headers-3.5.0-54-generic
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

Last stanza more hopeful ?

---

### Post by Bashing-om on 2014-08-21
Raggylad; kansasanoob; Now that "last stanza" ->

Is thought provoking, indeed.

Let's take the hint and see !
```

sudo apt-get install linux-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-headers-generic

``` as initially I see no fault with '3.5.0-54'; So why then is the package manager puking over it ?
Maybe attempting to install the meta-packages will either resolve this sloppyation, or give a hint why it pukes !

Keep in mind folks, when we do get to a dead end -or run out of options - or run out of patience, there is the option to take matters into our own hands and manually remove the images and headers , leaving the package manager still in an inconsistent state , but a state that might be easier to fix .

There are 3 other dependency issues pending a solution, maybe this too will help them.

I do though want to know the why. I will learn something !

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-21
Bashing-om,

Here are the results of those three commands:

```
unick@ubuntu:~$ sudo apt-get install linux-generic
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic : Depends: linux-image-generic (= 3.2.0.67.79) but it is not going to be installed
                 Depends: linux-headers-generic (= 3.2.0.67.79) but 3.2.0.65.77 is to be installed
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get install linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.2.0-67-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.2.0.67.79 is to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

I am learning too (I'd never edited code scripts before) and am gradually developing some inkling of how you are tackling this.  Thanks again.

---

### Post by Bashing-om on 2014-08-21
Raggylad; This is getting real old !

OK, we do not have "linux-image-generic (= 3.2.0.67.79)" nor " linux-image-generic-pae (= 3.2.0.65.77)" installed.
How bout we see if we can get them installed ? .. now, I am not sure of the proper syntax to do so .. 
but, let's try it as:
```

sudo apt-get install linux-image=3.2.0-67.77-generic-pae

``` note the use of "=" in an attempt to install particularly ! See if that flies.
else maybe try as 3.2.0.67.77
If we can get this to install one way or the other, then we can also try the same same for "3.2.0.67.79".

[INDENT][INDENT]if at first you do not succeed
[INDENT][INDENT][INDENT][INDENT]try try again ( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-21
Bashing-om,

Ungood ?

```
unick@ubuntu:~$ sudo apt-get install linux-image=3.2.0-67.77-generic-pae
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version ‘3.2.0-67.77-generic-pae’ for ‘linux-image’ was not found
unick@ubuntu:~$ 

```

---

### Post by Bashing-om on 2014-08-21
Raggylad; Honestly,

With all the other round robin round and around we goes -> I just do not know.

What results with the alternative:
```

sudo apt-get install linux-image=3.2.0.67.77-generic-pae

```
As I say, I am not sure of the proper syntax to obtain that package explicitly.

might be time to holler for expert advise (Ian).

see what haps
[INDENT][INDENT]there is that option
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-22
Bashing-om,

Not better?

```
unick@ubuntu:~$ sudo apt-get install linux-image=3.2.0.67.77-generic-pae
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version ‘3.2.0.67.77-generic-pae’ for ‘linux-image’ was not found
unick@ubuntu:~$
```

---

### Post by ian-weisser on 2014-08-22
> $ sudo apt-get install linux-image=3.2.0.67.**77**-generic-pae

The version seems to have bumped up from 77 to 79:

```
$ rmadison -u ubuntu linux-image-generic-pae
[...]
 linux-image-generic-pae | 3.2.0.23.25  | precise          | i386
 linux-image-generic-pae | 3.2.0.67.79  | precise-security | i386
 linux-image-generic-pae | 3.2.0.67.**79**  | precise-updates  | i386
[...]

```

---

### Post by Bashing-om on 2014-08-22
@ ian-weisser; Hey thanks !

Guidance please, in order to install that explicit package from the repository is:
> 
sudo apt-get install linux-image=3.2.0-67.79-generic-pae

The proper syntax ?? Is it even possible to obtain the 'package' at this level ?
I surely do  not need a failure on my part to understand the syntax to stand in my way.

Believe me I struggle to find my way through this maze, and to identify where the failures are.
Preparing to do my homework, and see what I can learn to step through just one more  of these issues.

Hoo boy !
[INDENT][INDENT]that process of learning
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-08-22
Well, I have never had reason to try it myself,
but the previous error message "E: Version &#8216;number&#8217; for &#8216;package&#8217; was not found" certainly makes it seem you guys are on the right path.

---

### Post by Bashing-om on 2014-08-22
ian-weisser; Well !

LOL, Now I do not feel quite so bad .

I recon we learn the hard way ... keep poking till something gives and we learn better.

[INDENT][INDENT]Oh Joy !
[INDENT][INDENT][INDENT]I am fixing to learn something new
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-22
Raggylad; Backing up and regrouping !

I am in the position to accept that the version we want is not getable in the manner I am trying. Must be under 'version control' from the generic "linux-headers-generic". I am unable to fashion any syntax to obtain the particular version".
So back to looking at the status file for the entry for "linux-lts-quantal".
because:
> 
Package: linux-headers-3.5.0-54 -------------->Source: linux-lts-quantal -> Version: 3.5.0-54.81~precise1
Package: linux-headers-3.5.0-54-generic --> Source: linux-lts-quantal -> Version: 3.5.0-54.81~precise1
Package: linux-image-3.5.0-54-generic ----> Source: linux-lts-quantal -> Version: 3.5.0-54.81~precise1

points us back in that direction.

Let's see what it relates as to what is required, and what is installed -> and what we can/should change.

See how that relates to the entry in the status file for:
search term:
Package: linux-image-generic
-----------------------------------------------
We have poked, prodded and done so many unproductive things, it is getting difficult to see this tree for all the forest.
BUT ->
Got to be a way to get this " linux-image-generic (= 3.2.0.67.79) but it is not going to be installed" under control.

[INDENT][INDENT]what does it take
[INDENT][INDENT][INDENT]to get a dependency like you
[INDENT][INDENT][INDENT][INDENT][INDENT]satisfied ![/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-23
> **Bashing-om said:**
> Raggylad; Backing up and regrouping !

I am in the position to accept that the version we want is not getable in the manner I am trying. Must be under 'version control' from the generic "linux-headers-generic". I am unable to fashion any syntax to obtain the particular version".
So back to looking at the status file for the entry for "linux-lts-quantal".
because:

points us back in that direction.

Let's see what it relates as to what is required, and what is installed -> and what we can/should change.

See how that relates to the entry in the status file for:
search term:
Package: linux-image-generic
-----------------------------------------------
We have poked, prodded and done so many unproductive things, it is getting difficult to see this tree for all the forest.
BUT ->
Got to be a way to get this " linux-image-generic (= 3.2.0.67.79) but it is not going to be installed" under control.[INDENT][INDENT]what does it take[INDENT][INDENT][INDENT]to get a dependency like you[INDENT][INDENT][INDENT][INDENT][INDENT]satisfied ![/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

The status file has the following when I searched for "linux-lts-quantal":

```
Package: linux-image-3.5.0-54-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 116107
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-lts-quantal
Version: 3.5.0-54.81~precise1
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, ndiswrapper-modules-1.9, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-lts-quantal-doc-3.5.0 | linux-lts-quantal-source-3.5.0, linux-lts-quantal-tools, linux-headers-3.5.0-54-generic
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.5.0 on 32 bit x86 SMP
 This package contains the Linux kernel image for version 3.5.0 on
 32 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

```

And when I searched for "Package: linux-image-generic", it showed this;


```
Package: linux-image-generic-pae
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 3.2.0.67.79
Depends: linux-image-3.2.0-67-generic-pae, linux-firmware
Description: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
```

---

### Post by Bashing-om on 2014-08-23
Raggylad; UUoohhh ...

Is this:
> 
Package: linux-image-generic-pae
Status: install ok [color=red]installed[/color]
Version: 3.2.0.67.79
 that dark horse we have been hunting ?

And, Is there no return for the term:
Package: linux-image-generic
specifically ?

As due consideration is given to changing that version to " 3.5.0-54.81~precise1" or maybe  " 3.5.0-54 "

EDIT:
MY stanza for the package as installed in 'trusty':
> 
Package: linux-image-generic
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 28
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 3.13.0.34.40
Depends: linux-image-3.13.0-34-generic, linux-image-extra-3.13.0-34-generic, linux-firmware
Description: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.

as in yours is:
"Depends: linux-image-3.2.0-67-generic-pae, linux-firmware"
change that line also (??) to reflect:
3.5.0-54.81~precise1

end edit.

[INDENT][INDENT]my mind, after all this time
[INDENT][INDENT][INDENT]all in a-whirl
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-23
Bashing-om,

Just checked again.  This is all I get when I search for "Package: linux-image-generic":


```
Package: linux-image-generic-pae
Status: install ok installed
Priority: optional
Section: kernel
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 3.2.0.67.79
Depends: linux-image-3.2.0-67-generic-pae, linux-firmware
Description: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
```

EDIT:  I'll be on for about another hour but then I'll be travelling and offline for 12 hours or so.

---

### Post by Bashing-om on 2014-08-23
Raggylad; Hey hey !

Still think we are onto something.

When you can, make the two edits to the stanza "Package: linux-image-generic-pae" - Remember, always a good idea to make a means of backup to effect a recovery when things go south.

Make the edits and see what results by:
```

sudo apt-get update
sudo apt-get upgrade

``` and let's see what the package manager relates to us now.


[INDENT][INDENT]try it
[INDENT][INDENT][INDENT]no workie
[INDENT][INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-23
Bashing-om,

Sorry - being slow.  Which two edits ?  Set up & ready to do it (with backed up status file), but .....

---

### Post by Bashing-om on 2014-08-23
Raggylad; Hey;

Do this: -> Package: linux-image-generic-pae
change "Version: 3.2.0.67.79" to be version 3.5.0-54.81~precise1
change "Depends: linux-image-3.2.0-67-generic-pae, linux-firmware" to be  3.5.0-54

I think (??) as we have no install of the 3.5.0-54 linux-image-generic-pae
per:
ii  linux-image-generic-pae                      3.2.0.67.79

Maybe we can cheat here, and get up onto 'trusty' and get rid of these past headaches .

Hey it is one way forward !

[INDENT][INDENT]do this and I hope we are glad
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-23
Bashing-om,

Results:
```

unick@ubuntu:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-23aug2014
[sudo] password for unick: 
unick@ubuntu:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-19aug2014
unick@ubuntu:~$ gksudo gedit /var/lib/dpkg/status
unick@ubuntu:~$ sudo apt-get update
[sudo] password for unick: 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://gb.archive.ubuntu.com precise Release.gpg                         
Hit http://gb.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://security.ubuntu.com precise-security Release                        
Hit http://gb.archive.ubuntu.com precise Release                               
Hit http://gb.archive.ubuntu.com precise-updates Release                       
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://linux.dropbox.com precise Release.gpg                               
Hit http://security.ubuntu.com precise-security/restricted Sources   
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise/restricted Sources          
Hit http://gb.archive.ubuntu.com precise/universe Sources            
Hit http://gb.archive.ubuntu.com precise/multiverse Sources          
Hit http://gb.archive.ubuntu.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex       
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/main Sources
Hit http://gb.archive.ubuntu.com precise-updates/restricted Sources
Hit http://gb.archive.ubuntu.com precise-updates/universe Sources    
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://linux.dropbox.com precise Release                         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/main Sources      
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://linux.dropbox.com precise/main i386 Packages
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Ign http://linux.dropbox.com precise/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_GB
Ign http://linux.dropbox.com precise/main Translation-en
Reading package lists... Done
unick@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.5.0-54.81~precise1 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-65-generic but it is not installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
 linux-image-generic-pae : Depends: linux-image-3.5.0-54-generic-pae but it is not installable
E: Unmet dependencies. Try using -f.
unick@ubuntu:~$ 
```

Got to go now; back on tomorrow.  Thanks again.

---

### Post by Bashing-om on 2014-08-23
Raggylad; Welp;

Not as much as I had hoped, but maybe we can:
```

sudo apt-get install linux-headers-3.2.0-65-generic

```

BUT ! We now have this situation:
> 
linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic [color=red]but it is not installable[/color]
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not installed
 linux-image-generic-pae : Depends: linux-image-3.5.0-54-generic-pae but it is not installable


But if we can get the 3.2 kernel operational, maybe we can get the 3.13 kernel installed and get rid of the 3.5 kernels !

Else back once more to working on 3.5 !

[INDENT][INDENT][INDENT]gotta be a way !
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-23
Raggylad; Hi !


Just a note before It slips my mind, in the event we still can not install/remove anything:
How bout this as a thought, instead of 'guessing' let's see what the recommendation for the "version" in '  - Package: linux-image-generic-pae -
is:
```

apt-cache show linux-image-generic-pae

```

[INDENT][INDENT]not the size of the dog in the fight
[INDENT][INDENT][INDENT]the size of the fight
[INDENT][INDENT][INDENT]that matters
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-24
> **Bashing-om said:**
> Raggylad; Welp;

Not as much as I had hoped, but maybe we can:
```

sudo apt-get install linux-headers-3.2.0-65-generic

```

BUT ! We now have this situation:


But if we can get the 3.2 kernel operational, maybe we can get the 3.13 kernel installed and get rid of the 3.5 kernels !

Else back once more to working on 3.5 !
[INDENT][INDENT][INDENT]gotta be a way !
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

Hi.  Results for the above:
```

unick@ubuntu:~$ sudo apt-get install linux-headers-3.2.0-65-generic
[sudo] password for unick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.65.77) but 3.5.0-54.81~precise1 is to be installed
 linux-headers-3.2.0-65-generic : Depends: linux-headers-3.2.0-65 but it is not going to be installed
 linux-headers-generic-lts-quantal : Depends: linux-headers-3.5.0.54-generic but it is not installable
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-65-generic-pae but it is not going to be installed
 linux-image-generic-pae : Depends: linux-image-3.5.0-54-generic-pae but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
unick@ubuntu:~$ 
```

---

### Post by Raggylad on 2014-08-24
> **Bashing-om said:**
> Raggylad; Hi !


Just a note before It slips my mind, in the event we still can not install/remove anything:
How bout this as a thought, instead of 'guessing' let's see what the recommendation for the "version" in '  - Package: linux-image-generic-pae -
is:
```

apt-cache show linux-image-generic-pae

```
[INDENT][INDENT]not the size of the dog in the fight[INDENT][INDENT][INDENT]the size of the fight[INDENT][INDENT][INDENT]that matters
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


And to this one ......

```
Package: linux-image-generic-pae
Priority: optional
Section: metapackages
Installed-Size: 31
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 3.2.0.23.25
Depends: linux-image-3.2.0-23-generic-pae, linux-firmware
Filename: pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.23.25_i386.deb
Size: 2498
MD5sum: 453e7b595f1645ee780879fc6c4cab04
SHA1: a4129b2dfa458affb997bcdc66681430f7bd8740
SHA256: 41ca403833e7c7cfc734f3d865f3dffe6b99b4b07af938c703079b3e11e63cdf
Description-en: Generic Linux kernel image
 This package will always depend on the latest generic kernel image
 available.
Description-md5: 6d632579c673704f44b290b16e7dbfd1
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
```

---

### Post by Bashing-om on 2014-08-24
Raggylad; Sheeeessshh !

That too was unproductive !
As well, from this:
> 
Package: linux-image-generic-pae -> Depends: linux-image-3.2.0-23-generic-pae, linux-firmware

We know that "Package: linux-image-generic-pae" is not the file we want to mess with directly.

So revert those edits (both) back to the original.

As much as I want to know where this "hang-up" is, I am about to the point of disgust with myself to do the manual removal of the kernel's images, headers and files. - Do not know where we are breaking the chain of dependencies in reference to where they are already broken ; to this time not able to find out- Then fix the package manager.

I would really like to learn the why and HOW; but, are we out of time ?

[INDENT][INDENT]ring around the posey
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-25
> **Bashing-om said:**
> 
As much as I want to know where this "hang-up" is, I am about to the point of disgust with myself to do the manual removal of the kernel's images, headers and files. - Do not know where we are breaking the chain of dependencies in reference to where they are already broken ; to this time not able to find out- Then fix the package manager.

I would really like to learn the why and HOW; but, are we out of time ?
[INDENT][INDENT]ring around the posey
[/INDENT]
[/INDENT]


Bashing-om,

I deeply appreciate all your time and effort (together with that of Kansasnoob and Ian), but I fear that we _are_, after trying for two weeks, out of time. I just don't have the time left to give this the level of attention that I have been able to give it thus far. I sincerely hope that it has been a useful time for you; I have learned a lot.  

I'll now head in the direction of a fresh install of 14.04 - after seeking Kansasnoob's advice on how to avoid pitfalls.

---

### Post by kansasnoob on 2014-08-25
> **Raggylad said:**
> Bashing-om,

I deeply appreciate all your time and effort (together with that of Kansasnoob and Ian), but I fear that we _are_, after trying for two weeks, out of time. I just don't have the time left to give this the level of attention that I have been able to give it thus far. I sincerely hope that it has been a useful time for you; I have learned a lot.  

I'll now head in the direction of a fresh install of 14.04 - after seeking Kansasnoob's advice on how to avoid pitfalls.

Lets begin by having a look at your hardware so we can decide what version and flavor of Ubuntu might be best:

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

```
free -m
```

Once we figure that out you can download and burn whatever we decide on. Then it's time to boot into Windows, delete the Wubi install like you would any installed app in Windows, defrag Windows (possibly more than once), then [use Vista's own partitioning tool to resize itself]("http://www.techrepublic.com/blog/windows-and-office/how-do-i-resize-a-vista-partition-without-damaging-data/") and give us room to create the Ubuntu partitions.

One thing that may cause us to perform a new Wubi install rather than a dual-boot is that sometimes Windows drops files at the end of a disc that it's own defrag tool won't move, but we'll cross that bridge if and when we come to it. The [free version of Paragon]("http://download.cnet.com/Paragon-Partition-Manager-Free-Edition/3000-2248_4-10904411.html") used to be able to deal with that though so if needed we'll try that.

---

### Post by Raggylad on 2014-08-27
> **kansasnoob said:**
> Lets begin by having a look at your hardware so we can decide what version and flavor of Ubuntu might be best:

```
cat /proc/cpuinfo | head -10
```

```
lspci | grep VGA
```

```
free -m
```

Once we figure that out you can download and burn whatever we decide on. Then it's time to boot into Windows, delete the Wubi install like you would any installed app in Windows, defrag Windows (possibly more than once), then [use Vista's own partitioning tool to resize itself]("http://www.techrepublic.com/blog/windows-and-office/how-do-i-resize-a-vista-partition-without-damaging-data/") and give us room to create the Ubuntu partitions.

One thing that may cause us to perform a new Wubi install rather than a dual-boot is that sometimes Windows drops files at the end of a disc that it's own defrag tool won't move, but we'll cross that bridge if and when we come to it. The [free version of Paragon]("http://download.cnet.com/Paragon-Partition-Manager-Free-Edition/3000-2248_4-10904411.html") used to be able to deal with that though so if needed we'll try that.

@kansanoob,

Here's the results from the above:

```
unick@ubuntu:~$ cat /proc/cpuinfo | head -10
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
stepping    : 11
microcode    : 0xb3
cpu MHz        : 800.000
cache size    : 4096 KB
physical id    : 0
unick@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
unick@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4026       3109        916          0        631       1937
-/+ buffers/cache:        541       3485
Swap:          255         44        211
unick@ubuntu:~$ 
```

---

### Post by kansasnoob on 2014-08-27
Based on that I'd think you'd be fine with 14.04.1 amd64. I didn't think to ask what desktop environment you prefer. The direct download for Ubuntu 14.04.1 amd64 including links to info regarding disc or USB creation is here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

If you prefer another flavor (or prefer using a torrent for downloading) the links are here:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Download_Ubuntu_14.04_LTS](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Download_Ubuntu_14.04_LTS)

Once you've created a live DVD or USB it's a good idea to [enter the advanced boot options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") on first boot and run *Check disc for defects* just to be sure the media is correct before proceeding.

Have you booted Windows yet and deleted the old Wubi install:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F)

If so it's time to defrag:

[http://www.ehow.com/how_5053714_defrag-windows-vista.html](http://www.ehow.com/how_5053714_defrag-windows-vista.html)

Then resize:

[http://www.techrepublic.com/blog/windows-and-office/how-do-i-resize-a-vista-partition-without-damaging-data/](http://www.techrepublic.com/blog/windows-and-office/how-do-i-resize-a-vista-partition-without-damaging-data/)

I'm going to stop there for the moment. I'll be keeping my fingers crossed that the resize goes OK :)

If so I'll then explain how to safely install Ubuntu in a dual-boot. It's much easier than one might think ;)

---

### Post by Raggylad on 2014-08-28
@Kansasnoob,

Thanks for the above (#175).  I've downloaded and created a 14.04.1 disc and run *Check Disc** on it *- all OK.

Just about to boot up Windows to delete/defrag/resize.

Will report back once done.

---

### Post by Bashing-om on 2014-08-28
Raggylad/kansasnoob
I continue with an active interest.

[INDENT][INDENT]just so yall know
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-28
> **Raggylad said:**
> @Kansasnoob,

Thanks for the above (#175).  I've downloaded and created a 14.04.1 disc and run *Check Disc** on it *- all OK.

Just about to boot up Windows to delete/defrag/resize.

Will report back once done.

Cool, I'm subscribed to the thread now so I'll be ready when you are ................. or when I wake from my next nap :biggrin:

---

### Post by Raggylad on 2014-08-29
> **Bashing-om said:**
> Raggylad/kansasnoob
I continue with an active interest.
[INDENT][INDENT]just so yall know
[/INDENT]
[/INDENT]

@Bashing-om,

Again, many thanks for all your help and time.

---

### Post by Raggylad on 2014-08-29
> **kansasnoob said:**
> Cool, I'm subscribed to the thread now so I'll be ready when you are ................. or when I wake from my next nap :biggrin:

@Kansasnoob,

Now defragged and resized - apparently successfully.  I say 'apparently' because Windows is not very stable; after both the defrag and the resize it had blue screen crashes.  I'm currently running in safe (with networking) mode.

After resizing, the results were:
C: 74.44 GB NTFS
37.34 GB unallocated.

[INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-29
> **Raggylad said:**
> @Kansasnoob,

Now defragged and resized - apparently successfully.  I say 'apparently' because Windows is not very stable; after both the defrag and the resize it had blue screen crashes.  I'm currently running in safe (with networking) mode.

After resizing, the results were:
C: 74.44 GB NTFS
37.34 GB unallocated.

[INDENT][/INDENT]
[INDENT][/INDENT]

That's why I prefer using Windows own tools for dealing with itself :)

So what do you want to do next? 

Just install Ubuntu in the free space?

Or should we fiddle with Windows a little bit?

I've nearly forgotten what little I did know about fixing Windows so I probably can't be of a lot of help with that. I have some important errands to run so let me think about this ;)

Oh, something that might be quite helpful is booting the Ubuntu DVD choosing to Try without installing and posting a screenshot of Gparted. That could provide some info that helps us decide what to do next.

---

### Post by Bashing-om on 2014-08-29
Raggylad; Hey !

I know a bit here !
In Windows, run defrag ( X2) and chkdsk ( check disk), at least twice, so Windows resets the partition table.
Then we are ready to install ubuntu onto that "unallocated" space.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-29
> **Bashing-om said:**
> Raggylad; Hey !

I know a bit here !
In Windows, run defrag ( X2) and chkdsk ( check disk), at least twice, so Windows resets the partition table.
Then we are ready to install ubuntu onto that "unallocated" space.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

I was thinking of having Raggylad run chkdsk /r in safemode after being sure Vista has at least 20% free space :)

---

### Post by Raggylad on 2014-08-29
Thanks to advice from the sysadmins at work, I've been able to do some Windows housekeeping.  I've also (as Bashing-om) suggested defragged a couple more times.  I haven't been able to run chkdsk, as the command line keeps telling me that I don't have sufficient privileges !

Anyway, after resizing a couple of times more, here's what I've got;

C: 63.22 GB NTFS
Unallocated: 48.56 GB

I'm currently running 14.04 in trial mode from the disc.  I haven't got a screenshot from Gparted, but here are the results given by it:

Partition: /dev/sda1
     File system: ntfs
     Mount point: /media/ubuntu/5A4E1DDC4E1DB1AD
     Size: 63.22 GB
     Used; 19.43 GB
     Unused: 43.80 GB
     Flags: boot

Partition: unallocated
     File system: unallocated
     Size 48.57 GB

[INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-29
> **Raggylad said:**
> Thanks to advice from the sysadmins at work, I've been able to do some Windows housekeeping.  I've also (as Bashing-om) suggested defragged a couple more times.  I haven't been able to run chkdsk, as the command line keeps telling me that I don't have sufficient privileges !

Anyway, after resizing a couple of times more, here's what I've got;

C: 63.22 GB NTFS
Unallocated: 48.56 GB

I'm currently running 14.04 in trial mode from the disc.  I haven't got a screenshot from Gparted, but here are the results given by it:

Partition: /dev/sda1
     File system: ntfs
     Mount point: /media/ubuntu/5A4E1DDC4E1DB1AD
     Size: 63.22 GB
     Used; 19.43 GB
     Unused: 43.80 GB
     Flags: boot

Partition: unallocated
     File system: unallocated
     Size 48.57 GB

[INDENT][/INDENT]

Do you not know the Windows admin password?

There is [a nasty way to change it]("http://askleo.com/ive_lost_the_password_to_my_windows_administrator_account_how_do_i_get_it_back/") but **[COLOR="#FF0000"]don't do it if your Windows data is encrypted!!!!![/COLOR]**

---

### Post by Bashing-om on 2014-08-29
Raggylad; Hey;

Do not recall enough of Windows operations to be of any great assistance.
BUT, you do need to run Windows check disk routine at this time, at least twice.
Then, once the Windows partition table is re- established, install ubuntu.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-30
@Kansasnoob, @Bashing-om,

I have now defragged three times, run chkdsk twice and resized again. I'm still left with the partition sizes I gave above and the same results from GParted.  I reckon that's about as good as it's going to get with my Windows install ?

So is now the time to set about ensuring that I set up a true dual boot (without Wubi) ?

---

### Post by Bashing-om on 2014-08-30
Raggylad; Yepper !

Reboot twice in Windows, make sure Windows is in a happy state .

Ready Set ->

---

### Post by Raggylad on 2014-08-30
> **Bashing-om said:**
> 

Reboot twice in Windows, make sure Windows is in a happy state .

Ready Set ->

Done - it seems happy (!).

---

### Post by Bashing-om on 2014-08-30
Raggylad; OK !

Now it is time to install ubuntu. As you now have some experience with the ubuntu operating system, you may have some preference other than the standard install.

Give some consideration to how you use your system(s) .. maybe making up a separate /home partition and as well a "shared" data partition is in order ?
For reference this is my set up at my level of comprehension:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  1.8G  2.8G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G   12K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  736K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   21M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  1.3G  7.8G  14% /home
/dev/sda8       4.7G  1.6G  2.9G  36% /var
sysop@1404mini:~$

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux
sysop@1404mini:~$

sysop@1404mini:~$ sudo blkid
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
sysop@1404mini:~$

```

As a idea and guide, your use case will be different.

Show us now what we are working with:
post back:
```

sudo fdisk -lu
sudo parted -l

```
and a screen shot of what GParted shows would be real nice.
Then we can discuss this in detail.

Else you are free in the installer to hit "something else" and install away . So long as the Windows partition(NTFS) is not touched in this " something else" environment what ever you do, can be redone if you do not like the results.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-30
@Bashing-om,

Here's the results from those two commands:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   132592559    66295256    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ parted -l
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$
```

Here (I hope !) is the screenshot from Gparted:

/home/ubuntu/Pictures/Screenshot from 2014-08-30 20:28:06.png  [******** !, no it's not.  How do I insert an image that is held in the clipboard of the live disc version of 14.04 ?]

I'm happy with the standard install.  It's an old-ish laptop; I keep the internal HD for OS and software and save all data to an external HD.  I am the only user.  Windows is there only as a backstop - seldom used.

---

### Post by Raggylad on 2014-08-30
@Bashing-om,
Answered my own question - here is a Gparted screenshot:

[ATTACH=CONFIG]255980[/ATTACH]

---

### Post by Bashing-om on 2014-08-30
Raggylad; Hey hey !

Screen shot looks good to me>

I am just a tad bit concerned about:
> 
ubuntu@ubuntu:~$ parted -l
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$


Maybe just because I failed to direct the use of 'sudo" .. try:
```

sudo parted -l

``` to see that the error is not present.
In the event of a standard install as acceptable, I used to advise the option " install along side of", however, presently there is a bug that might effect you also:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)
So we do this in a safer manner, and use the "something else" option and tell the installer what we want.

Select the "unallocated" space and I would suggest the partitioning as:
[LIST]
[*]/ 10Gigs
[*]2 Gigs swap
[*]/home all the remainer
[/LIST]
Drawback, this uses up the allocation of the 4 primary partitions and so does not allow for future additions, Might want to consider making up an "extended partition" to hold both /home and /swap as "logical" partitions", only a bit more complex and does permit greater flexibility. No real reason, but I do prefer to have my '/' (root) partition as a 'primary' partition. I just feel better that-a-way. Rather than also installing it in the 'extended partition.
Watch and make sure the installer installs grub to 'sda' - it should as this is the default.

Nor will it hurt my feelings in the least if you await kansasboob's advise on this and see how he wants to proceed. His mileage may vary .

[INDENT][INDENT][INDENT]we be stepp'n
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-08-30
Bashing-om,

Result from that amended line:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67.9GB  67.9GB  primary  ntfs         boot


Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 
```

Quite late at night here in the UK now, so I'll pause here I think.  If @kansasnoob arrives here while I'm away then the thread will have the benefit of both your expertise.  He alerted me to that bug a while back, which is the main reason I'm proceeding ultra cautiously.

---

### Post by kansasnoob on 2014-08-30
> **Bashing-om said:**
> Raggylad; OK !

Now it is time to install ubuntu. As you now have some experience with the ubuntu operating system, you may have some preference other than the standard install.

Give some consideration to how you use your system(s) .. maybe making up a separate /home partition and as well a "shared" data partition is in order ?
For reference this is my set up at my level of comprehension:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  1.8G  2.8G  39% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G   12K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  736K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   21M  2.0G   2% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda2       9.5G  1.3G  7.8G  14% /home
/dev/sda8       4.7G  1.6G  2.9G  36% /var
sysop@1404mini:~$

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux
sysop@1404mini:~$

sysop@1404mini:~$ sudo blkid
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
sysop@1404mini:~$

```

As a idea and guide, your use case will be different.

Show us now what we are working with:
post back:
```

sudo fdisk -lu
sudo parted -l

```
and a screen shot of what GParted shows would be real nice.
Then we can discuss this in detail.

Else you are free in the installer to hit "something else" and install away . So long as the Windows partition(NTFS) is not touched in this " something else" environment what ever you do, can be redone if you do not like the results.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

I'd suggest with only about 48 GB of free space keeping things very simple, like if things look about like this (just a mock-up so size is not accurate):

[ATTACH=CONFIG]255981[/ATTACH]

Then create a logical SWAP about 4.1 to 4.2 GB at the right end of the unallocated space and use the rest as a primary / partition (aka root) kind of like this:

[ATTACH=CONFIG]255982[/ATTACH]

Then during installation choose Something else and be sure to select the appropriate partition as / like I described here:

[http://ubuntuforums.org/showthread.php?t=2239146&page=6&p=13101695#post13101695](http://ubuntuforums.org/showthread.php?t=2239146&page=6&p=13101695#post13101695)

Of course Raggylad's device designations may be different so you must choose the proper device. Sorry I can't go into more detail right now but I have some heat stressed animals to take care of.

It could be very late tonight or even tomorrow before I get back to this.

---

### Post by kansasnoob on 2014-08-30
> **Raggylad said:**
> Bashing-om,

Result from that amended line:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67.9GB  67.9GB  primary  ntfs         boot


**[COLOR="#FF0000"]Error: Can't have a partition outside the disk! [/COLOR]**                          

ubuntu@ubuntu:~$ 
```

Quite late at night here in the UK now, so I'll pause here I think.  If @kansasnoob arrives here while I'm away then the thread will have the benefit of both your expertise.  He alerted me to that bug a while back, which is the main reason I'm proceeding ultra cautiously.

That **[COLOR="#FF0000"]Error[/COLOR]** will have to be taken care of before we proceed!

We could really use a screenshot from Gparted ;)

---

### Post by Bashing-om on 2014-08-30
Raggylad; Yeah !

Let's wait ! I am not at all happy with:
> 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67.9GB  67.9GB  primary  ntfs         boot


[color=red]Error: Can't have a partition outside the disk![/color] 

as GParted reports the size as - 63.22 - . I can see loosing a little from the 67.9 to housekeeping, but this to me is excessive and reason for concern.
Starting sector at 1049 I wonder as 'fdisk' says 1048, but I do not know why the partition would be listed as " outside the disk " . not good !

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-30
Actually the output of this command would also be very helpful:

```
sudo fdisk -lu
```

I've never seen that happen before as a result of using Windows own partitioning tools.

---

### Post by kansasnoob on 2014-08-30
> **Bashing-om said:**
> Raggylad; Yeah !

Let's wait ! I am not at all happy with:

as GParted reports the size as - 63.22 - . I can see loosing a little from the 67.9 to housekeeping, but this to me is excessive and reason for concern.
Starting sector at 1049 I wonder as 'fdisk' says 1048, but I do not know why the partition would be listed as " outside the disk " . not good !

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

I'm surprised Windows still boots :shock:

---

### Post by Raggylad on 2014-08-30
> **kansasnoob said:**
> Actually the output of this command would also be very helpful:

```
sudo fdisk -lu
```

I've never seen that happen before as a result of using Windows own partitioning tools.

@Kansasnoob,

Here's the result:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   132592559    66295256    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 
```

Windows is booting with no (apparent) problems at all.

---

### Post by Bashing-om on 2014-08-31
Raggylad; Morning to ya !

Are you loosing sleep over this ? .. It is not even daylight yet at your house !

I have been considering, and I have not come up with the why fdisk and parted do not agree, or IF the "" outside the disk " is really important.
But it does make me pause 'till I know better,

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-31
I found some instructions for dealing with that error that are better than anything I could type up:

[http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)

**[COLOR="#FF0000"]EDIT: I'm not sure that's at all helpful!!!![/COLOR]** Stay tuned.

---

### Post by kansasnoob on 2014-08-31
Well I'm at a loss here :(

We do need to fix that error before proceeding so I'd open a new thread with a title like "Error: Can't have a partition outside the disk! after resizing Windows". Then go on to explain what is going on including a link to this thread.

---

### Post by Raggylad on 2014-08-31
> **Bashing-om said:**
> Raggylad; Morning to ya !

Are you loosing sleep over this ? .. It is not even daylight yet at your house !



A bit - but the reason I was up was to take my son to catch the bus for football (soccer in US-speak ?) camp !

---

### Post by kansasnoob on 2014-08-31
I keep thinking about this while I'm doing other things, so time to think out loud .............

Typically when you see that error fdisk -lu (or even fdisk -l) will show that a partitions sector is outside the actual physical range. In other words it can't possibly begin or end where the disc info says it does. Consider what it says [here]("http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk") in step 4, "*Does any partition have an end value larger than the disk size*"?

Then look at the output we're dealing with:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total **[COLOR="#FF0000"]234441648[/COLOR]** sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   **[COLOR="#FF0000"]132592559[/COLOR]**    66295256    7  HPFS/NTFS/exFAT
```

And you can see that's not the case here:

234441648
132592559

And the Windows partition appears to start in the right place - sector  2048.

So fdisk sees no problem but parted does - odd indeed. But look at this comparison on that mock-up disc I was using:

```
##fdisk -lu first:
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047c0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    57346047    28672000    7  HPFS/NTFS/exFAT

##now parted -l
Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  29.4GB  29.4GB  primary  ntfs
```

Now make the same comparison with your info:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   132592559    66295256    7  HPFS/NTFS/exFAT

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  67.9GB  67.9GB  primary  ntfs         boot


Error: Can't have a partition outside the disk!
```

**Absolutely no aha moments in looking at all of that.**

And the Gparted screenshot you posted showed nothing unexpected. Most users don't know that Partition Outside the Disk error even exists until they try creating or resizing a partition ............. or they may get a similar (but slightly different) error message if partitions overlap - something more commonly seen with logical/exteneded partitions which we're not yet dealing with.

So lets see what info Gparted provides - I think the screenshots almost speak for themselves. Right click on the Windows partition and select Info:

[ATTACH=CONFIG]256008[/ATTACH]

It'll display something like this which we should see:

[ATTACH=CONFIG]256009[/ATTACH]

Then repeat for the unallocated space:

[ATTACH=CONFIG]256010[/ATTACH]

We'd expect to see something like this which we should also see:

[ATTACH=CONFIG]256011[/ATTACH]

Are we having fun yet?

---

### Post by Raggylad on 2014-08-31
> **kansasnoob said:**
> Well I'm at a loss here :(

We do need to fix that error before proceeding so I'd open a new thread with a title like "Error: Can't have a partition outside the disk! after resizing Windows". Then go on to explain what is going on including a link to this thread.

@Kansasnoob,

I've opened a new thread as you suggested.  Hope some Windows expert shows up .......

Here's some screenshots from Gparted:

[ATTACH=CONFIG]256015[/ATTACH]

[ATTACH=CONFIG]256016[/ATTACH]

Nothing unexpected ?

Fun ? ..... Oh yes !  So long as we get to a sound install some time.  I'm working off the live disc at the moment ......

---

### Post by kansasnoob on 2014-08-31
> Nothing unexpected ?

Nope ................ she's a puzzler :-k

---

### Post by kansasnoob on 2014-08-31
Going clear back to post #9 we were OK other than the read only error:

```
sudo parted -l
sudo: unable to open /var/lib/sudo/unick/2: Read-only file system
Model: ATA MD01200-AVDW-RO (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ntfs         boot


Model: Seagate Portable (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  ntfs         boot
```

---

### Post by Raggylad on 2014-08-31
Over on the new "Error" thread, @Nadrach has the following suggestion:

> Not sure if I am reading this right, but as far as I remember, on a dual  (or multi) boot system, Windows always has to be the first partition,  Linux goes into the next one. However, there needs to be a partition,  not just free unallocated space.
You appear to have a 120 GB fixed disk of which only 67.9GB is  allocated, and a 250GB portable disk almost all of which is allocated,  in both cases configured as ntfs.
Both partitions start at the beginning of the disk and are Window formatted.
It seems as if you have free space, but not partitioned ready for Linux to load into. It needs a blank partition to work with.
For the dual boot you need to create a blank partition for the Linux to  go into, on the 120GB disk, starting at 132592560 and ending at  234441648 (basically the unallocated space). Run Linux from the USB and  use the disk partition program to do this. Format it anything simple ...  FAT or ext2 will do.
Then run the Linux Install. Tell it to use this blank partition. It will  divide it up for root and swap, reformat it (probably ext4 and swap)  and, as you have with the portable disk, there will probably be a little  left at the top that does not fit the block size (488392128 to  488397168 for the portable). Then it will amend or create a suitable  boot loader to allow you to choose what to load at boot time.                 

Perhaps we just need to format that unallocated space and name it ?  That might explain why in post #09 (when there was no unallocated space - no resizing done) there wasn't an error message ?

---

### Post by Raggylad on 2014-08-31
'Fraid I'll now be offline for about 18 hours.

---

### Post by kansasnoob on 2014-08-31
> **Raggylad said:**
> Over on the new "Error" thread, @Nadrach has the following suggestion:



Perhaps we just need to format that unallocated space and name it ?  That might explain why in post #09 (when there was no unallocated space - no resizing done) there wasn't an error message ?

Parts of that are incorrect :(

But first of all I thought the 250GB drive was disconnected???????

Have you been leaving it connected? I assume it's a USB drive, is that correct?

If it's been connected maybe that's the drive that parted is reading an error on, but then we'd expect to see the fdisk output for that drive in the info you've been posting.

Anyway I'll have a look over there ..................... regarding what's inaccurate in those statements:

> It needs a blank partition to work with.

Not really, if the automated parts of the installer weren't a total mess (therefore not to be trusted) the installer should read the largest free space and offer to install alongside, and what would otherwise be a Continue button in the lower right hand corner of the window will just say Install now. For comparison here's a shot of what alongside looks like with no unallocated space:

[ATTACH=CONFIG]256017[/ATTACH]

And here's what it looks like if it sees any unallocated space it deems large enough:

[ATTACH=CONFIG]256018[/ATTACH]

> Tell it to use this blank partition.

Well, not a good way to describe it ............... you'd have to choose Something else to perform the advanced partitioning, then resize that partition to make room for the additional SWAP partition. But we need to figure out what the cause of that error is before creating any new partitions! It's pointless to build a new home on a faulty foundation!

> It will divide it up for root and swap

There is no part of the automated procedure that does that!!!!!!

But I'll have a look over there ASAP.

Have you had that other drive connected all along? That would have been nice to know.

---

### Post by Raggylad on 2014-09-01
> **kansasnoob said:**
> 

But first of all I thought the 250GB drive was disconnected???????

Have you been leaving it connected? I assume it's a USB drive, is that correct?

If it's been connected maybe that's the drive that parted is reading an error on, but then we'd expect to see the fdisk output for that drive in the info you've been posting.



My mistake.  We _have_ been working with the 250 GB USB drive  disconnected. The external drive is where I keep all data, leaving the smaller internal drive for OS, software, apps,etc.

  I had temporarily reconnected to get some files and  forgot to disconnect before copying the code and posting the OP in that 'Error' thread.  I  noticed this after reading #2 and checked that the original error  message still occurred - it did.

I've corrected the OP. Do you want the external HD connected or not while we work ?

---

### Post by didier5 on 2014-09-01
I also encoutered this issue with 12.04 - I had updated HWE before the 116 soft updates. Wrong idea.
So I started again without touching HWE update.

Nice to play with Unix to patch.
But I prefer to have a clear and reproducable installation.

---

### Post by kansasnoob on 2014-09-01
> **Raggylad said:**
> My mistake.  We _have_ been working with the 250 GB USB drive  disconnected. The external drive is where I keep all data, leaving the smaller internal drive for OS, software, apps,etc.

  I had temporarily reconnected to get some files and  forgot to disconnect before copying the code and posting the OP in that 'Error' thread.  I  noticed this after reading #2 and checked that the original error  message still occurred - it did.

I've corrected the OP. Do you want the external HD connected or not while we work ?

Cool, I figured something like that but wanted to clarify.

---

### Post by kansasnoob on 2014-09-01
> **didier5 said:**
> I also encoutered this issue with 12.04 - I had updated HWE before the 116 soft updates. Wrong idea.
So I started again without touching HWE update.

Nice to play with Unix to patch.
But I prefer to have a clear and reproducable installation.

If by "started again" you mean reinstalling Precise I hope you used [the archived 12.04.1 (or 12.04) image]("http://old-releases.ubuntu.com/releases/12.04.1/") with the 3.2 series kernel ............... otherwise you'll be running an unsupported kernel, and most kernel updates do include security patches:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

---

### Post by Bashing-om on 2014-09-01
kansasnoob; Raggylad; Hey, hey;

See Westie's conclusion in the alternate thread.

[INDENT][INDENT]good work, done well
[/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-09-01
> **Bashing-om said:**
> kansasnoob; Raggylad; Hey, hey;

See Westie's conclusion in the alternate thread.

[INDENT][INDENT]good work, done well
[/INDENT][/INDENT]

I had not even thought about checking the entire drive size, but still I browsed thru Testdisk docs and don't see what to do related to that problem.

---

### Post by Bashing-om on 2014-09-01
kansasnoob; Sorry,

I too lack the familiarity with testdisk to know what to advise.
Our fellow Mark Phelps might have some insight on such a situation ?

Sometimes
[INDENT][INDENT][INDENT]it is not what you know
[INDENT][INDENT][INDENT][INDENT]but who you know, who does know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-09-01
> **Bashing-om said:**
> kansasnoob; Sorry,

I too lack the familiarity with testdisk to know what to advise.
Our fellow Mark Phelps might have some insight on such a situation ?

Sometimes
[INDENT][INDENT][INDENT]it is not what you know
[INDENT][INDENT][INDENT][INDENT]but who you know, who does know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Yep ................. it's OK not to know something, never too old to learn new tricks ;)

---

### Post by Raggylad on 2014-09-02
Of course there is the slight issue that - having removed 12.04 from the computer - I am running on either Windows or a 14.04 live disc.  I've checked when in the latter and testdisk is not installed - nor is Universe enabled (which terminal says that it needs to be for Testdisk) !

---

### Post by Bashing-om on 2014-09-02
Raggylad; Welp:

Not a major obstacle.
In the liveDVD insure the universe and multiverse repositories are enabled;
install testdisk:
```

sudo apt-get install testdisk

```
else for extended use one might consider downloading and burning the bootable testdisk CD.
Then again, Windows may have the tools on-board to repair the file system, here I am unqualified to offer guidance.

one thing for sure, we can not go forward
[INDENT][INDENT][INDENT]'til we are on a solid foundation
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2014-09-07
The issues which were explored in this thread, while not having been resolved, have been bypassed for me by achieving a fresh install as a true dual boot (Windows Vista and Trusty).  The full story is over on this thread:

[http://ubuntuforums.org/showthread.php?t=2242245&page=7](http://ubuntuforums.org/showthread.php?t=2242245&page=7)

With many thanks to all who have helped me - in particular @Bashing-om, @Kansasnoob and @ian-weisser.  I have learned a great deal more about Linux and Ubuntu in the process.

---

### Post by Bashing-om on 2014-09-07
Raggylad; Hey hey ;

Great ! Any solution beats no solution.

Pleasing also you are becoming that much more comfortable with this "our operating system of choice" .

Please mark this thread solved.
Top of post -> thread tools.

I look forward to finding something else to play with next time; but in the interim ->

Ian and Kansas I expect reflect the same attitude.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-09-07
> **Bashing-om said:**
> Raggylad; Hey hey ;

Great ! Any solution beats no solution.

Pleasing also you are becoming that much more comfortable with this "our operating system of choice" .

Please mark this thread solved.
Top of post -> thread tools.

I look forward to finding something else to play with next time; but in the interim ->

Ian and Kansas I expect reflect the same attitude.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

+1!

---

