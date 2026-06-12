---
title: "cannot mount samba windows share (fstab)"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by matt91 on 2006-10-28
since updating to dapper i cannot mount windows network shares. i had a problem with the samba package which i fixed and reinstalled. when i do "sudo mount -a" i get:
> 
matt@ubuntu-pc2:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //10.0.0.12/_matt,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //10.0.0.12/My_Documents,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //10.0.0.12/c,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //10.0.0.12/r,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //10.0.0.12/web,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

matt@ubuntu-pc2:~$ 


my fstab file is this:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=e3e00747-073d-4cc0-83ef-18f3a0659805 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=6CD48264D482307E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=616d6498-ad7a-42ce-922f-117307ac4923 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
//10.0.0.12/_matt    /home/matt/_matt smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//10.0.0.12/My_Documents    /home/matt/My_Documents smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//10.0.0.12/c    /home/matt/c smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//10.0.0.12/r    /home/matt/r smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//10.0.0.12/web    /home/matt/web smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

does anybody know how to fix this, perhaps fstab now requires to be written differently?

---

### Post by dbott67 on 2006-10-28
Do you have samba, smbfs & smbclient installed?

```
sudo apt-get install samba smbfs smbclient
```

---

### Post by matt91 on 2006-10-28
oh thanks:D, edgy must have removed smbfs and smbclient.

---

