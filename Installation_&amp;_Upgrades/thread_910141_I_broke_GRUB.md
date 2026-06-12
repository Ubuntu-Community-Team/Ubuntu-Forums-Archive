---
title: "I broke GRUB"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by Atrus6 on 2008-09-04
So, in essence I broke grub. (Not 100% Sure if this is the right section but...)

I dual boot, with Ubuntu and XP. I actually don't remember what I did, but I ended up with GRUB unable to load XP.  It wasn't a huge problem, since I mainly use XP to play games, and I could use some time off of them.  So, I didn't do anything about it. Then I got some Windows only software, and I tried to fix it.  This only broke GRUB more, now I cannot boot on Ubuntu, and I get an error number 15.

(The method I used [that broke GRUB completely] is as follows)
1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

I didn't use the command line version, because I was afraid to break it more. Oh the irony.

Well, after I was unable to boot to either OS, I booted up my PuppyLinux, because I remembered that it had an install GRUB function. I followed the steps, and nothing changed.  Still broke.

So, how would I fix it?
And the data on the partitions is still there (as far as I know, I didn't look all that indepth) so, I should (in my head) be able to fix it, with some more expert advice.

Thanks in advance!

---

### Post by eotakos on 2008-09-04
Hi! 

this is a nice thread that can help you out! - there are actually 2 ways to fix your issue that are introduced here - the first is proposed by the guy that made the thread, the other one is posed as an answer. 

the first is supposed to be more user-friendly. the other one is supposed to be quicker - choose the one you feel more comfortable with

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub).

note: this will only bring back grub - i don't think it'll give you the windows option in the grub-menu.

if you get over this first issue, post again so i know where you stand, and maybe i can help you with booting windows

---

