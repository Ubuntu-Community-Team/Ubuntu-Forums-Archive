---
title: "not able to update the update manager"
date: 2013-12-16
forum: Installation &amp; Upgrades
---

### Post by vikas.180 on 2013-12-16
when i try to update the update manager then i get a error 
**"The upgrade needs a total of 52.6 M free space on disk '/boot'. Please free at least an additional 52.6 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'. " **I am a beginner please help. even when i try and run sudo apt-get install cmake for open cv It says error no disk space. if i have to remove some files from /boot folder then which all files should i remove.

---

### Post by ian-weisser on 2013-12-16
You won't be able to install *anything* until it's fixed.
Happily, it's usually easy.

Open a terminal.
Enter the following commands and paste the complete output of each here. None are dangerous.
```
uname -r
df -h
ls -l /boot
```

---

### Post by vikas.180 on 2013-12-16
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        74G  5.0G   65G   8% /
udev            872M  4.0K  872M   1% /dev
tmpfs           352M  904K  351M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            880M  276K  879M   1% /run/shm
/dev/sda6       184M  180M     0 100% /boot
/dev/sda8        92G  1.1G   86G   2% /home
/dev/sda2        59G   44G   15G  76% /media/DE4A9B2B4A9AFF87

this is the output when i try to run df -h 

how do i increase the memory space of /dev/sda6 , if i can not increase what is the other option (worst case if i have to delete the contents of /boot then which file do i have to keep and which files i have to delete)

---

### Post by ian-weisser on 2013-12-16
Still awaiting the other two outputs. Need those to give you best advice.

You can resize any partition you wish...but I would recommend you know what you are doing before resizing partitions. A wrong choice can lose a lot of your data, or make your system unbootable.
Usually there are easier ways.

---

### Post by vikas.180 on 2013-12-16
vikas@vikas-Pavilion:~$ uname -r
3.5.0-41-generic



vikas@vikas-Pavilion:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        74G  4.8G   65G   7% /
udev            872M  4.0K  872M   1% /dev
tmpfs           352M  924K  351M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            880M  244K  880M   1% /run/shm
/dev/sda6       184M  180M     0 100% /boot
/dev/sda8        92G  1.1G   86G   2% /home


vikas@vikas-Pavilion:~$ ls -l /boot

total 174355
-rw-r--r-- 1 root root   804552 Jul 24 17:44 abi-3.2.0-51-generic-pae
-rw-r--r-- 1 root root   804726 Aug 22 18:27 abi-3.2.0-53-generic-pae
-rw-r--r-- 1 root root   804726 Sep 10 17:32 abi-3.2.0-54-generic-pae
-rw-r--r-- 1 root root   804873 Oct 23 14:54 abi-3.2.0-56-generic-pae
-rw-r--r-- 1 root root   856743 Jan 25  2013 abi-3.5.0-23-generic
-rw-r--r-- 1 root root   861363 Jul 10 14:13 abi-3.5.0-37-generic
-rw-r--r-- 1 root root   861648 Aug 23 14:21 abi-3.5.0-40-generic
-rw-r--r-- 1 root root   861789 Sep 12 13:24 abi-3.5.0-41-generic
-rw-r--r-- 1 root root   147576 Jul 24 17:44 config-3.2.0-51-generic-pae
-rw-r--r-- 1 root root   147576 Aug 22 18:27 config-3.2.0-53-generic-pae
-rw-r--r-- 1 root root   147576 Sep 10 17:32 config-3.2.0-54-generic-pae
-rw-r--r-- 1 root root   147576 Oct 23 14:54 config-3.2.0-56-generic-pae
-rw-r--r-- 1 root root   154436 Jan 25  2013 config-3.5.0-23-generic
-rw-r--r-- 1 root root   154713 Jul 10 14:13 config-3.5.0-37-generic
-rw-r--r-- 1 root root   154713 Aug 23 14:21 config-3.5.0-40-generic
-rw-r--r-- 1 root root   154713 Sep 12 13:24 config-3.5.0-41-generic
drwxr-xr-x 3 root root     7168 Oct 10 11:30 grub
-rw-r--r-- 1 root root 19810183 Aug 12 04:13 initrd.img-3.2.0-51-generic-pae
-rw-r--r-- 1 root root 14200383 Sep 16 00:06 initrd.img-3.2.0-53-generic-pae
-rw-r--r-- 1 root root 14198989 Oct 10 11:30 initrd.img-3.2.0-54-generic-pae
-rw-r--r-- 1 root root 15402386 Aug 12 04:44 initrd.img-3.5.0-23-generic
-rw-r--r-- 1 root root 15539756 Sep 16 00:02 initrd.img-3.5.0-37-generic
-rw-r--r-- 1 root root 15542370 Sep 26 00:37 initrd.img-3.5.0-40-generic
-rw-r--r-- 1 root root 15545033 Oct 10 11:30 initrd.img-3.5.0-41-generic
drwx------ 2 root root    12288 Aug 12 03:47 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2320656 Jul 24 17:44 System.map-3.2.0-51-generic-pae
-rw------- 1 root root  2321335 Aug 22 18:27 System.map-3.2.0-53-generic-pae
-rw------- 1 root root  2321477 Sep 10 17:32 System.map-3.2.0-54-generic-pae
-rw------- 1 root root  2321891 Oct 23 14:54 System.map-3.2.0-56-generic-pae
-rw------- 1 root root  2421090 Jan 25  2013 System.map-3.5.0-23-generic
-rw------- 1 root root  2420011 Jul 10 14:13 System.map-3.5.0-37-generic
-rw------- 1 root root  2421348 Aug 23 14:21 System.map-3.5.0-40-generic
-rw------- 1 root root  2421572 Sep 12 13:24 System.map-3.5.0-41-generic
-rw------- 1 root root  5028224 Jul 24 17:44 vmlinuz-3.2.0-51-generic-pae
-rw------- 1 root root  5028480 Aug 22 18:27 vmlinuz-3.2.0-53-generic-pae
-rw------- 1 root root  5028896 Sep 10 17:32 vmlinuz-3.2.0-54-generic-pae
-rw------- 1 root root  5030080 Oct 23 14:54 vmlinuz-3.2.0-56-generic-pae
-rw-r--r-- 1 root root  5237968 Feb 13  2013 vmlinuz-3.5.0-23-generic
-rw------- 1 root root  5231920 Jul 10 14:13 vmlinuz-3.5.0-37-generic
-rw------- 1 root root  5236048 Aug 23 14:21 vmlinuz-3.5.0-40-generic
-rw------- 1 root root  5236208 Sep 12 13:24 vmlinuz-3.5.0-41-generic
vikas@vikas-Pavilion:~$

