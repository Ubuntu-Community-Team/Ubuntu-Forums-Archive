---
title: "[SOLVED] Installation on pc with 2 Hard disks"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by squidboy67 on 2008-03-22
Hi,

ubuntu 7.10 desktop on a e2180 msi p35 neo 2gb memory and 2 X 250Gb drives

drives are empty...no windows software anywhere. No requirement to dual boot.


My question/problem.... During install from the live cd it will only use the first disk. When I get into the os once its setup I can see the second disk and partition it format it etc

However every time I want to use it I need to enter my password, I have tried the chown command and get no change of security rights..

What I want here is OS and swap as it is on the first disk and I want the second disk to be my storage area, mounted every time I start. Changes to fstab for mounts etc still seem to have problems with the fact I dont own the disk.

Any help appreciated

---

### Post by kyphi on 2008-03-22
If you have a look at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
you will find a step by step description of how to mount your drive.

The article was written for mounting Ubuntu as well as Windows but the principle is the same as if it was written for Ubuntu and Ubuntu.

---

### Post by Bruce M. on 2008-03-22
> **squidboy67 said:**
> Hi,

ubuntu 7.10 desktop on a e2180 msi p35 neo 2gb memory and 2 X 250Gb drives

drives are empty...no windows software anywhere. No requirement to dual boot.


My question/problem.... During install from the live cd it will only use the first disk. When I get into the os once its setup I can see the second disk and partition it format it etc

However every time I want to use it I need to enter my password, I have tried the chown command and get no change of security rights..

What I want here is OS and swap as it is on the first disk and I want the second disk to be my storage area, mounted every time I start. Changes to fstab for mounts etc still seem to have problems with the fact I dont own the disk.

Any help appreciated

Check out:  [Need to change permissions for second HD]("http://ubuntuforums.org/showthread.php?t=721112")

---

### Post by logos34 on 2008-03-22
> **squidboy67 said:**
> drives are empty...no windows software anywhere. No requirement to dual boot.

... During install from the live cd it will only use the first disk. When I get into the os once its setup I can see the second disk and partition it format it etc

However every time I want to use it I need to enter my password, I have tried the chown command and get no change of security rights..


If you formatted it ext3, then you need to run chmod -R 777 /media/<drive> and chown -R username:username /media/<drive>

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(->bottom)

---

### Post by squidboy67 on 2008-03-23
Right on the nail logos34

So to recap on solution : I have a machine with 2 drives, I scrub partitions from both disks, I do my install, I run Gparted and create new partition on second disk, I then get my uuid with ls /dev/disk/by-uuid/ -alh and update my /etc/fstab. I now have a 2nd disk that mounts every boot but no rights to it.

I then use run chmod -R 777 /media/<drive> and chown -R username:username /media/<drive> and thats it working as I need.

Many thanks and case closed

---

