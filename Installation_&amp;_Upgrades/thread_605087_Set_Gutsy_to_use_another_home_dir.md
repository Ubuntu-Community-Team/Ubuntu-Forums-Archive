---
title: "Set Gutsy to use another /home dir"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by marciano#1 on 2007-11-06
I have splited an ext3 partition in two parts: sdb2 and sdb4
 sdb2 contains my old and prefered /home It also contains Feisty installation and all my installed programs.
 sdb4 contains a clean install of Gutsy
 I need to change Gutsy settings to use /home of the other partition sdb2 instead of its recently created in sdb4.

 How do I tell Gutsy to use the other /home dir ?
Thank you

---

### Post by taurus on 2007-11-06
Open a terminal and edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb2   /home   ext3   defaults   0   1
```
Save it and then reboot.  /dev/sdb2 now should mount to /home.

```
df -h
```

---

### Post by marciano#1 on 2007-11-06
I got 'Could not start kstartupconfig. Check your installation' starting KDE after reboot.
Thank you

fstab> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb4
UUID=78a1b861-4617-46e8-8626-60aafdbc9c1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=94c37bdf-519d-4dae-bd51-e4123c022612 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc        /media/floppy1  auto    rw,user,noauto,exec 0       0
/dev/sdd        /media/floppy2  auto    rw,user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sdb1 /media/sdb1 vfat rw,user,fmask=0111,dmask=0000 0 0
# /dev/sbd2
#UUID=cf35fc52-7155-43c8-8904-3681d53fcf8e /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2 /media/sdb2 ext3 defaults,errors=remount-ro 0       1
# set by me
#/dev/sdb2 /home ext3 defaults 0 1

df -h
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb4             104G  2.3G   97G   3% /
varrun                505M  136K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  124K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   34M  471M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              75G   71G  4.0G  95% /media/sda1
/dev/sdb1             9.8G  4.4G  5.5G  45% /media/sdb1
/dev/sdb2             175G   59G  111G  35% /media/sdb2


---

### Post by marciano#1 on 2007-11-07
As I understand I can mount   
 /dev/sdb2   /home   ext3   defaults   0   1
so /dev/sdb2 will be THE /home dir itself.
What I am asking is if can I set or mount regular /home 'pointing' to the /home located in other partition, sdb2
Of course I can remove all data in sdb2 but /home , then move its content to / and mount /dev/sdb2 /home
Thank you

---

### Post by timcredible on 2007-11-07
if the fstab thing the other poster suggested doesn't work, boot into gutsy, then:
```

sudo mv /home /home-gutsy
sudo ln -s /home /media/sdb2/home

```
this renames your /home directory in sdb4, then does a symbolic link that makes gutsy look in sdb2 for /home

---