---

### Post by ian-weisser on 2013-12-16
Try the following commands:
```
sudo apt-get autoremove linux-image-3.2.0-51-generic-pae
sudo apt-get autoremove linux-image-3.2.0-53-generic-pae
sudo apt-get autoremove linux-image-3.2.0-54-generic-pae
sudo apt-get autoremove linux-image-3.2.0-56-generic-pae
sudo apt-get autoremove linux-image-3.5.0-23-generic
sudo apt-get autoremove linux-image-3.5.0-37-generic
sudo apt-get autoremove linux-image-3.5.0-40-generic
```

Each command will remove an old kernel. It's kind of fun to watch.
One kernel will remain: 3.5.0-41-generic  DO NOT try to remove that one. That's the one you are using. If you remove it, your system will be unbootable.

If you get any errors, stop. Post the entire session here.
If you don't get any errors, then you will have plenty of room in your /boot.

The buildup of old kernels was a bug that was recently fixed. The fix has not yet been backported to older releases of Ubuntu.

---

### Post by vasa1 on 2013-12-17
I find that just **sudo apt-get autoremove** is enough. That leaves me with the current and the immediately previous kernel (just in case): [http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988](http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988)

---

### Post by vikas.180 on 2013-12-17
[SIZE=2][FONT=arial]First of all thanks [SIZE=2][[COLOR=#000000]ian-weisser[/COLOR]]("http://ubuntuforums.org/member.php?u=1841707")[/SIZE][COLOR=#000000][SIZE=2] [/SIZE],  what i have done is that i have kept all the latest versions and moved the old version to a directory in /opt and rebooted the system now i have enough space  and do u think sudo apt-get autoremove still necessary [/COLOR][/FONT][/SIZE]

---

### Post by ian-weisser on 2013-12-17
> **vikas.180 said:**
> [SIZE=2][FONT=arial][COLOR=#000000]i have kept all the latest versions and moved the old version to a directory in /opt and rebooted the system[/COLOR][/FONT][/SIZE]

Don't move files that the package manager installed. Never do that unless you *really* know what you are doing.
You have just broken your ability to remove those old kernels using the package manager.
The package manager still thinks those kernels are installed properly. That can lead to unexpected behavior.

You should undo the move and remove those old and unused kernels the proper way immediately...before you forget how to undo exactly what you did.

---

