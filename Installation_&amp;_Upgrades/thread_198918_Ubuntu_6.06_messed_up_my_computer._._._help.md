---
title: "Ubuntu 6.06 messed up my computer. . . help"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by PsychoGIno on 2006-06-17
I tried to upgrade from 5.1 to 6.06, I got an Xserver problem.  I just tried to install it from the live CD.  I went to manually edit partition tables, resized my 360gb windows partition to 300gb then the partition table shows my windows partition as unknown.  It doesnt say it has anything on it.  It doesnt say free space or used space either.  Is there any way to recover all of my files?

---

### Post by hangfire on 2006-06-17
[QUOTE=PsychoGIno]I tried to upgrade from 5.1 to 6.06, I got an Xserver problem.  I just tried to install it from the live CD.  I went to manually edit partition tables, resized my 360gb windows partition to 300gb then the partition table shows my windows partition as unknown.  It doesnt say it has anything on it.  It doesnt say free space or used space either.  Is there any way to recover all of my files?[/QUOTE]

Chopping down existing partitions is not the way to make room for Ubuntu. Some installs have a partition editor which MIGHT resize an existing partition satisfactorily, saving data; usually, going manual bypasses those safeguards.

You can try setting the Windows partition back to NTFS, better yet, if the data is real important, try to duplicate the original Windows NTFS partition size (probably the whole disk). Then set it to bootable flag on and see what happens.

HF

---

### Post by PsychoGIno on 2006-06-18
How do I go about doing that? When it shows up as unknown it has the boot flag. When I go to format > ntfs the flag goes away.  I dont know what to do.  Is there any way that I can just copy some files over?

---

### Post by aysiu on 2006-06-18
Have you already applied the changes in GParted? Can you post a screenshot of what your partition table looks like?

---

### Post by PsychoGIno on 2006-06-18
[QUOTE=aysiu]Have you already applied the changes in GParted? Can you post a screenshot of what your partition table looks like?[/QUOTE]


I havent changed anything yet.  Here's a screen:

