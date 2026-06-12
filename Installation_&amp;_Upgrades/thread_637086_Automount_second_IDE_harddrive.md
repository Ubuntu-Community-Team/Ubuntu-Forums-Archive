---
title: "Automount second IDE harddrive"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by dma1342 on 2007-12-10
Hi, 

I have a problem with my freshly installed ubuntu system. My plan is to make a headless media server and I have a Dell hardware system with two IDE harddrives. Everything installs/functions perfectly out of the box apart from the second IDE harddrive, the second IDE drive does not automount (I hope the term is correct, being a windows user for 15 years never having to mount anything, is not the best way to learn the correct vocabulary). 

If I type df on system start I get this result
[FONT="Courier New"]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            113892200   2412220 105694576   3% /
varrun                  257672       228    257444   1% /var/run
varlock                 257672         0    257672   0% /var/lock
udev                    257672        80    257592   1% /dev
devshm                  257672         0    257672   0% /dev/shm
lrm                     257672     34696    222976  14% /lib/modules/2.6.22-14-generic/volatile[/FONT]

and if I mount the disk by right clicking on the disk in the File Browser and the typing df I get

[FONT="Courier New"]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            113892200   2412248 105694548   3% /
varrun                  257672       228    257444   1% /var/run
varlock                 257672         0    257672   0% /var/lock
udev                    257672        80    257592   1% /dev
devshm                  257672         0    257672   0% /dev/shm
lrm                     257672     34696    222976  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1            118169876     60996 112106196   1% /media/disk[/FONT]

It seems to me that the second disk (/dev/sdb1) is mounted as /media/disk. I would like this to happen automatically on system start and not have to log in to do this. Is there an easy way to do this?

Any help appreciated
/dma

---

### Post by taurus on 2007-12-10
What filesystem (vfat, ntfs, or ext3) is your second harddrive, /dev/sdb1?

```
sudo fdisk -l
```

Basically, you just add an entry in /etc/fstab to have it mount each time you boot Ubuntu.

---

### Post by Pumalite on 2007-12-10
Delete.

---

### Post by dma1342 on 2007-12-10
Here is the output from the sudo fdisk -l command.
[FONT="Courier New"]
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaead9016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux[/FONT]

And the output from the mount command

[FONT="Courier New"]/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev)[/FONT]

Which I tried to read the man page for, but realized that I would probably have to read a few Linux books before understanding. If I read the output from the mount command and try to remember what the default filesystem was when I partitioned my drives I would have to say that the  filesystem was ext2, but am I sure - No.

/dma

---

### Post by taurus on 2007-12-10
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext2   defaults   0   1
```
Save it.  Then, create a new mount point for it.

```
sudo mkdir /media/sdb1
```
Now, reboot.  Your /dev/sdb1 should now be mounted to /media/sdb1.  If you want to have write access to it without using sudo/gksudo, then you need to change the ownership of /media/sdb1 from root to your login name, _assuming_ it's **username**.

```
sudo chown -R **username**:**username** /media/sdb1
ls -la /media
```

---

### Post by dma1342 on 2007-12-11
Thanks, 

works perfectly.

/ma

---

