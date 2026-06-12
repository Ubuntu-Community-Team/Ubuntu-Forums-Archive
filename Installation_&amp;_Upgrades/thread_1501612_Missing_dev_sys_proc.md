---
title: "Missing /dev /sys /proc"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by Tema1 on 2010-06-04
I have just installed 10.04. Updated the  software(124 packets) and rebooted to this:


 mount: mounting /dev/disk/by-uuid/1a1af5d8-88cb-44b5-aed9-1f22bb247c87  on root failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


I booted from live CD and checked sudo blkid and /etc/fstab file to see if the UUID was the same:

 # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=1a1af5d8-88cb-44b5-aed9-1f22bb247c87 /                ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=24dc1e5c-b8c2-4576-8b13-8202330ec421 none             swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8  0       0




  sudo blkid:


 /dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="1a1af5d8-88cb-44b5-aed9-1f22bb247c87"  TYPE="ext4"
/dev/sda5: UUID="24dc1e5c-b8c2-4576-8b13-8202330ec421"  TYPE="swap"


  I can't get into the root files. I hope this helps you help me.




 Thanks, Tema1

---

### Post by Herman on 2010-06-04
:) The first thing I would do would be to run a file system check in the / partition, and that will probably fix it.

First you'll need to boot your Ubuntu Live CD, or if you installed by USB then use that, or you could use a different Ubuntu or other Linux operating system providing it has ext4 support.

Once your Live CD or other operating system has booted, open a terminal and run e2fsck like this,
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```Where: /dev/sda1 is your / partition, replace with a different partition number if needed,
Where: /dev/sda12 contains an ext series file system.
Note: the 'C' must be in upper case, the 0 is a zero, 
-p means to 'preen' the file system meaning to automatically fix most problems but not if it means moving files to the lost+found, if the damage is too severe it will give you a report instead advising what to do next, (rather than just automatically moving your files).
-f stands for 'force', (run the check anyway even if the file system might not really need it).
-v is for 'verbose', (tell you what it's doing/has done).
 e2fsck is the program for checking and repairing ext series file systems.

---

### Post by Tema1 on 2010-06-04
I ran the code and this is the result:

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sda1: recovering journal
                                                                               
  149369 inodes used (1.02%)
      36 non-contiguous files (0.0%)
     131 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 124536/12
 1559992 blocks used (2.66%)
       0 bad blocks
       1 large file

  101463 regular files
   16582 directories
      60 character device files
      26 block device files
       0 fifos
     188 links
   31222 symbolic links (24718 fast symbolic links)
       7 sockets
--------
  149548 files


I will now try to reboot and see what happens.

Thanks, Tema1

---

### Post by Tema1 on 2010-06-04
On the reboot I did not get the error message , but I see nothing except the ubuntu purple backgroud. No toolbars or desktop files??

Any ideas?

Tema1

---

### Post by Herman on 2010-06-04
> WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes:( You ignored the WARNING?

In the future, be aware that in Linux operating systems we need to pay  attention to warning messages, it's not like Windows where there are  tons of stupid warnings that the user can safely ignore. When you see a  warning in Linux it means business and especially if it's in upper case -  ignore at your own risk! 

I'm sorry, but I forgot to repeat the same advice myself, and warn you never to run a file system check on a file system while it's mounted, so it's my fault too.

I'm surprised it even booted at all.
You will be lucky if you can recover your data.
If you don't have a recent backup of your data and you can still 'see' your files from a Live CD, then be sure to make a fresh backup right away!

Simply try running another file system check again is the only way I can think of to go forwards from here, but this time make sure you don't mount your file system, I repeat DO NOT MOUNT the FILE SYSTEM before running any file system check -EVER!!! (Unless you're doing it for an experiment and you don't care about what you may destroy).

EDIT:
> I have just installed 10.04. Updated the  software(124 packets) and  rebooted to this:Lucky there's probably no data yet.

Maybe just re-installing would be quicker and better than trying to repair.

---

### Post by Herman on 2010-06-04
:) It's all too easy to forget the not everybody was born speaking Linux  terms.

The term 'mount', when used in Linux means something like to 'connect' or 'engage'.

When we 'mount' a file system, say from the Live CD, we can look inside it, and normally it's connected to the Live CD's file system at a 'mount point', which is just a folder, normally in the /media folder, which is two stories up from the home folder. If you look inside the /media folder and if there are file system mounted, you can open any of the folders and see what's inside the mounted file systems. Those folder in /media are called 'mount points'.
Traditionally, the /mnt directory was supposed to be used for making mount point folders in, but now we use the /media directory and in Ubuntu an icon appears automatically on out desktop when we mount a file system if the mount point is in /media.

To 'mount' a file system in Ubuntu, we go into the 'Places' menu and click on an icon to open a Window which shows all the files inside that disk or partition. In the case of a USB drive, we just plug it in and it will be automatically 'mounted', a Window usually opens on our desktop showing us the files in the USB disk. That's the modern way to 'mount' a file system, under normal circumstances.

To unmount, you just right-click on the desktop icon for that file system and select 'unmount'.   :)

---

### Post by gabak on 2010-07-27
i did what u said. and it said
error reading block 700 (attempt to read block from filesystem resulted in short read)
/dev/sda1  unexpected inconsistency; run fsck manually


> **Herman said:**
> :) The first thing I would do would be to run a file system check in the / partition, and that will probably fix it.

First you'll need to boot your Ubuntu Live CD, or if you installed by USB then use that, or you could use a different Ubuntu or other Linux operating system providing it has ext4 support.

Once your Live CD or other operating system has booted, open a terminal and run e2fsck like this,
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```Where: /dev/sda1 is your / partition, replace with a different partition number if needed,
Where: /dev/sda12 contains an ext series file system.
Note: the 'C' must be in upper case, the 0 is a zero, 
-p means to 'preen' the file system meaning to automatically fix most problems but not if it means moving files to the lost+found, if the damage is too severe it will give you a report instead advising what to do next, (rather than just automatically moving your files).
-f stands for 'force', (run the check anyway even if the file system might not really need it).
-v is for 'verbose', (tell you what it's doing/has done).
 e2fsck is the program for checking and repairing ext series file systems.

---

### Post by Herman on 2010-07-27
> error reading block 700 (attempt to read block from filesystem resulted in short read)
/dev/sda1  unexpected inconsistency; run fsck manuallyThat means the gentle file system check wasn't enough to fix your file system problem(s) and you will need to resort to a more intense file system check. 
By using the -y option, (y for 'yes'), you will be giving the file system check program permission to automatically unlink whatever files it needs to and move them to the lost+found folder. 
The -y option can save you hours at the keyboard pressing the y key over and over again because otherwise e2fsck needs to ask for your permission for each file individually and sometimes there can be a lot of files to unlink.
```
sudo e2fsck -y -f -v /dev/sda1
```The number of files that might be unlinked to the lost+ found could be  none or a lot, depending on your luck and on the nature of the problem. 

If you're lucky, no files will be moved to the lost+found directory.

Sometimes if it's only one or two obscure system files that aren't used very often, you might not miss them and maybe they will be replaced anyway in  a future update so you might not need to look in the lost+found to recover any files.

Other times, a lot of files can be unlinked to the lost+found directory, and you might need to go into the lost+found to recover user files like photos and whatever files you had. 
They will probably be renamed with an inode number instead of the file's name.
If the files are vital operating system files it could break your operating system and you might need to use a Live CD to recover your files from the lost+found and you might need to re-install Ubuntu.

I hope it will fix your file system problem without removing any important files. Keep your fingers crossed! ;)

---

