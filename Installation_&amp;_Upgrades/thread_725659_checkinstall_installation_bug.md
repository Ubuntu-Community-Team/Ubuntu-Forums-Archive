---
title: "checkinstall installation bug"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by NeoParabola on 2008-03-15
I had a bug while installing checkinstall. I been asked if I want to delete some packages no longer required and I answered Yes. Now my hda1 is no longer accessible. How can I fix this? Here is a example of an installation of checkinstall from one of my friend. 


gagle@gagle-laptop:~$ sudo apt-get install checkinstall
[sudo] password for gagle:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gagle@gagle-laptop:~$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-qt3 python-sip4 libxine1-gnome libgd2-xpm libgraphviz3 graphviz
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116kB of archives.
After unpacking, 557kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  checkinstall
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116kB of archives.
After unpacking, 557kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  checkinstall
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated


I've purged checkinstall and I reinstalled the missing package in;  python-qt3 python-sip4 libxine1-gnome libgd2-xpm libgraphviz3 graphviz , whit synaptic but I still have the same problem. Any Idea!?

Thx, -Phil

---

### Post by mikewhatever on 2008-03-16
Do you get any errors trying to access hda1? Also, post the following info: <sudo fdisk -l> ,<cat /etc/fstab>.

---

### Post by NeoParabola on 2008-03-16
The hda1 link is missing on my desktop and the /media/hda1 folder is empty. Here are the others info tou requested: 

parabola@parabola-desktop:~$ sudo fdisk -l
[sudo] password for parabola:

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x53110b4d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16455   132174756    7  HPFS/NTFS
/dev/hda2           16456       19798    26852647+  83  Linux
/dev/hda3           19799       19929     1052257+  82  Linux swap / Solaris

parabola@parabola-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=dfd037a4-f874-4f5c-a059-9d45c2abbd18 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=A0DC65ABDC657C82 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=893b6c8f-d3dd-471d-8c67-f964517a0bc3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Thx!

---

### Post by NeoParabola on 2008-03-16
One more thing, I've tried to mount hda1 manually and I've got the following error message 

ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error

When I boot, I have a sequence of error message for 250 second like this one:

Buffer I/O error on device hda1, logical block XXXXXXXX 
Buffer I/O error on device hda1, logical block XXXXXXXX
Buffer I/O error on device hda1, logical block XXXXXXXX (.....)


where X are nubers....

---

### Post by NeoParabola on 2008-03-16
New info : 

I cannot boot hda1 partition, even in safe mode, and GParted is unable to read hda1 partition too. I'm pretty scared right now... Please give me some hope!

---

### Post by mikewhatever on 2008-03-17
I don't know if the removed packages had anything to do here. It looks more like ntfs filesystem error.

---

### Post by NeoParabola on 2008-03-17
Problem solved! I dont understand how nor why nor when it happened but my hda1 partition crashed and it might effectively not be related to checkinstall... only a coinsidence. Whatever, I run Hiren's boot CD and successfully repair 29 error block and my partition is back to life. However, windows is still not accessible which is far from beeing a problem. Thx for your help !

Phil

---

