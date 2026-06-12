---
title: "&quot;ALERT! /dev/hda8 does not exist.&quot; I can`t run Ubuntu 6"
date: 2006-04-14
forum: Installation &amp; Upgrades
---

### Post by wwwluckyro on 2006-04-14
Hello! This is the first time I`m trying to install linux and the first time to ever use linux.

I thought I`d give Ubuntu a try as some people recommended it to me. And the Screen Shots look really good :) I`m impresed.

Here is my history with Ubuntu:
**Monday**: downloading Ubuntu 5.1 Live CD - everything OK - Ubuntu freezes after start up sound. I can only see the Ubuntu logo
**Tuesday**: downloading Ubuntu 5.1  Install CD - everything OK - Ubuntu freezes during login screen.

After reading some treads from this site, I thought I`d try Ubuntu 6 beta.

I downloaded Ubuntu 6 beta, burned it with Nero at 4x. Install process went OK without any error. After reboot, I got the error attached.

**Alert! /dev/hda8 does not exist. Dropping to a shell!**

If anyone can give me any advice it would be great. Thank you.

Edit: I also attached a screen shot from partition magic for anyone who wants to see my HDD`s partitions.

---

### Post by wwwluckyro on 2006-04-14
Update! I reinstalled Ubuntu 6 and I got this error. Can anyone please help? :(

---

### Post by taurus on 2006-04-14
What is the output of this command then?
```

fdisk -l /dev/hda

```

---

### Post by wwwluckyro on 2006-04-14
fdisk: not found

---

### Post by taurus on 2006-04-14
Do you have a LiveCD handy around?  Boot from it and open a terminal and type this again...
```

sudo fdisk -l /dev/hda

```
The reason you need to include "sudo" this time because you want to run that command as root.

---

### Post by towsonu2003 on 2006-04-14
First of all, this sounds like a bad CD problem. make sure you checked the md5sum of the iso file you downloaded. If you have time and patience, burn it with 1x or 2x and try installing again... Otherwise, see below. 


I checked your partition screenshot ( [http://ubuntuforums.org/attachment.php?attachmentid=8302&d=1144998515](http://ubuntuforums.org/attachment.php?attachmentid=8302&d=1144998515) )
and there is no hda8 (or above) there. From what I see, these are your partitions: 
> 
hda1: windows (c)
hda2: extended (ignore)
hda3: programs (e)
hda4: share (f)
hda5: Linux ext3 (Root partition for Linux)
hda6: Linux swap
hda7: fat32 (i)

So, I will assume you have a live cd. Also, I may be wrong here, so try to wait for someone to notify something is wrong with what I'm telling you ;) Steps: 

1. Boot from live cd. If it gives you the GUI, fine. If it doesn't, does it drop you to command line? If it just freezes, following stes are obsolete... try hitting ctrl + c where it freeze and hit ctrl + alt + f1. If that doesn't work either, I'm clueless. Port yourerrors, if any...

2. Mount your linux root filesystem:
```

sudo mkdir /media/linuxroot
sudo mount /dev/hda5 /media/linuxroot -t ext3

```This should not give any output. 

3. Navigate to the root partition and change some files. Comments after sign # is for description only:
```

cd /media/linuxroot/boot/grub
sudo nano menu.list #editing menu.list with a text editor - it boots your windows and linux OS's
```
if file is empty, something is wrong. exit with ctrl + c and see what files there are with ls
in nano, check for lines that say "hd(0,7)". Depending on the operating system they refer to, change them to:
If referring to Windows, hd(0,0)
If referring to Linux, hd(0,4)
Save with ctrl + O (letter O) say yes and quit with ctrl + x
```

cd /mdeia/linuxroot/etc
sudo nano fstab #editing fstab, where partitions are mounted

```
again, if empty, something is wrong. 
Search for lines that refer to partitions like hda8 or hda9. They do not exist in your system. Change those lines according to info I gave above (partition name and what's in it). So for example, if it says somewhere
```

**/dev/hda8**       /fat32          **vfat**    defaults        0       0

```
change it to
```

**/dev/hda7**       /fat32          **vfat**    defaults        0       0

``` which is your only fat32 filesystem (in hda7). you are changing that line because you do NOT have a hda8 partition. 
Save with ctrl + O, say yes, exit with ctrl + x

This should fix things. Try rebooting (without live CD).

Please, before doing this (even if noone nofitied you that what I wrote was wrong), in case my instructions screw grub (hence screwing you Windows booting ability, boot from live cd and do: /sbin/grub-install /dev/hda
also, check out this wiki page: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows) 
which has informatio  on how to recover grub.

---

### Post by wwwluckyro on 2006-04-22
Sorry I didn`t respond earlier. I was busy with my new Intel Mac.
Anyway, I downloaded the latest beta of Ubuntu 6.06 - Desktop CD. And After booting, into Ubuntu, the Install program located on the desktop worked just fine. I`m writing this reply from Ubuntu :)
I like it. It`s cool.

Now I really have a problem: On windows, if I want to install a program, I run the .exe
But what do I run on Linux? I actually want to install GAIM 2 beta 3. Can anyone tell me what file is right for me from that long list? :) Thanks.

[Gaim 2 beta 3]("http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=405479")

Ubuntu is super cool!

---

