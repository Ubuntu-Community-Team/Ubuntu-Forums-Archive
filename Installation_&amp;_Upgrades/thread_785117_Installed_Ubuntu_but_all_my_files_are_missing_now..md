---
title: "Installed Ubuntu but all my files are missing now."
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by stat5bot on 2008-05-07
First time to install UBUNTU 

curious about what Ubuntu looks like, and how it works.. i tried it,

first i got Windows XP. so i installed Ubuntu. then after i restarted the computer. it did not give me any options to choose which OS to boot.. it just went to Ubuntu. then when i check my files. all of my partitions are gone (well, 2 of them C & D) which contains all of my important files) now im having a hard time looking for a way to recover them.. :( 

all i could see here in Ubuntu is FILESYSTEM and thats it.. i dont see any partitions for my previous drives.. :(

anyone help? thanks a lot :)

---

### Post by tamoneya on 2008-05-07
the way you get to choose your os is you hit esc when it says "loading grub".  As for your files they are on a seperate partition that is nice and safe. Post the output of the following code in terminal (applications->accessories->terminal)```
sudo fdisk -l
```

---

### Post by stat5bot on 2008-05-07
> **tamoneya said:**
> the way you get to choose your os is you hit esc when it says "loading grub".  As for your files they are on a seperate partition that is nice and safe. Post the output of the following code in terminal (applications->accessories->terminal)```
sudo fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb17f4837

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

---

### Post by tamoneya on 2008-05-07
Okay you are going to try and remain relaxed because this is going to take some work.  When you installed ubuntu it appears that you told it to use the entire disk and in the process you erased you NTFS partition and therefore your files.  The first thing you shoud do is you should turn of the computer in question and if possible trouble shoot this from a seperate computer.  The reason behind this is that every write to your harddisk decreases the chances that you will recover your files.  From this other computer you should download [RIPLinux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/") (recovery is possible linux).  This will allow you to boot from a liveCD (like you did during the install) and from there recovery your files onto a spare harddrive.

---

### Post by stat5bot on 2008-05-07
by the way sir. i tried to press escape while it was still loading.. it only gave me choices like Ubuntu 8.04 Generic, Recovery Mode & Memtest.. :(

---

### Post by tamoneya on 2008-05-07
that is because as i said earlier you installed over your windows partition instead of along with it.  You told ubuntu to remove windows and therefore it wont show up in grub :(

---

### Post by stat5bot on 2008-05-07
aw.. :(

thanks a lot. im currently downloading the file. but unfortunately i dont have another computer. is it ok if i could boot it using the same computer?.

and im really sorry, im really new to this. how do you burn the.. image file into the CD.. i only know how to do it in Norton..sorry :(

---

### Post by tamoneya on 2008-05-07
testdisk seems to be a little bit more up to date.  Try this instead of RIPLinux
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
edit: ignore this.  Test disk is included on recovery is possible.  It is testdisk that you should be running once you load recovery is possible.

---

### Post by tamoneya on 2008-05-07
ubuntu will automatically detect that it is an ISO and it will just open the burn cd/dvd program.  If that doesnt happen it is called Brasero and is located in applications -> sound and video.  You should try to find some sort of external drive or even a flash drive to which you can transfer your hopefully soon to be recovered files.

---

