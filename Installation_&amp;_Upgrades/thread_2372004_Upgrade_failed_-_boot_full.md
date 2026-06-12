---
title: "Upgrade failed - /boot full"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2017-09-20
The upgrade failed, below is the list.  Don't understand, there are only 2 files that are not rc.
```

ron@Cronluath:~$ uname -r
4.4.0-93-generic
ron@Cronluath:~$ sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                Architecture           Description
+++-==================================-======================-======================-==========================================================================
un  linux-image                        <none>                 <none>                 (no description available)
un  linux-image-4.2.0-34-generic       <none>                 <none>                 (no description available)
rc  linux-image-4.4.0-28-generic       4.4.0-28.47            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic       4.4.0-31.50            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic       4.4.0-34.53            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic       4.4.0-36.55            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic       4.4.0-38.57            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic       4.4.0-42.62            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic       4.4.0-43.63            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic       4.4.0-45.66            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic       4.4.0-47.68            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic       4.4.0-51.72            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic       4.4.0-53.74            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic       4.4.0-59.80            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic       4.4.0-62.83            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-63-generic       4.4.0-63.84            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic       4.4.0-64.85            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-65-generic       4.4.0-65.86            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic       4.4.0-66.87            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-70-generic       4.4.0-70.91            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-71-generic       4.4.0-71.92            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-72-generic       4.4.0-72.93            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-75-generic       4.4.0-75.96            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-77-generic       4.4.0-77.98            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-78-generic       4.4.0-78.99            amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generic       4.4.0-79.100           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-81-generic       4.4.0-81.104           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generic       4.4.0-83.106           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generic       4.4.0-87.110           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generic       4.4.0-89.112           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generic       4.4.0-91.114           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic       4.4.0-92.115           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-93-generic       4.4.0-93.116           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic       4.4.0-96.119           amd64                  Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic 4.2.0-34.39            amd64                  Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-generic 4.4.0-28.47            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic 4.4.0-31.50            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic 4.4.0-34.53            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic 4.4.0-36.55            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic 4.4.0-38.57            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic 4.4.0-42.62            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic 4.4.0-43.63            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic 4.4.0-45.66            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic 4.4.0-47.68            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic 4.4.0-51.72            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic 4.4.0-53.74            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic 4.4.0-59.80            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic 4.4.0-62.83            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-generic 4.4.0-63.84            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic 4.4.0-64.85            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-65-generic 4.4.0-65.86            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic 4.4.0-66.87            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-70-generic 4.4.0-70.91            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-71-generic 4.4.0-71.92            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic 4.4.0-72.93            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic 4.4.0-75.96            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-77-generic 4.4.0-77.98            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-78-generic 4.4.0-78.99            amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic 4.4.0-79.100           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-81-generic 4.4.0-81.104           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-generic 4.4.0-83.106           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-generic 4.4.0-87.110           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-generic 4.4.0-89.112           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic 4.4.0-91.114           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-generic 4.4.0-92.115           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-93-generic 4.4.0-93.116           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic 4.4.0-96.119           amd64                  Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                4.4.0.96.101           amd64                  Generic Linux kernel image
ron@Cronluath:~$ sudo apt remove linux-image-4.4.0-28-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-4.4.0-28-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ron@Cronluath:~$ 

```

Question 2:  I have a recurring cups error.  How can I capture the apport error window in order to post?

---

### Post by Alligator on 2017-09-20
```

ron@Cronluath:~$ cd /boot
ron@Cronluath:/boot$ ls -la
total 246500
drwxr-xr-x  4 root root     6144 Sep 20 07:37 .
drwxr-xr-x 25 root root     4096 Sep 20 07:24 ..
-rw-r--r--  1 root root  1247269 Aug 11 17:40 abi-4.4.0-93-generic
-rw-r--r--  1 root root  1249161 Sep 12 11:59 abi-4.4.0-96-generic
-rw-r--r--  1 root root   190356 Aug 11 17:40 config-4.4.0-93-generic
-rw-r--r--  1 root root   190517 Sep 12 11:59 config-4.4.0-96-generic
drwxr-xr-x  5 root root     8192 Sep 20 07:37 grub
-rw-r--r--  1 root root  9967188 Sep  8 12:29 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  9967074 Sep  8 12:29 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  9967090 Sep  8 12:28 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  9967060 Sep  8 12:28 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  9967207 Sep  8 12:28 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  9967061 Sep  8 12:28 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  9967058 Sep  8 12:28 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  9967062 Sep  8 12:28 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  9967200 Sep  8 12:28 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  9967184 Sep  8 12:28 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  9967187 Sep  8 12:28 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  9967057 Sep  8 12:28 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  9967093 Sep  8 12:27 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  9967075 Sep  8 12:27 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root  9967039 Sep  8 12:27 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 38227272 Sep  8 12:27 initrd.img-4.4.0-93-generic
-rw-r--r--  1 root root 38226395 Sep 20 07:37 initrd.img-4.4.0-96-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3885811 Aug 11 17:40 System.map-4.4.0-93-generic
-rw-------  1 root root  3886723 Sep 12 11:59 System.map-4.4.0-96-generic
-rw-------  1 root root  7097296 Aug 11 17:40 vmlinuz-4.4.0-93-generic
-rw-------  1 root root  7101968 Sep 12 11:59 vmlinuz-4.4.0-96-generic
ron@Cronluath:/boot$ 

```

