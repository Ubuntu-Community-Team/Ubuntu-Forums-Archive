---
title: "Problems with mounting shares at bootup"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by MrSam on 2006-06-15
I'm still haveing trouble with getting the shares from my file server to mount properly at bootup.

My file server is running on Centos and my other computers can see the drives there with no problems. I heard about Ubuntu and thought I'd take a look at it and have been having trouble getting these drives mounted ever since.

I can see the drives in the Network Servers and mount them manually from there and they are rw but don't show up in the file system when I need to load a file in a program like mplayer. If I auto mount them at bootup by editing my fstab they mount but are read only and are assigned as u=root, g=root and I can't change the permissions so I can save anything to them. I tried adding a dmask and fmask to the fstab lines but then they didn't mount at all.

I have checked the permissions on the file server and they are set to allow writes so this is coming from something in the mount proceedure when I boot Ubuntu.

Here is a copy of my current fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.0.25/LDrive2 /media/smbmnt1 smbfs credentials=/root/.smbcredentials  0    0
//192.168.0.25/Sata1 /media/smbmnt2 smbfs credentials=/root/.smbcredentials  0    0
//192.168.0.25/Sata2 /media/smbmnt3 smbfs credentials=/root/.smbcredentials  0    0
```

---

### Post by acehigh on 2006-06-15
Hi, 
Try to give a look at [this]("http://ubuntuforums.org/showthread.php?t=184428")  and see if it helps.

---

