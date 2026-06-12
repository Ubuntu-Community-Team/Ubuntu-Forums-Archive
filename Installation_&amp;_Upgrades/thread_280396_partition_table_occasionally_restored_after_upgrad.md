---
title: "partition table occasionally restored after upgrade to edgy"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by john826 on 2006-10-19
I recently upgraded my thinkpad t43 from dapper to edgy, but it occasionally gives me a gdm login screen with all the text replaced by small boxes, and I login to text mode by CTRL+ALT+F1 and wanted to check the font directory, then I found the whole file system directory names are gray, and I use df -h to check the partition, it turns out the partition is a very old one that before I reszied my harddisk to give more space to linux partition!!! 

Now I have to reboot the system every time when it loads the old partition and pray. Any one has experienced this odd problem?

---

### Post by john826 on 2006-10-19
this is my partition list when I can boot normally


john@pangu:/opt$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             4.7G  1.5G  3.3G  31% /
varrun                506M   64K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  487M   4% /lib/modules/2.6.15-27-386/volatile
/dev/sda1             126M   51M   75M  41% /boot
/dev/sda8              21G   13G  8.3G  60% /home
/dev/sda10             10G  4.1G  5.9G  41% /usr
/dev/sda7             2.8G  1.9G  959M  67% /var
/dev/sda2             9.4G  7.9G  1.5G  85% /windows/sda2
/dev/sda9             9.8G  3.9G  6.0G  39% /windows/sda4
john@pangu:/opt$ 


I found this in my /etc/fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5 -- converted during upgrade to edgy
UUID=3b440047-9ac7-4ed2-b54d-f24e7785f588 / reiserfs defaults 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=0695fdef-9456-4491-9993-7d3d93efcef4 /boot reiserfs notail 0 2
# /dev/sda8 -- converted during upgrade to edgy
UUID=7723103f-11c0-4e17-98aa-20cb1350ca0c /home reiserfs defaults 0 2
# /dev/sda10 -- converted during upgrade to edgy
UUID=19c1948c-9ff4-4c18-ba84-deb9c96caf12 /usr reiserfs defaults 0 2
# /dev/sda7 -- converted during upgrade to edgy
UUID=c9cbc8bc-42ba-4c25-a51b-8bafdf8b73d0 /var reiserfs defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=C89C3FF69C3FDD9E /windows/sda2 ntfs auto,user,nls=utf8,umask=0 0 0
# /dev/sda9 -- converted during upgrade to edgy
UUID=44EE-379B /windows/sda4 vfat auto,user,utf8,umask=0 0 0
# tudo:/home  /home/john/tudo/home    nfs rw              0       0



and GParted tells me there is a partition /dev/sda6 "unable to find mountpoint"

---

