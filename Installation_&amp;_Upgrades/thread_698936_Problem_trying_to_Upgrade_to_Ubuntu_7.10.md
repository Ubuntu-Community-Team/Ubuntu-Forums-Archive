---
title: "Problem trying to Upgrade to Ubuntu 7.10"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by nigel_salvador on 2008-02-16
I am not new to Ubuntu however I am new to this particular forum for getting help on problems that I've encounter with Ubuntu. Therefore, I would like to apologize in advance if I do not follow some of proper etiquette of the Ubuntu Forum.

This is my problem:
The partition on which Linux Ubuntu 6.06 resided needed expanding. I used the GParted LiveCD to repartition my hard drive. As a result after rebooting my system I received the following error:

Grub Loading Stage 1.5

Grub Loading Please Wait...

Error 2

I attempted to fix the problem by repairing the partition, assuming that a damaged or lost partition was the cause for the above error. I did so by using Linux's native parted shell. Also, to fix the problem I attempted to reinstall grub, the boot loading software. These attempts were not successful. 

If anyone could help me with my problem it would be greatly appreciated. 

Thanks

---

### Post by PmDematagoda on 2008-02-16
If you can access the hard drive using the Live CD, can you post the contents of the menu.lst and blkid.

---

### Post by nigel_salvador on 2008-02-20
I am having trouble searching for these files, can you provide me with a little help. Thanks :)

---

### Post by nigel_salvador on 2008-02-20
Nevermind, I used the "find" command. It resulted in the file in two locations, which are:

- /usr/share/doc/grub/examples/menu.lst
- /rofs/usr/share/doc/grub/examples/menu.lst

The contents of the file is,

#
# Sample boot menu configuration file
#

# Boot automatically after 30 secs.
timeout 30

# By default, boot the first entry.
default 0

# Fallback to the second entry.
fallback 1

# For booting GNU (also known as GNU/Hurd)
title  GNU (also known as GNU/Hurd)
root   (hd0,0)
kernel /boot/gnumach.gz root=device:hd0s1
module /hurd/ext2fs.static --multiboot-command-line=${kernel-command-line} --host-priv-port=${host-port} --device-master-port=${device-port} --exec-server-task=${exec-task} -T typed ${root} $(task-create) $(task-resume)
module /lib/ld.so.1 /hurd/exec $(exec-task=task-create)

# For booting GNU/Linux
title  GNU/Linux
root (hd1,0)
kernel /vmlinuz root=/dev/hdb1
#initrd /initrd.img

# For booting GNU/kFreeBSD
title  GNU/kFreeBSD
root   (hd0,2,a)
kernel /boot/loader.gz

# For booting GNU/kNetBSD
title  GNU/kNetBSD
root   (hd0,2,a)
kernel --type=netbsd /boot/knetbsd.gz

# For booting Mach (getting kernel from floppy)
title  Utah Mach4 multiboot
root   (hd0,2)
pause  Insert the diskette now!!
kernel (fd0)/boot/kernel root=hd0s3
module (fd0)/boot/bootstrap

# For booting FreeBSD
title  FreeBSD
root   (hd0,2,a)
kernel /boot/loader

# For booting NetBSD
title  NetBSD
root   (hd0,2,a)
kernel --type=netbsd /netbsd

# For booting OpenBSD
title  OpenBSD
root   (hd0,2,a)
kernel --type=netbsd /bsd

# For booting OS/2
title OS/2
root  (hd0,1)
makeactive
# chainload OS/2 bootloader from the first sector
chainloader +1
# This is similar to "chainload", but loads a specific file
#chainloader /boot/chain.os2

# For booting Windows NT or Windows95
title Windows NT / Windows 95 boot menu
rootnoverify (hd0,0)
makeactive
chainloader  +1
# For loading DOS if Windows NT is installed
# chainload /bootsect.dos

# For installing GRUB into the hard disk
title Install GRUB into the hard disk
root    (hd0,0)
setup   (hd0)

# Change the colors.
title Change the colors
color light-green/brown blink-red/blue

However the other file is an executable which I obviously cannot open

---

### Post by Partyboi2 on 2008-02-20
The terminal  (Applications>Accessories>Terminal) commands to get what PmDematagoda asked for 
```
blkid
``````
cat /boot/grub/menu.lst
```
menu.lst is with a small L

---

### Post by PmDematagoda on 2008-02-20
You will need to mount the hard drive, post the output of:-
```
sudo fdisk -l
```

---

### Post by nigel_salvador on 2008-02-20
This is the result of entering "blkid":

ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ 

This is the result of entering "cat /boot/grub/menu.lst"

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 

This is result of entering "fdisk -l"

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20cb20cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4217    33873021    7  HPFS/NTFS
/dev/hdb2   *        4218        8478    34226482+  83  Linux
/dev/hdb3            9389        9644     2056320   82  Linux swap / Solaris
/dev/hdb4            9645        9729      682762+  83  Linux
ubuntu@ubuntu:~$

---

### Post by PmDematagoda on 2008-02-20
Mount the Linux partitions:-

