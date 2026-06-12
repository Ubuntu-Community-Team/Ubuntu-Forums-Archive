---
title: "Trusty to Xenial Xerus"
date: 2017-05-12
forum: Installation &amp; Upgrades
---

### Post by ewuntu on 2017-05-12
Greetings to one and all. HELP.
Trying to upgrade Trusty 14.04 to Xenial Xerus LTS via the Software Updater.
Midstream this dialog box popsup "   	 	 	 	   The upgrade has aborted. The upgrade needs a total of 138 M free space on disk '/boot'. Please free at least an additional 6,159 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
Ran sudo apt-get clean and sudo apt-get autoremove. The trash bin is empty.
Still getting the same box.
Thanks in advance

---

### Post by ian-weisser on 2017-05-12
Well, what do you have on /boot, and how much space is it taking up?
Use the 'ls -l' and 'df' commands for easy answers to those questions.

Tip: DON'T use 'rm' on files in /boot. Files in /boot are placed by the package manager. Use apt to remove the appropriate package.

---

### Post by ewuntu on 2017-05-13
```
qx24z@qx24z-ET1161-05:~$ ls -l
total 76
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Desktop
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Documents
drwxr-xr-x 3 qx24z qx24z 4096 May 12 17:36 Downloads
-rw-r--r-- 1 qx24z qx24z 8980 May  9 13:14 examples.desktop
-rw-rw-r-- 1 qx24z qx24z 2380 Jun 18  2010 getdeb-repository_0.1-1~getdeb1_all.deb
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Music
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Pictures
-rw-rw-r-- 1 qx24z qx24z 2244 Jun 18  2010 playdeb_0.3-1~getdeb1_all.deb
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Public
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Templates
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Videos
qx24z@qx24z-ET1161-05:~$ df
Filesystem           1K-blocks    Used Available Use% Mounted on
udev                   1841456       4   1841452   1% /dev
tmpfs                   378772    1696    377076   1% /run
/dev/dm-1             72609064 7352680  61545000  11% /
none                         4       0         4   0% /sys/fs/cgroup
none                      5120       0      5120   0% /run/lock
none                   1893848     156   1893692   1% /run/shm
none                    102400      56    102344   1% /run/user
/dev/sda1               240972   99610    128921  44% /boot
/home/qx24z/.Private  72609064 7352680  61545000  11% /home/qx24z
```

Ian
hope this answers your queries. The swap file was created by the installation disc.

---

### Post by wildmanne39 on 2017-05-13
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ewuntu on 2017-05-13
Ian
re your Tip: DON'T use 'rm' on files in /boot. Files in /boot are placed by the  package manager. Use apt to remove the appropriate package. 				

Don't know what to remove or where to remove it from.

Wildmanne 39
```

 ls -l
total 76
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Desktop
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Documents
drwxr-xr-x 3 qx24z qx24z 4096 May 12 17:36 Downloads
-rw-r--r-- 1 qx24z qx24z 8980 May  9 13:14 examples.desktop
-rw-rw-r-- 1 qx24z qx24z 2380 Jun 18  2010 getdeb-repository_0.1-1~getdeb1_all.deb
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Music
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Pictures
-rw-rw-r-- 1 qx24z qx24z 2244 Jun 18  2010 playdeb_0.3-1~getdeb1_all.deb
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Public
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Templates
drwxr-xr-x 2 qx24z qx24z 4096 May  9 13:24 Videos

```
```

 df
Filesystem           1K-blocks    Used Available Use% Mounted on
udev                   1841456       4   1841452   1% /dev
tmpfs                   378772    1696    377076   1% /run
/dev/dm-1             72609064 7352680  61545000  11% /
none                         4       0         4   0% /sys/fs/cgroup
none                      5120       0      5120   0% /run/lock
none                   1893848     156   1893692   1% /run/shm
none                    102400      56    102344   1% /run/user
/dev/sda1               240972   99610    128921  44% /boot
/home/qx24z/.Private  72609064 7352680  61545000  11% /home/qx24z

```

---

### Post by wildmanne39 on 2017-05-13
@ewuntu, why are you posting the same information over and over? you can bump your thread once every 12 hours only, please stop.
Thanks

---

### Post by deadflowr on 2017-05-13
I think it meant to run the ls -l command for the /boot partition.
like
```
ls -l /boot
```
no sense running it for Home...

---

### Post by ewuntu on 2017-05-13
```

ls -l /boot
total 90729
-rw-r--r-- 1 root root  1273095 Jan 13 11:52 abi-3.19.0-80-generic
-rw-r--r-- 1 root root  1246246 Apr 20 08:53 abi-4.4.0-75-generic
-rw-r--r-- 1 root root   177856 Jan 13 11:52 config-3.19.0-80-generic
-rw-r--r-- 1 root root   190222 Apr 20 08:53 config-4.4.0-75-generic
drwxr-xr-x 5 root root     1024 May 10 19:00 grub
-rw-r--r-- 1 root root 31884275 May  9 21:34 initrd.img-3.19.0-80-generic
-rw-r--r-- 1 root root 36097803 May 10 18:56 initrd.img-4.4.0-75-generic
drwx------ 2 root root    12288 May  9 13:01 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3633374 Jan 13 11:52 System.map-3.19.0-80-generic
-rw------- 1 root root  3896793 Apr 20 08:53 System.map-4.4.0-75-generic
-rw------- 1 root root  6595152 Jan 13 11:52 vmlinuz-3.19.0-80-generic
-rw------- 1 root root  6985424 Apr 20 08:53 vmlinuz-4.4.0-75-generic

```

---