[http://img220.imageshack.us/img220/405/screenshotgparted9vg.png](http://img220.imageshack.us/img220/405/screenshotgparted9vg.png)

---

### Post by aysiu on 2006-06-18
[QUOTE=PsychoGIno]I havent changed anything yet.[/quote] Well, if that's the case... > Is there any way to recover all of my files? ... your files should still be good.

Just so we can do a little comparison (maybe GParted is just messed up--which wouldn't be the first time I've heard of it), can you open a terminal and post back here the output of this command? ```
sudo fdisk -l
``` That's a lowercase L, not a one.

---

### Post by PsychoGIno on 2006-06-18
Here's another screenshot. 

[http://img206.imageshack.us/img206/5819/1237cb.png](http://img206.imageshack.us/img206/5819/1237cb.png)

Do you know what I should do?

---

### Post by aysiu on 2006-06-18
I don't know what you should do, but according to ```
sudo fdisk -l
``` your partition table looks fine. Maybe GParted is having some kind of funky error. /dev/sda1, for example, appears as FAT32, not "unknown."

> Is there any way to recover all of my files? Did you want to recover your files? If so, just paste these terminal commands: ```
sudo umount /dev/sda1
sudo mkdir /recovery
sudo mount -t vfat /dev/sda1 /recovery -o iocharset=utf8,umask=000
``` And then you should see your files in the /recovery directory.

Or is it the Ubuntu 5.10 files that you're trying to recover?

---

### Post by PsychoGIno on 2006-06-18
I just want to make my windows the way it was.  I would like to have 3 partitions:  One for my windows stuff, one for Ubuntu and one fat32 partition for media files from both.  I just want to make sure I have all my windows stuff first. When I tried to boot into windows it couldnt find the partition.

---

### Post by aysiu on 2006-06-18
Windows couldn't find the FAT32 partition? I'm a bit confused about what you're trying to do.

---

### Post by PsychoGIno on 2006-06-18
No.  I wanted to resize my windows ntfs partition.  I resized my 5.10 partition.  I chose sizes for both and I had leftover space.  I think it did resize them but it didnt finish something.  It said unknown, I panicked and turned it off to boot into windows but it wouldnt boot.  Now I cant boot into either  and I am forced to run the live cd. What I want to do is restore my Windows partition to how it was with all my data back on it, preferably so I dont have to reinstall windows.

---

### Post by aysiu on 2006-06-18
That's weird. You say the Windows partition was NTFS. GParted says it's "unknown," and *fdisk* says it's FAT32.

If you try the mount command I gave you before, can you see your Windows files in there? I think you should focus on saving your data before you worry about saving your installation--just on the off chance that you *do* have to reinstall.

---

### Post by PsychoGIno on 2006-06-18
I tried pasting them and it didnt work.  Here's what it showed:

[http://img239.imageshack.us/img239/2779/3216em.png](http://img239.imageshack.us/img239/2779/3216em.png)

---

### Post by aysiu on 2006-06-18
By the way, terminal output can be highlighted and pasted into posts--they don't need to be attached as images. That may save you some time and save me clicking on the image.

It appears that you already have a directory called /recovery: ```
mkdir: cannot create directory '/recovery': File exists
``` Maybe you can try creating another one and mounting it there. You can call it /recovery2 or /gobbledygook or /smorgasbord. Whatever you want, but make sure it doesn't already exist.

I'm not sure that's where the problem lies, but let's tackle it one error at a time.

---

### Post by PsychoGIno on 2006-06-18
It creates the directory but it doesnt put anything in it.  Could it be because Im running the live cd?

BTW, thank you for your help.  Im sure most people wouldnt care at all about how I messed up my hard drive.  I really appreciate it.

---

### Post by aysiu on 2006-06-18
So after you try to mount it to /smorgasbord, what error do you get, if any? Same thing about ```
wrong fs type, bad option, bad superblock
```?

---

### Post by PsychoGIno on 2006-06-18
```
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t vfat /dev/sda1 /recovery -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$

```

Thats the error

---

### Post by aysiu on 2006-06-18
I'm not very good at diagnosing these sorts of problems, but have you tried actually running ```
dmesg | tail
```?

---

### Post by PsychoGIno on 2006-06-18
[QUOTE=aysiu]I'm not very good at diagnosing these sorts of problems, but have you tried actually running ```
dmesg | tail
```?[/QUOTE]


Here's what I got:

```
ubuntu@ubuntu:~$ dmesg | tail
\[4294824.361000] Bluetooth: L2CAP socket layer initialized
[4294825.085000] Bluetooth: RFCOMM socket layer initialized
[4294825.085000] Bluetooth: RFCOMM TTY layer initialized
[4294825.085000] Bluetooth: RFCOMM ver 1.7
[4294848.147000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295729.253000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4295729.256000] FAT: bogus number of reserved sectors
[4295729.256000] VFS: Can't find a valid FAT filesystem on dev sda1.
[4296414.243000] cdrom: open failed.
[4296414.254000] cdrom: open failed.
ubuntu@ubuntu:~$ \


```

---

### Post by aysiu on 2006-06-18
These two messages look concerning: ```
[4295729.256000] FAT: bogus number of reserved sectors
[4295729.256000] VFS: Can't find a valid FAT filesystem on dev sda1.
``` Maybe you need to do some kind of system repair/recovery? I can give you links. Unfortunately, I don't know how to use them.

[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

---

### Post by PsychoGIno on 2006-06-18
How do I install them?

---

### Post by aysiu on 2006-06-18
I have no idea. I've never had to use system recovery tools, so I'm at a bit of a loss here.

---

### Post by lychee on 2006-06-18
[QUOTE=aysiu]These two messages look concerning: ```
[4295729.256000] FAT: bogus number of reserved sectors
[4295729.256000] VFS: Can't find a valid FAT filesystem on dev sda1.
``` Maybe you need to do some kind of system repair/recovery? I can give you links. Unfortunately, I don't know how to use them.

[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)[/QUOTE]

i could be totally wrong here, but might it be possible that the filesystem is ntfs instead? try -t ntfs -o ro

might have to set umask too; but see if it can be mounted first...

---

### Post by PsychoGIno on 2006-06-22
Ok well I got everything recovered but now I have a new problem.  I made a FAT32 partition.  It shows up but it wont let me mount it.  Can someone help?

Edit:  I followed the directions on this page: [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

And when I got to the end to mount all the terminal gave me this:
```
psychogino@PsychoGino:~$ sudo mount -a
mount: unknown filesystem type 'fat32'

```

I thought fat32 was supposed to work with Linux?

---

### Post by guyg on 2006-06-23
[QUOTE=hangfire]Chopping down existing partitions is not the way to make room for Ubuntu.[/QUOTE]

What is the correct way then? This guy's problem just happened to me: Tried to install Ubuntu next to an existing Windows XP, told the installer to resize my partition, and it destroyed it (shows up as 'unknown'). 

Now my machine won't boot. I tried setting the boot flag to 'boot' in gparted but that didn't help. I'm in the middle of restoring my machine to factory settings as I'm writing this.

I have already done resize/install-linux several times in the past, but I always did the resizing from within Windows using Partition Magic. It always worked, and it certainly never messed up my machine.

---

