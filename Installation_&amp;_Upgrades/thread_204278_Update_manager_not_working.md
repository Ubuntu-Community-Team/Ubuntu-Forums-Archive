---
title: "Update manager not working"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by codified on 2006-06-26
Hi,

I have Ubuntu 6.06 running with an internet and network connection.  When I try to run the Update Manager, and press the check button, it gives me an error to say that the following repositories may no longer be available.

[http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Temporary failure resolving 'au.archive.ubuntu.com'
[http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Temporary failure resolving 'au.archive.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Temporary failure resolving 'security.ubuntu.com'

What do I do now?  Is this correct, or is there a network problem?

---

### Post by tonyr on 2006-06-26
Most likely a network problem.  If you feel comfortable modifying repositories in **Synaptic**
or by editting **/etc/apt/sources.list** manually, you could try some of the other repositories locations 
(change the **au** n the URL to **eu** or **ca** or **us** or **gb**, for example).

---

### Post by codified on 2006-06-26
You're right, a network problem.  I didn't realise that there are two places where you have to enter network proxy settings (Firefox preferences and Ubuntu admin / system).  Both are now up to date, and updates working well.

Can you solve my other problem?  My install has two shortcuts on the desktop, to fat and NTFS partitions.  I have a 3rd FAT32 partition that hasn't shown up on the desktop.  How do I make it show up?

Thanks.

---

### Post by tonyr on 2006-06-26
Every 'normal' filesystem in my **/etc/fstab** file shows up on my desktop.  

Is your other FAT32 partition mounted?   Is it mentioned in the file **/etc/fstab**?

In a terminal (Applications->Accessories->Terminal), type
```

mount
cat /etc/fstab
sudo fdisk -l

```

and post the results here. (that last command, the **fdisk** one, will ask for your 
password).

---

### Post by codified on 2006-06-26
Here are the results:

codified@ubuntu:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-386/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda6 on /windows type vfat (rw,utf8,umask=007,gid=46)
codified@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
codified@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        8517    68364607+   7  HPFS/NTFS
/dev/sda3            8518       10219    13671315   83  Linux
/dev/sda4           10220       12161    15599115    5  Extended
/dev/sda5           10220       10458     1919704+  82  Linux swap / Solaris
/dev/sda6           10460       12161    13671315    b  W95 FAT32
codified@ubuntu:~$

edit: 

the two icons appearing on the desktop are 'DellUtility' and 'sda2'.  I would like to see the partition currently mapped to /windows appear as a disk icon on the desktop.  I don't care about seeing DellUtility, and I should probably hide sda2 (NTFS, and don't want anyone using linux to write to it).

Thanks

---

### Post by tonyr on 2006-06-26
I sure hope the **cat /etc/fstab** output really looks like this

[QUOTE=codified]
codified@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
[/QUOTE]
and not like it does in your post!

I couldn't swear to it, but I believe that only devices appearing mounted on a directory
in** /media** show up on the Desktop.  To modify your arrangement, (unless you 
have some overriding need to have the **windows** partition mounted in the
root directory) you will need to unmount the windows partition, create a windows
directory in the **/media** directory, modify **/etc/fstab** to specify the 
**/media/windows** mount point, and remount the partition.  

In a terminal do
```

sudo umount /windows
sudo mkdir /media/windows

```

The first time you use  **sudo**, it will prompt you for your password.

Then edit **/etc/fstab** as root.  In a terminal, I do
```

sudo vi /etc/fstab

```
since I use the **vi** editor. You should use whatever editor you are comfortable with.
Change the line that says
```

/dev/sda6       **/windows**        vfat    defaults,utf8,umask=007,gid=46 0       1

```

to
```

/dev/sda6       **/media/windows**        vfat    defaults,utf8,umask=007,gid=46 0       1

```
and save and close the file.

Then do
```

sudo mount -a

```

and if I am not too stupid, the **windows** partition should show up on your
desktop as a hdd icon.

EDIT: I followed myh own instructions here, and it seemed to work as I expected it would.

---

### Post by codified on 2006-06-26
You're right about the /etc/fstab file - it looks as you have shown it.

I tried your instructions, but there is no new icon on the desktop.  When I use Nautilus, it doesn't show up as a drive either.

Here is modified fstab, in case I made a mistake.  Any other ideas?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /media/windows  vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by codified on 2006-06-26
Not sure if this helps, but the fat32 partition I'm trying to view is actually a logical drive on an extended partition - not a primary partition.  Think Ubuntus installer handled this for me when it found multiple primary partitions on the hard drive already created by Dell.

---

### Post by tonyr on 2006-06-26
It doesn't matter whether it is a primary or logical partition.

What does **mount** say? (mount command in a terminal)

---

### Post by codified on 2006-06-27
Tonyr,

I have rebooted and now the windows partition shows up on the desktop as desired - thanks!!

---