### Post by caljohnsmith on 2008-09-04
If you have Ubuntu successfully installed, you don't need to reinstall it just to get Grub working. Boot your Live CD, and follow these steps:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Next, post the following:
```
sudo fdisk -lu
```
From the above command, find which is your Ubuntu partition in the form sdaX, and use that:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
```
All the above should give us enough info to help you get Grub working again. :)

---

### Post by Crafty Kisses on 2008-09-05
You can repair it with SuperGRUB > supergrub.forjamari.linex.org

---

### Post by Atrus6 on 2008-09-05
Result of sudo fdisk -lu:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27322731

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     3968054     1983996   83  Linux
/dev/hda2   *     3968055   116615834    56323890    7  HPFS/NTFS
/dev/hda3       116615835   232605134    57994650   83  Linux
/dev/hda4       232605135   234436544      915705    5  Extended
/dev/hda5       232605198   234436544      915673+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   156248189    78124063+   b  W95 FAT32


And the result of running the cat command:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27322731

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     3968054     1983996   83  Linux
/dev/hda2   *     3968055   116615834    56323890    7  HPFS/NTFS
/dev/hda3       116615835   232605134    57994650   83  Linux
/dev/hda4       232605135   234436544      915705    5  Extended
/dev/hda5       232605198   234436544      915673+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   156248189    78124063+   b  W95 FAT32


And starting up gives me this:
Booting 'Ubuntu Linux (on /dev/hda3)'
root(hd0,2)
File System type is ext2fs, partition type 0x83
Kernel /boot/vmlinux root = /dev/hda3 ro vga=normal

Error 15: File not Found
Press any key to continue...

---

### Post by Atrus6 on 2008-09-06
anyone?

---

### Post by caljohnsmith on 2008-09-06
Did you try reinstalling Grub to the MBR using the method I gave in post #3? And after that, how about mounting your Ubuntu partition and post the contents of your menu.lst like I also described to do in that post.

---

### Post by Atrus6 on 2008-09-06
My fault, I accidentally pasted the fdisk output twice in place of the output from the cat command.

Here are the actual results from the cat command:

ubuntu@ubuntu:~$ sudo mount /dev/hda3 /mnt
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Wed Sep  3 23:01:05 2008
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
# End GRUB global section
# Linux bootable partition config begins
  title Ubuntu Linux (on /dev/hda3)
  root (hd0,2)
  kernel /boot/vmlinuz root=/dev/hda3 ro vga=normal 
# Linux bootable partition config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,2)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/hda3)
root (hd0,2)
setup (hd0,2)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
ubuntu@ubuntu:~$ 

Sorry about that.

---

### Post by Atrus6 on 2008-09-08
Is there any other information that anyone requires?

---

### Post by caljohnsmith on 2008-09-08
It looks like when you tried to install Grub with PuppyLinux, it installed something a bit different then a normal Grub install in Ubuntu. Here's what I would do at this point to try and get Grub working again (from the Live CD):
```
sudo -i
mount /dev/hda3 /mnt
rm /mnt/boot/grub/*
grub-install --root-directory=/mnt /dev/hda
chroot /mnt
update-grub
exit
ls -l /mnt/boot/grub
cat /mnt/boot/grub/menu.lst
```
Please post the output of all commands above.

---

### Post by Atrus6 on 2008-09-08
And here are my results:



ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/hda3 /mnt
root@ubuntu:~# grub-install --root-directory=/mnt /dev/hda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/hda
(hd1)	/dev/hdb
root@ubuntu:~# chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:~# update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

root@ubuntu:~# exit
logout
ubuntu@ubuntu:~$ ls -l /mnt/boot/grub
total 312
-rw-r--r-- 1 root root    197 2008-09-08 12:20 default
-rw-r--r-- 1 root root     30 2008-09-03 15:01 device.map
-rw-r--r-- 1 root root   8056 2008-09-08 12:20 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-09-08 12:20 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-09-08 12:20 installed-version
-rw-r--r-- 1 root root   8608 2008-09-08 12:20 jfs_stage1_5
-rw-r--r-- 1 root root    512 2008-09-03 14:47 mbr.hda.6657
-rw-r--r-- 1 root root    801 2008-09-03 15:01 menu.lst
-rw-r--r-- 1 root root   1556 2008-09-03 14:47 menu.lst.old.6634
-rw-r--r-- 1 root root   7324 2008-09-08 12:20 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-09-08 12:20 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-09-08 12:20 stage1
-rw-r--r-- 1 root root 108356 2008-09-08 12:20 stage2
-rw-r--r-- 1 root root 104356 2007-10-18 15:58 stage2_eltorito
-rw-r--r-- 1 root root   1833 2008-09-03 15:01 usage.txt
-rw-r--r-- 1 root root   9276 2008-09-08 12:20 xfs_stage1_5
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Wed Sep  3 23:01:05 2008
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
# End GRUB global section
# Linux bootable partition config begins
  title Ubuntu Linux (on /dev/hda3)
  root (hd0,2)
  kernel /boot/vmlinuz root=/dev/hda3 ro vga=normal 
# Linux bootable partition config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,2)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/hda3)
root (hd0,2)
setup (hd0,2)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-08
That's not a good sign that the chroot command said you don't have a /bin/bash command in the mounted hda3 directory. While hda3 is still mounted on /mnt, do the following:
```
ls -l /mnt
cat /mnt/boot/grub/menu.lst.old.6634
```
Please post the output.

---

### Post by Atrus6 on 2008-09-08
Here is the output:



ubuntu@ubuntu:~$ ls -l /mnt
total 52
drwxr-xr-x  2 root root    4096 2008-09-03 22:38 bin
drwxr-xr-x  3 root root    4096 2008-09-03 14:46 boot
drwxr-xr-x  2 root root    4096 2008-09-03 22:38 dev
drwxr-xr-x  3 root root    4096 2007-11-01 17:33 home
drwxr-xr-x  2 root root    4096 2008-09-03 22:38 initrd
lrwxrwxrwx  1 root root      33 2008-08-25 23:17 initrd.img -> boot/initrd.img-2.6.24-19-generic
drwx------  2 root root   16384 2007-11-01 17:22 lost+found
drwxr-xr-x  6 root root    4096 2008-09-04 01:45 media
drwxr-xr-x 29 root root    4096 2008-06-02 01:53 root
drwxr-xr-x  2 root root    4096 2007-10-15 23:17 srv
lrwxrwxrwx  1 root root      30 2008-08-25 23:17 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
lrwxrwxrwx  1 root root      30 2008-06-06 20:03 vmlinuz.old -> boot/vmlinuz-2.6.24-18-generic
drwxr-xr-x  2 root ubuntu  4096 2008-09-03 22:38 windows
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst.old.6634
# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Wed Sep  3 22:47:18 2008
#
# The backup copy of the MBR for drive '/dev/hda' is
# here '/boot/grub/mbr.hda.6657'.  You can restore it like this.
# dd if=/boot/grub/mbr.hda.6657 of=/dev/hda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
# End GRUB global section
# Linux bootable partition config begins
  title Linux (on /dev/hda1)
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/hda1 ro vga=normal
# Linux bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/hda2)
  map (hd0,0) (hd0,1)
  map (hd0,1) (hd0,0)
  rootnoverify (hd0,1)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/hda3)
  root (hd0,2)
  kernel /boot/vmlinuz root=/dev/hda3 ro vga=normal
# Linux bootable partition config ends
# Other bootable partition config begins
  title Windows (on /dev/hdb1)
  map (hd0) (hd1)
  map (hd1) (hd0)
  rootnoverify (hd1,0)
  makeactive
  chainloader +1
# Other bootable partition config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,2)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/hda3)
root (hd0,2)
setup (hd0,2)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-09-08
It looks like you either don't have a complete install of Ubuntu, or you have maybe Puppylinux or some other distro installed where Ubuntu used to be:
[QUOTE=Atrus6]```
drwxr-xr-x 2 root root 4096 2008-09-03 22:38 bin
drwxr-xr-x 3 root root 4096 2008-09-03 14:46 boot
drwxr-xr-x 2 root root 4096 2008-09-03 22:38 dev
drwxr-xr-x 3 root root 4096 2007-11-01 17:33 home
drwxr-xr-x 2 root root 4096 2008-09-03 22:38 initrd
lrwxrwxrwx 1 root root 33 2008-08-25 23:17 initrd.img -> boot/initrd.img-2.6.24-19-generic
drwx------ 2 root root 16384 2007-11-01 17:22 lost+found
drwxr-xr-x 6 root root 4096 2008-09-04 01:45 media
drwxr-xr-x 29 root root 4096 2008-06-02 01:53 root
drwxr-xr-x 2 root root 4096 2007-10-15 23:17 srv
lrwxrwxrwx 1 root root 30 2008-08-25 23:17 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
lrwxrwxrwx 1 root root 30 2008-06-06 20:03 vmlinuz.old -> boot/vmlinuz-2.6.24-18-generic
drwxr-xr-x 2 root ubuntu 4096 2008-09-03 22:38 windows
```[/QUOTE]
Notice that you are missing at least the following Ubuntu directories:
```
/etc
/lib
/opt
/proc
/sbin
/usr
/var

```
So, I think if I were you, I would back up whatever files are important from your hda3 linux partition, and then reinstall Ubuntu. Did you maybe install some special version of Ubuntu, like the server version?

---

### Post by Atrus6 on 2008-09-08
No, in fact I've been this particular installation for about a year now.

In fact, I'm not even sure how I even did this. Oh well, it could be worse.

---