1) Make 2 directories in /media using:-
```
sudo mkdir /media/disc

sudo mkdir /media/disc2
```

2) Mount the two Linux drives on the new mount points using:-
```
sudo mount /dev/hdb2 /media/disc

sudo mount /dev/hdb4 /media/disc2
```

After they are mounted see if these commands gives any output:-
```
cat /media/disc/boot/grub/menu.lst

cat /media/disc2/boot/grub/menu.lst
```
If you do get any output other than an error using one of the commands, then post them here.

---

### Post by nigel_salvador on 2008-02-20
The results of each of your steps are below:

1)

ubuntu@ubuntu:~$ sudo mkdir /media/disc
ubuntu@ubuntu:~$ sudo mkdir /media/disc2

2)

ubuntu@ubuntu:~$ sudo mount /dev/hdb2 /media/disc
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount /dev/hdb4 /media/disc2

----------------------------------------------------------------------------------------

ubuntu@ubuntu:~$ cat /media/disc/boot/grub/menu.lst
cat: /media/disc/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /media/disc2/boot/grub/menu.lst
cat: /media/disc2/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 

I just want to say thank you in advance, your amazing

---

### Post by PmDematagoda on 2008-02-20
Try and navigate to the mounted disk using:-
```
cd /media/disc
```
and then post the files in there using:-
```
ls
```

---

### Post by nigel_salvador on 2008-02-20
The result:

ubuntu@ubuntu:~$ cd /media/disc
ubuntu@ubuntu:/media/disc$ ls
ubuntu@ubuntu:/media/disc$ 

The directory is empty

---

### Post by PmDematagoda on 2008-02-20
Post the output of:-
```
cat /etc/mtab
```

---

### Post by nigel_salvador on 2008-02-20
The result:

ubuntu@ubuntu:/media/disc$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/hdb4 /media/disc2 ext2 rw 0 0
ubuntu@ubuntu:/media/disc$ 

What is the purpose of this file

---

### Post by PmDematagoda on 2008-02-20
You did not mount /dev/hdb2, please try the command again and post the result of:-
```
cat /etc/mtab
```

The mtab file contains information about the current mount points, it can be useful in finding out if a certain volume or partition has been mounted or not.

---

### Post by nigel_salvador on 2008-02-20
The result:

ubuntu@ubuntu:/media/disc$ sudo mount /dev/hdb2 /media/disc
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/media/disc$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev/hdb4 /media/disc2 ext2 rw 0 0
ubuntu@ubuntu:/media/disc$

There is a problem with trying to mount that particular partition. Do you know how to resolve the error from trying to mount /dev/hdb4 ?

---

### Post by PmDematagoda on 2008-02-20
The error is with hdb2. Run fsck on it:-
```
fsck -r /dev/hdb2
```

After the problems are fixed try mounting it again.

---

### Post by nigel_salvador on 2008-02-20
The result:

ubuntu@ubuntu:/media/disc$ sudo fsck -r /dev/hdb2
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Group descriptors look bad... trying backup blocks...
Corruption found in superblock.  (blocks_count = 0).

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 32768 <device>

ubuntu@ubuntu:/media/disc$ sudo mount /dev/hdb2 /media/disc
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/media/disc$

---

### Post by PmDematagoda on 2008-02-20
It looks bad, I think you may have to reinstall Ubuntu or maybe even replace the hard drive itself. But before we decide that post the output of:-
```
ls
```
in the /media/disc2 directory.

---

### Post by nigel_salvador on 2008-02-20
The result:

ubuntu@ubuntu:/media/disc2$ ls
lost+found
ubuntu@ubuntu:/media/disc2$

---

### Post by PmDematagoda on 2008-02-20
You will have to reinstall Ubuntu because it seems that the partition onto which it was installed is corrupted.

But first see if you can actually format it. Open GParted in System>Administration>Gnome Partition Editor and then format the partition hdb2 to ext3.

---

### Post by nigel_salvador on 2008-02-20
So based on your knowledge there is no way of recovering the information off of the partition?

Also, the the partiton /dev/hdb2 has an ext2 filesystem and you are suggesting that I format using filesystem ext3 and not ext2.

Well regardless of the outcome I would like to thank you, you were very helpful

---

### Post by PmDematagoda on 2008-02-20
> **nigel_salvador said:**
> So based on your knowledge there is no way of recovering the information off of the partition?

Also, the the partiton /dev/hdb2 has an ext2 filesystem and you are suggesting that I format using filesystem ext3 and not ext2.

Well regardless of the outcome I would like to thank you, you were very helpful

There are ways but since you do not have any important files or data(you don't do you?) a clean reinstall is better.

Yes, format it as ext3, ext3 is more reliable than ext2 is so it can help avoid future problems.

---

### Post by nigel_salvador on 2008-02-20
Well I do have important files on that partition, which - yes as I know, should have backed up. What else could you suggest in terms of recovering from the partition?

---

### Post by PmDematagoda on 2008-02-20
You could try recovery tools such as [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Download") or [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/"), but I am not too sure as I have not tried them out myself.

---

