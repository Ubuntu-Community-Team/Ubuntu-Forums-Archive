---
title: "unplug ubuntu disk, can't boot winxp disk"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by six648 on 2010-08-22
WinXp sp3 is on disk sdb, then installed Ubuntu 10.04 on sda, 
can go into diff OS without any problem. 
I am going to move sda to another machine, 
when I unplug sda, 
WinXp can't start to boot on sdb. How to fix it?
Thx
---
below is my case output
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB
...
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150253568   83  Linux
/dev/sda2           18706       19458     6034433    5  Extended
/dev/sda5           18706       19458     6034432   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 
...
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2742    22025083+   7  HPFS/NTFS
/dev/sdb4            4250       15144    87514087+   f  W95 Ext'd (LBA)
/dev/sdb5            5245       11618    51199123+   7  HPFS

---

### Post by presence1960 on 2010-08-22
with the disk which has ubuntu unplugged or removed from the case boot the ubuntu 10.04 live cd. Boot to the desktop and open a terminal and run ```
sudo apt-get install lilo
```This will install lilo to the live cd session. Next in terminal run ```
sudo lilo -M /dev/sda mbr
```Ignore any warnings when running those commands and proceed. When both commands are executed reboot without the live cd and you should boot to windows.

If you do not boot to windows do the following with the ubuntu disk still unplugged:
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by six648 on 2010-08-22
it works after installed lilo on Windows disk, Many thanks!

---

