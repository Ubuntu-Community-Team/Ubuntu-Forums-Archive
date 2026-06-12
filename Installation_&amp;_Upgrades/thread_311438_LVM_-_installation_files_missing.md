---
title: "LVM - installation files missing?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by navilon on 2006-12-02
I just installed Ubuntu 6.10 Server on an extra machine
I needed LVM on that computer so I installed it with the following command..
```
sudo apt-get install lvm2
```
which resulted in this..
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  lvm-common mdadm
Suggested packages:
  dmsetup
Recommended packages:
  mail-transport-agent
The following NEW packages will be installed:
  lvm-common lvm2 mdadm
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 469kB of archives.
After unpacking 1479kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com edgy/main mdadm 2.4.1-6ubuntu5 [152kB]
Get:2 http://us.archive.ubuntu.com edgy/main lvm-common 1.5.20ubuntu7 [16.9kB]
Get:3 http://us.archive.ubuntu.com edgy-updates/main lvm2 2.02.06-2ubuntu3.2 [300kB]
Fetched 469kB in 2s (227kB/s)
Preconfiguring packages ...
Selecting previously deselected package mdadm.
(Reading database ... 16034 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_2.4.1-6ubuntu5_i386.deb) ...
Selecting previously deselected package lvm-common.
Unpacking lvm-common (from .../lvm-common_1.5.20ubuntu7_i386.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.06-2ubuntu3.2_i386.deb) ...
Setting up mdadm (2.4.1-6ubuntu5) ...
Generating mdadm.conf... done.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-server
 * Starting RAID monitoring service mdadm --monitor                      [ ok ]

Setting up lvm-common (1.5.20ubuntu7) ...

Setting up lvm2 (2.02.06-2ubuntu3.2) ...
Backing up any LVM2 metadata that may exist...done.
```

Looking pretty good from here, but when i try to run the first command..
```
sudo pvcreate /dev/hdb
```
i get this..
```
 No program "pvcreate" found for your current version of LVM
```

why didn't **pvcreate** get installed?

---

### Post by typhoon476 on 2007-01-28
hi mate,

just run into the same problem. dunno what's causing the system to behave that way but i found a way to correct it. 

Problem:

Installed lvm2 using the packager manager, but when you run one of the binaries you get: 

```
:~$ pvcreate 
No program "pvcreate" found for your current version of LVM
```

or similar depending on the lvm command you entered.

I used strace to see what happened during the execution and saw that it looked to all the wrong places.

```
open("/dev/lvm", O_RDONLY)              = -1 ENOENT (No such file or directory)
stat64("/lib/lvm-0/vgchange", 0xbfaf0130) = -1 ENOENT (No such file or directory)
execve("/lib/lvm-0/pvcreate", ["pvcreate"], [/* 30 vars */]) = -1 ENOENT (No such file or directory)
write(2, "No program \"pvcreate\" found for "..., 60No program "pvcreate" found for your current version of LVM
) = 60
exit_group(99)                          = ?
Process 14602 detached
```

Solution:

Copy the iinstalled files to the place the binaries are really looking for:

```
:~$ sudo cp -r /lib/lvm-200/ /lib/lvm-0
```

Running the commands now should work nicely.

Hope this helps others too.


Cheers from Turkey!

---

### Post by fitzhugh on 2007-02-11
Worked for me - thanks from Berkeley to Turkey!

---

### Post by SosoKoba on 2007-04-11
Thank you typhoon476 

That worked perfectly for me, Have an Efes or dort on me :-)

Tessekur edirim

---

### Post by wolf08 on 2007-07-04
Thanks, this worked for me on 7.04

---

### Post by grimdestripador on 2007-07-20
I came here, looking for exactly your answer. 
It was on the 2 or 3rd google page when searched for "ubuntu feisty pvcreate"

But definitely thanks.

---

### Post by qaball on 2007-08-24
typhoon476

I just did a new install and ran into the same problem with lvm.  My install was from the ubuntu server cd but since I didn't use lvm for my base drive, it never got installed.  After installing I hit the wall all of the other folks on this post did and luckily found your instructions.  Well Done and Thanks!!!

qaball

---