---

### Post by oldfred on 2017-09-20
Have you run this?
 -s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 

But if you did not do that before upgrade, you may have all those old kernels & related files for all the old install that now are not in dpkg to normally remove. Then there are multiple places to houseclean files besides just /boot.

Is this an LVM or full drive encrypted install?
      
 [https://ubuntuforums.org/showthread.php?t=2361761](https://ubuntuforums.org/showthread.php?t=2361761)
/boot full or Not enough disk space on updates
[http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808](http://ubuntuforums.org/showthread.php?t=2308938&p=13418808#post13418808)
[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by ajgreeny on 2017-09-20
Let's see the output of command ```
df -h
``` which may give us a few more clues.
It may also be useful to see output from ```
df -i
``` as I wonder if you have a lot of linux-headers packages that have not been removed; these use a huge number of inodes of the filesystem so it's possible you may have run out of inodes rather than space.

Finally have you tried command ```
sudo apt autoremove
``` which, even if it is unsuccessful, will tell us a lot about what is in your filesystem but probably ought to be removed.

---

### Post by ian-weisser on 2017-09-20
Those 14  initrd.img-3* files in /boot seem a likely culprit.
If you are running a 4.* kernel, then those 3.* initrd files can be safely deleted.

Normally, I would recommend against using 'rm' on anything in /boot...but you have already done the dilligence.

---

### Post by Alligator on 2017-09-20
```

ron@Cronluath:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M   18M  767M   3% /run
/dev/md0        720G  317G  367G  47% /
tmpfs           3.9G   39M  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  248M   66M  80% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M  116K  785M   1% /run/user/1001
tmpfs           785M   80K  785M   1% /run/user/1000
/dev/sdb2       661G  5.1G  656G   1% /media/ron/Data
ron@Cronluath:~$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             998898     552   998346    1% /dev
tmpfs           1003984     905  1003079    1% /run
/dev/md0       47947776 1153099 46794677    3% /
tmpfs           1003984      69  1003915    1% /dev/shm
tmpfs           1003984       6  1003978    1% /run/lock
tmpfs           1003984      18  1003966    1% /sys/fs/cgroup
/dev/sdb1         88352     323    88029    1% /boot
cgmfs           1003984      14  1003970    1% /run/cgmanager/fs
tmpfs           1003984      51  1003933    1% /run/user/1001
tmpfs           1003984      41  1003943    1% /run/user/1000
/dev/sdb2             0       0        0     - /media/ron/Data

```

```

ron@Cronluath:~$ sudo apt autoremove
[sudo] password for ron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by oldfred on 2017-09-20
If you have to manually delete old kernels you need to check multiple places.

 Use dpkg -S to see which .dkms files were not placed by the package manager
dpkg -S /full/path/to/file
Only use rm on files not in dpkg
dpkg -S /lib/modules | sed s/:.\*//
uname --kernel-release
 Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 /var/cache/apt/archives
kernel house clean
/usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)
in /boot by version: abi, config, initrd.img, vmlinuz

---

### Post by Alligator on 2017-09-21
Not sure what to do with the above, need more details.  I've forgotten far too much.  Also, a light came on, I have a RAID 1 system, mirroring linux on a second 1T hd.  That may be the problem?

---

### Post by Alligator on 2017-09-25
I'm back.  I read the links and made a couple of changes to auto updates and to 50unattended-upgrades.  Thank you.

---

### Post by asgharisajjad on 2017-09-29
Hi @Alligator,
I have almost the same error, Could you please let me know what changes you made?
Thank you,
Best.

---

