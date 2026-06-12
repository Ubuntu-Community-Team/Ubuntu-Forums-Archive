---
title: "Dual Boot Ubuntu 12.04 with Windows 8.1 SSD"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by leland.chow on 2014-03-29
Hi everyone. I tried to find information on how to dual boot ubuntu 12.04 with Windows 8.1, but all I got is either HDD or hybrid, which isn't SSD. Is it the same way as HDD? If not, could anyone kindly tell me how to do so? :)

Thanks in advance :D

---

### Post by fantab on 2014-03-29
I suggest you go through these first:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]http://ubuntuforums.org/showthread.php?t=2147295
[/URL]
Post the hardware details of you computer, especially, Graphics Card, RAM, CPUl, HDD etc..
Post a screenshots of your Hard Disk Drive taken from 'Windows Disk Utility' showing all the drives and partitions.

Welcome to the world of Linux!

Remember [Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm").

---

### Post by leland.chow on 2014-03-29
Hardware details:
[IMG]http://i61.tinypic.com/jjn0o9.png[/IMG]

SSD Drive and Partitions:
[IMG]http://i57.tinypic.com/34goz82.png[/IMG]

---

### Post by fantab on 2014-03-29
I assume you have make a Ubuntu install DVD/USB. Boot with it and "Try Ubuntu [Without installing], desktop will load. Open Terminal [Ctrl+alt+T], and run the following commands in it. Post the output of the commands here:
```
sudo parted -l
sudo fdisk -l
```

Before installing Ubuntu we may have to disable IntelSRT, 'Fast Startup', and 'Fastboot', and 'Secure Boot'. Though disabling Secure Boot is not a must, but adviced. See the links I posted earlier to get more details...

---

### Post by oldfred on 2014-03-31
Since it is a very new Lenovo with Intel Haswell, I might suggest 14.04. While it is not officially released and they are working on last minute bugs, many with Haswell systems find the kernel, system files & video driver updates are really needed for it to work well with a Haswell based system.

---

