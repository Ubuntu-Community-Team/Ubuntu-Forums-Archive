---
title: "Disk boot failure insert system disk and press enter"
date: 2017-10-08
forum: Installation &amp; Upgrades
---

### Post by kostepanych2 on 2017-10-08
I tried to install [COLOR=#000000][FONT=&amp]ubuntu 16.04 64-bit to the very old hdd [/FONT][/COLOR][COLOR=#000000][FONT=&amp]Samsung SV0211H 20Gb.
After installation and reboot there is error message: [/FONT][/COLOR]DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER.

Here is [COLOR=#000000][FONT=&amp]sudo fdisk -l: 
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]




[COLOR=#000000][FONT=&amp]Disk /dev/sda: 18.7 GiB, 20060135424 bytes, 39179952 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Disklabel type: dos[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Disk identifier: 0x3073fe13[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]Device     Boot    Start      End  Sectors  Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda1  *        2048 34990079 34988032 16.7G 83 Linux[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda2       34992126 39178239  4186114    2G  5 Extended[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sda5       34992128 39178239  4186112    2G 82 Linux swap / Solaris[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]
What can I do with that?[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-10-08
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

Is it just the hard disk that's old or is the whole computer containing it also old; perhaps the computer is missing some hardware abilities, eg incompatible CPU, if it is very old.

---

### Post by oldos2er on 2017-10-08
Did you reset the BIOS to boot from hard disk? 

What are the hardware specs of this computer?

---

