---
title: "Edgy 6.10 failing to mount things straight after install"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by AndyC_772 on 2007-03-03
Hi all

I decided the other day to wipe my Ubuntu drive, repartition it and do a clean install of Edgy 6.10.

I have a Matrox G400 video card, which means the regular install CD simply won't run because of the unresolved Xserver bug that affects Matrox users. So, I installed using the alternate CD in text mode instead.

Following installation and reboot, the X server still fails to start, so I have to install the patched driver: xserver-xorg-video-mga_1.4.4.dfsg.1-1jdong1~6.10prevu1_i386.deb - and then dpkg-reconfigure xserver-xorg to set it up properly. Following a reboot, I do at least get an X desktop.

The problem then, is that none of my hard discs get icons on the background. Also, if I update my /etc/fstab to automatically mount the shares on my NAS drive, they take absolutely ages (several minutes per share) to mount. (The NAS itself is fine, my laptop - also running Ubuntu - can mount it in moments).

I have two physical hard drives - the IDE master is split into two equal halves and has Windows 2000 on one of them. The IDE slave was repartitioned by the Edgy installer and is mostly ext3 with a small swap partition.

All I've done since the install, change of MGA driver and xserver configuration is edit my /etc/fstab - to try and fix the auto mount problem and to add my NAS shares:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=6c6f8581-3261-4891-b147-fca67fe31105 /               ext3    rw,errors=remount-ro 0       1
# /dev/hdb5
UUID=91ba8a8b-51dc-4e03-9794-3a31ae3a301f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

192.168.1.201:/media /mnt/media nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.201:/photos /mnt/photos nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.201:/docs /mnt/docs nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.201:/downloads /mnt/downloads nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.201:/discs /mnt/discs nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.201:/backup /mnt/backup nfs rsize=8192,wsize=8192,timeo=14,intr,ro
192.168.1.201:/upload /mnt/upload nfs rsize=8192,wsize=8192,timeo=14,intr

```

Any ideas before the machine goes out the window please? I had no problems before the reinstall, having upgraded to Edgy from Dapper which worked fine.

---

### Post by AndyC_772 on 2007-03-04
So... just give up and scrap the PC then? If even a fresh, clean install doesn't work... :confused:

---

### Post by chewearn on 2007-03-04
Instead of using fstab to mount your network drives, how about simply using 
Places -> Connect to Server...

I'am using Edgy as well; when I connect to my NAS via "Connect to server", the icon to the server appeared on the desktop.  This icon is persistent and did not go way even after reboot.

---

### Post by Jussi01 on 2007-03-04
hmmm, are they samba shares on the NAS? have you instlled samba? the fstab needs to look a little different if you need samba shares...

---

### Post by AndyC_772 on 2007-03-04
The NAS supports both Samba and NFS; the latter is faster and preserves permissions and attributes properly, so that's what I prefer to use.

Oddly, it does eventually mount the NAS - it just takes ages, whereas my laptop (and desktop, prior to the reinstall) mounted it almost immediately.

EDIT: I fixed the NAS problem, it just needed Portmap installing.

I still have no HDD icons on the desktop or under the 'Places' menu. Any ideas please?

---

