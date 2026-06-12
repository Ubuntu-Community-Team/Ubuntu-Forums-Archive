---
title: "Question on Wubi and hard disk space"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by iApex on 2010-03-16
Ok, here's the skinny..I installed Ubuntu onto my Windows machine via Wubi a few days ago. The install and everything were just peachy. When it asked me how much space I wanted to allocate Ubuntu, the default was 4GB, which I accepted. Now that I've been running ubuntu for a bit and love it, I want to know how I can increase the disk space for Ubuntu (I've gotten the "low disk space" message 4 times already) without adversly affecting either OS?

---

### Post by Elfy on 2010-03-16
You can resize the drive with LVPM - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Or you can move /home to it's own virtual drive - same link

General wubi wiki is here - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by iApex on 2010-03-16
> **forestpiskie said:**
> You can resize the drive with LVPM - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Or you can move /home to it's own virtual drive - same link

General wubi wiki is here - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Awesome, thanks for the help

---

### Post by iApex on 2010-03-16
> **forestpiskie said:**
> You can resize the drive with LVPM - [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Or you can move /home to it's own virtual drive - same link

General wubi wiki is here - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Awesome, thanks for the help

---

### Post by Witepa on 2010-04-16
Is it possible to resize the virtual drive using LVPM without making an extra partition, much like how partition managers like gparted resize physical partitions?

---

### Post by PhillyPhan627 on 2010-12-14
I stumbled across this thread while googling the same problem, and so I didn't think it would be necessary to create a new thread for the same problem.

I have been trying to deal with the space issue myself for 2 months now browsing various topics on this site and nothing seems to be working.  I followed the above instructions however when I copy 

> sudo sh wubi-add-virtual-disk /home 15000

into the terminal as the link specifies, I am greeted with 

> sh: Can't open wubi-add-virtual-disk

as a response.

When I installed Ubuntu via wubi I installed it with 20 GB of space.  I instantly loved Ubuntu way more than Windows and began the process of moving my files such as music over to Linux when now I am left with just under 1 GB of space.

---

### Post by PhillyPhan627 on 2010-12-14
I would like to add that I am fairly new with Ubuntu despite having it for about 2 months, but if you need any other information to help answer my question just ask and I will attempt to answer as best I can.

---

### Post by sanderd17 on 2010-12-14
did you download the file to your home directory?

If you don't know, post the output of 
```

ls -al

```

---

### Post by PhillyPhan627 on 2010-12-14
Alright so I moved the file like you said to my home folder and it worked and went through a list of all my files on Ubuntu, but I am a bit confused as where to go from here.  Like I said I am real new to using the terminal and getting around Ubuntu but I know some basics.

---

### Post by sanderd17 on 2010-12-14
you can just proceed and execute the 
```
sudo sh wubi-add-virtual-disk /home 15000 
```
command

---

### Post by PhillyPhan627 on 2010-12-14
Alright I let the command run through then rebooted my system like it recommended.  It says now that the virtual disk exists so now I guess my question is how do I go about acquiring space onto the new virtual disk?

---

### Post by sanderd17 on 2010-12-15
Isn't that automatically done? 

If I understand the script, it creates a new virtual disk and moves your /home to it (all your documents and settings). for safety it also creates a /home.backup. If you want room on your original disk, you just need to remove the /home.backup directory.

---

### Post by PhillyPhan627 on 2010-12-15
I'm really not sure.  I'm just trying to add space from Windows that I don't use, to Ubuntu since I only placed 20GB when I first installed Ubuntu using wubi.  When I checked the space available it still reads under a GB.

---

### Post by sanderd17 on 2010-12-15
wubi isn't my speciality, but could you post the output of the following 2 commands?

```

sudo parted -l
cat /etc/fstab

```

(it's an L after the parted)

---

### Post by PhillyPhan627 on 2010-12-15
The first command yielded this answer:

> Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1574MB  1573MB  primary  ntfs
 2      1574MB  250GB   248GB   primary  ntfs         boot


The second:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/host/ubuntu/disks/home.disk    /home    ext3    loop    0    0


---

### Post by sanderd17 on 2010-12-15
hmm, I hoped I could see the space of those partitions, but parted seems to list the real partitions and not the virtual.

the fstab shows there are 2 partitions in any case: a root and a home.

So the only possibility is that you forgot to delete the backup.

can I see the output of

```

ls -al /

```

---

### Post by PhillyPhan627 on 2010-12-15
> total 120
drwxr-xr-x  25 root root  4096 2010-12-14 15:53 .
drwxr-xr-x  25 root root  4096 2010-12-14 15:53 ..
drwxr-xr-x   2 root root  4096 2010-11-18 09:05 bin
drwxr-xr-x   3 root root  4096 2010-11-30 09:58 boot
drwxr-xr-x   2 root root  4096 2010-10-27 09:48 cdrom
drwxr-xr-x  18 root root  3780 2010-12-15 12:53 dev
drwxr-xr-x 137 root root 12288 2010-12-15 12:54 etc
drwxr-xr-x   4 root root  4096 2010-12-14 15:53 home
drwxr-xr-x   3 root root  4096 2010-10-27 09:48 home.backup
drwxrwxrwx   1 root root  8192 2010-12-08 10:39 host
lrwxrwxrwx   1 root root    33 2010-11-30 09:58 initrd.img -> boot/initrd.img-2.6.32-26-generic
lrwxrwxrwx   1 root root    33 2010-10-27 14:51 initrd.img.old -> boot/initrd.img-2.6.32-25-generic
drwxr-xr-x  17 root root 12288 2010-12-08 10:39 lib
drwxr-xr-x   7 root root  4096 2010-10-27 16:17 lib32
lrwxrwxrwx   1 root root     4 2010-10-27 09:45 lib64 -> /lib
drwx------   2 root root 16384 2010-10-27 09:44 lost+found
drwxr-xr-x   2 root root  4096 2010-12-11 17:07 media
drwxr-xr-x   2 root root  4096 2010-04-23 06:23 mnt
drwxr-xr-x   4 root root  4096 2010-11-29 02:31 opt
dr-xr-xr-x 175 root root     0 2010-12-15 07:53 proc
drwx------  13 root root  4096 2010-11-04 18:49 root
drwxr-xr-x   2 root root  4096 2010-11-30 09:55 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 17:25 selinux
drwxr-xr-x   2 root root  4096 2010-08-16 05:53 srv
drwxr-xr-x  13 root root     0 2010-12-15 07:53 sys
drwxrwxrwt  13 root root  4096 2010-12-15 12:55 tmp
drwxr-xr-x  11 root root  4096 2010-10-27 16:14 usr
drwxr-xr-x  15 root root  4096 2010-08-16 06:08 var
lrwxrwxrwx   1 root root    30 2010-11-30 09:58 vmlinuz -> boot/vmlinuz-2.6.32-26-generic
lrwxrwxrwx   1 root root    30 2010-10-27 14:51 vmlinuz.old -> boot/vmlinuz-2.6.32-25-generic


Ya i don't know if this helps but apparently it says I have no space, I can't save even small things like jpg pictures.  I should however have 964 MB remaining.

---

### Post by sanderd17 on 2010-12-15
As you can see, the home.backup directory is still there. Please remove it.
Press ALT+F2 and execute 
```

gksudo nautilus

```
to open the file manager in superuser mode. then go to the root directory and delete the home.backup folder. Check your trash bin (or how it is called in english) to see if it is there, if it is: empty the bin. Close nautilus afterwards.

---

### Post by PhillyPhan627 on 2010-12-15
Alright I removed the home.backup however I couldn't find it in the trash apparently it didn't go there hopefully it is still deleted.

---

### Post by PhillyPhan627 on 2010-12-20
I've noticed now that since I have done the before suggested terminal inputs my Linux side of my computer has deleted all of my icons and every boot up forgets my passwords for sites and for my wireless connections.  This is getting extremely frustrating, I just want to add more space to my Linux side of the computer and be done with this problem.

---

### Post by sanderd17 on 2010-12-20
for the icons, can you install other ones? like the ones from the elementary theme: [http://gnome-look.org/content/show.php/Elementary+Icons?content=73439](http://gnome-look.org/content/show.php/Elementary+Icons?content=73439)

and for the passwords and so, can I see the output of
```

ls -al ~/.mozilla

```

If I can't solve it, maybe use Chromium for a while.

---

### Post by PhillyPhan627 on 2010-12-20
I feel like the problem is that it says I have absolutely no space some how after the previous list of terminal commands even though in reality i have to have at least 1 Gb.


total 16
drwx------  4 frank frank 4096 2010-10-27 14:11 .
drwxr-xr-x 44 frank frank 4096 2010-12-20 14:20 ..
drwx------  3 frank frank 4096 2010-10-27 14:11 extensions
drwx------  4 frank frank 4096 2010-10-27 16:11 firefox

I really use Google Chrome for my browser over Firefox.

I'm just wondering if the creation of that other thing that I did last week was the reason all of my space has disappeared, it didn't seem to move any hard drive space from windows to ubuntu

---

### Post by sanderd17 on 2010-12-20
hmmm, I'm in troubles with wubi.

Normally, I would do the following: 

boot up a live CD, check if the /home directory is still in that place, if it's there, delete it.

But the problem is that you can't boot up a live CD to check out wubi's fake partitions. 

I'm sorry, but I don't know enough of Wubi to help you further.

---

### Post by PhillyPhan627 on 2010-12-20
Ya I guess I'll have to completely restart my computer if I want to use Linux and set it to factory defaults, no one seems to know how to solve this problem but thanks for your help.

---

### Post by sanderd17 on 2010-12-20
Are you considering a full install? with disk repartitioning?

I would recommend it, but do backup your files. The first time I had done an install, I chose "manual install" because I came from the windows world, and there I always wanted more control. But by choosing manual install without knowing a lot about partitions, I wiped them all.

---

