---
title: "grub broke after update"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2010-01-05
I did a update of grub-pc through update-manager in KDE
After reboot I'm dropped to grub-rescue.
Have this happened any of you?
After some searching i found this thread.
[http://ubuntuforums.org/showthread.php?t=544881](http://ubuntuforums.org/showthread.php?t=544881)
However that is not for grub 2 but that might work anyway?

---

### Post by philinux on 2010-01-05
> **Tompalaz said:**
> I did a update of grub-pc through update-manager in KDE
After reboot I'm dropped to grub-rescue.
Have this happened any of you?
After some searching i found this thread.
[http://ubuntuforums.org/showthread.php?t=544881](http://ubuntuforums.org/showthread.php?t=544881)
However that is not for grub 2 but that might work anyway?

That wont work at all as it's for legacy grub.

This procedure will work from the live cd or a dual boot ubuntu.
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by ranch hand on 2010-01-05
I prefer these instructions although I think they are the same;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I prefer them as they are from within the community.  While there is a lot of good info out there on blogs most is just copied from elsewhere bu folks who have not, it seems, ever seen, let alone used, the system they are suddenly "experts" on.

Seeing as philinux posted the link it is probably a good one.  I posted this as there have been a lot of problems caused with grub2 by people using real shaky information from ignorant sources.  Try the community first.

---

### Post by VMC on 2010-01-05
> **ranch hand said:**
> I prefer these instructions although I think they are the same;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

That's the one I prefer also.

Funny how when people see things in print, books, newspaper, web, et., they tend to believe, but if they ask a question in person they may be more apt to question their authority.

---

### Post by phillw on 2010-01-05
We all have our favourites ... For me, Grub2 = drs305, so any of his are good to go (he writes some of the wikis, as well) Dave is very knowledgeable on what they're doing with Grub2. His basics one --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  Has a quick way to re-install grub2, but, as ever with any-thing written by him, it also includes to link to the community document (I'm not sure if that's one of his, as well).

I know the quick method works - I had to use it ;-)

Regards,

Phill.

---

### Post by Tompalaz on 2010-01-06
Thank you all for your answers.
Followed the links, they seemed be more or like the same thing.

When I'm supposed to run grub-install /dev/sda I get this error message:
> root@ubuntu:/# grub-install --recheck /dev/sda
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
/usr/sbin/grub-setup: error: If you really want blocklists, use --force.


I'm on a MacBook (5,1) could it be so that I need to install grub to the EFI partition somehow?

output from fdisk
> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39e96fca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26        4836    38636420   af  HFS / HFS+
/dev/sda3            4836        7948    25000000+  83  Linux
/dev/sda4            7948        8011      500000+  82  Linux swap / Solaris

Thanks

---

### Post by kansasnoob on 2010-01-06
> **Tompalaz said:**
> Thank you all for your answers.
Followed the links, they seemed be more or like the same thing.

When I'm supposed to run grub-install /dev/sda I get this error message:


I'm on a MacBook (5,1) could it be so that I need to install grub to the EFI partition somehow?

output from fdisk

Thanks

I know nothing about a MacBook so I'm just thinking out loud here. 

I have run across some corner issues where grub2 refused to play well but legacy grub worked fine, in particular some Toshiba laptops, and some (but not all) multi-drive systems.

If you wanted to try that I've written some notes:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

One thing I'd add is that if you're going to try reverting or reinstalling any grub or grub2 packages using a mount & chroot begin in the chroot by running "apt-get update" to be certain there are no problems with updating the package list.

I've run into that problem twice and it can be a pain to try and straighten things out. Basically I had to wget the .debs and then use dpkg to reinstall the packages, it turns a very simple job into a hair pulling event!

If you'd like some more individualized instructions I'll be glad to try, I should say however that i have no idea exactly what syntax would be required to add your other OS to grubs menu.lst :confused:

Feel free to send me a PM by clicking on my username, just keep it very brief and point me back here. I like to keep correspondence on the forums as it allows others to catch my mistakes, etc.

---

### Post by ranch hand on 2010-01-06
This does not make sense to me at all.  You are using Ubuntu 10.04-testing right?

This was a clean install not updated from 9.04?

If the answers to the above is "true" then I think that your grub has become corrupted in some very interesting fashion.

I think that the thing to do is chroot in from the live CD and remove grub-pc and grub-common.  Then install grub-pc and grub common.

---

### Post by Tompalaz on 2010-01-06
I have upgraded from Ubuntu 9.10 and download my updates from the main server.

I don't really understand what chroot means, is it that I can access my installation from a Live-CD? So if I'm running sudo apt-get update && sudo apt-get upgrade I will update the installation (while chrooted)?

Anyhow, I autoremoved grub-pc and grub-common. When I try to install it again it also install burg something, what is that? 

> root@ubuntu:/# sudo apt-get install grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 112 not upgraded.
Need to get 0B/1,624kB of archives.
After this operation, 4,575kB of additional disk space will be used.
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 219832 files and directories currently installed.)
Unpacking grub-common (from .../**grub-common_1.97+burg**.20091210-2~ppa5_amd64.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97+burg.20091210-2~ppa5_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.97+**burg**.20091210-2~ppa5) ...
Setting up grub-pc (1.97+burg.20091210-2~ppa5) ...
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
/usr/sbin/grub-setup: error: If you really want blocklists, use --force.

---

### Post by Tompalaz on 2010-01-06
Hurray!! From the help of you folks I managed to fix it.
What I did was that I first updated the system with sudo apt-get update && sudo apt-get upgrade then I removed grub-pc and grub-common with --purge. I answered yes to remove grub from /boot/grub.

When I installed it again I got to choose to witch disk I'd like to install grub, the only option was /dev/sda witch I already tried but thed got those strange errors.

However when I by mistake didn't chose a disk it didn't produce any errors :S

Happy alpha :P  

Thank you all for your help!

---

### Post by ranch hand on 2010-01-06
"Burg" is from a ppa that you must have added to your sources list, it has to do with theming in grub.

I am glad you got it working but you should mention "little" details like the burg ppa.

Good job.

---

### Post by nicolaas3 on 2010-01-16
> **ranch hand said:**
> I prefer these instructions although I think they are the same;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I prefer them as they are from within the community.  While there is a lot of good info out there on blogs most is just copied from elsewhere bu folks who have not, it seems, ever seen, let alone used, the system they are suddenly "experts" on.

Seeing as philinux posted the link it is probably a good one.  I posted this as there have been a lot of problems caused with grub2 by people using real shaky information from ignorant sources.  Try the community first.

I tried to do this, but with the mount command gives the message " mount: you must specify the filesystem type" 

Next you'll find what I did:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdce9ab7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1148     9216000   27  Unknown
/dev/sda2   *        1148       21203   161088512    7  HPFS/NTFS
/dev/sda4           21203       60802   318080024    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bac7578

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48053   385984000    7  HPFS/NTFS
/dev/sdb2           48054       59842    94695142+  83  Linux
/dev/sdb3           59843       60801     7703167+   5  Extended
/dev/sdb5           59843       60801     7703136   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb3 /mnt
mount: you must specify the filesystem type

---

### Post by ranch hand on 2010-01-16
Looks to me like you need to mount sdb2.

It is easier to chroot if you label your partitions.  Here is a copy of a script that I use to mess with this OS everyday;
```

#!/bin/sh

sudo mkdir /mnt/Daily-root
sudo mount /dev/sda13 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash

fi

```
That is for one of my 12 OS' on my test platform.  It is an external enclosure and my internals get turned off in bios before I go there.

I am on that drive right now using 10.04-testing.  The OS above is another 10.04 that I try updates and other modifications on before I try them on here to reduce breakage here.

If you edit the above file to have your correct sdb2 and then the correct label in all places with Daily-root in them it should fly.  It will also give you better access than the limited one you get with the chroot in the directions incase you want to run apt or something.

I would put it in a folder on your LiveCD and copy it to your desktop on your OS.  Then if you need it from the LiveCD again it is easy to get fro your install.

I assume you are wanting to install grub on sda which should be your boot drive.

---

### Post by VMC on 2010-01-16
> **nicolaas3 said:**
> I tried to do this, but with the mount command gives the message " mount: you must specify the filesystem type" 


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48053   385984000    7  HPFS/NTFS
/dev/sdb2           48054       59842    94695142+  83  Linux
/dev/sdb3           59843       60801     7703167+   5  Extended
/dev/sdb5           59843       60801     7703136   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb3 /mnt
mount: you must specify the filesystem type
That happened because you tried to mount the Extended partition, and not the logical one.
Are you trying to mount the Linux partition?

---

### Post by kansasnoob on 2010-01-17
> **nicolaas3 said:**
> I tried to do this, but with the mount command gives the message " mount: you must specify the filesystem type" 

Next you'll find what I did:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdce9ab7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1148     9216000   27  Unknown
/dev/sda2   *        1148       21203   161088512    7  HPFS/NTFS
/dev/sda4           21203       60802   318080024    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bac7578

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48053   385984000    7  HPFS/NTFS
/dev/sdb2           48054       59842    94695142+  83  Linux
/dev/sdb3           59843       60801     7703167+   5  Extended
/dev/sdb5           59843       60801     7703136   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb3 /mnt
mount: you must specify the filesystem type

It appears that sdb2 is your *buntu partition.

It would be helpful to know exactly what you are trying to do. 

What's broken?

How are you trying to fix it?

---

### Post by nicolaas3 on 2010-01-17
Grub broke after Ubuntu 9.10 update. After booting I'm now everytime running in  Rescue-Grub prompt. I'm using a dualboot U9.10 and Vista (Vista first installed).

After booting from U9.10 LiveCD and following the Grub Recovery instructions (see below) I can't mout the device with the Linux distribution (see below), I've to specify the  filesystem type. The only devices I can mount without this message are /dev/sda2   and /dev/sdb1
[FONT=monospace]Please help.
[/FONT]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdce9ab7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1148     9216000   27  Unknown
/dev/sda2   *        1148       21203   161088512    7  HPFS/NTFS
/dev/sda4           21203       60802   318080024    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bac7578

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48053   385984000    7  HPFS/NTFS
/dev/sdb2           48054       59842    94695142+  83  Linux
/dev/sdb3           59843       60801     7703167+   5  Extended
/dev/sdb5           59843       60801     7703136   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt
mount: you must specify the filesystem type

The command:  
[FONT=monospace]ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory

Gives also an error.
[/FONT]

---

### Post by kansasnoob on 2010-01-17
Well, since this is for Lucid testing, I'd recommend starting a new thread here:

[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

I'll try to help you but stop trying what you're trying before you break something even worse!

What I'll need from you first of all in that new thread is to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Just run it from the Live CD.

---

### Post by VMC on 2010-01-17
That is an excellent suggestion. That boot-info-script is a great tool. Especially if your having boot issues. They have updated recently to at least version 47. It now does a good job recognizing grub2 boot info.

---

### Post by nicolaas3 on 2010-01-17
I have just started a new thread with the results of the boot-script run attached.

---

### Post by ranch hand on 2010-01-17
A link would be nice.

---

### Post by nicolaas3 on 2010-01-17
Here you can find the new thread:
[http://ubuntuforums.org/showthread.php?p=8679392#post8679392](http://ubuntuforums.org/showthread.php?p=8679392#post8679392)

---

### Post by ranch hand on 2010-01-17
Thank you.

---

