---
title: "Problem booting... busybox v1.15.3 (ubuntu 1:1.13.3-1ubuntu1)built_in shell(ash)"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Goroman on 2011-02-05
Hi,  
Can somebody help me with this booting issue I am having. 
2 days ago I turned my computer on and I could not enter to desktop as usually. The computer showed a message on a black screen that ended with:

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) 

...I couldn't do anything else. I don't want to loose my not backed up info.
I googled the error and I found that I could boot from a live cd so I downloaded Ubuntu 10.10 and boot it from livecd... Now I am running firefox from livecd trying to fix this error.

I note that /dev/sda1 my main partition is not mounted, so I have tried to mount it from gparted and from terminal and I am unable to do it...

I don't know if the error I am getting on when booting is because of sda1 is unmounted, but I would like anyone to help me.

I found a similar case here [http://ubuntuforums.org/showthread.php?t=1558343&page=4](http://ubuntuforums.org/showthread.php?t=1558343&page=4) but** "bcbc" **user recommend me to open a new post.

Hope anybody out there can help me.

---

### Post by Goroman on 2011-02-05
> **Goroman said:**
> Hi,  
Can somebody help me with this booting issue I am having. 
2 days ago I turned my computer on and I could not enter to desktop as usually. The computer showed a message on a black screen that ended with:

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) 

...I couldn't do anything else. I don't want to loose my not backed up info.
I googled the error and I found that I could boot from a live cd so I downloaded Ubuntu 10.10 and boot it from livecd... Now I am running firefox from livecd trying to fix this error.

I note that /dev/sda1 my main partition is not mounted, so I have tried to mount it from gparted and from terminal and I am unable to do it...

I don't know if the error I am getting on when booting is because of sda1 is unmounted, but I would like anyone to help me.

I found a similar case here [http://ubuntuforums.org/showthread.php?t=1558343&page=4](http://ubuntuforums.org/showthread.php?t=1558343&page=4) but** "bcbc" **user recommend me to open a new post.

Hope anybody out there can help me.

When I try to mount  device manually I get:
ubuntu@ubuntu:~$ sudo mount /dev/hda1 (MY UNMOUNTED PARTITION)
mount: can't find /dev/hda1 in /etc/fstab or /etc/mtab

How can I proceed?

---

### Post by bcbc on 2011-02-05
When you turn on the computer, hold down the SHIFT key and the grub menu should show. Then select an older kernel.

Or boot the live CD and download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the output here. 

While you're figuring out the bootinfoscript you can give us the output of 
```
fdisk -l
```
(that's a small L)
and 
```
ls /boot
```

---

### Post by Goroman on 2011-02-06
> **bcbc said:**
> When you turn on the computer, hold down the SHIFT key and the grub menu should show. Then select an older kernel.

Or boot the live CD and download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the output here. 

While you're figuring out the bootinfoscript you can give us the output of 
```
fdisk -l
```(that's a small L)
and 
```
ls /boot
```


YOU ARE THE MAN!!! As simple as a SHIFT Key to save my life.

Thank You very much...

---

### Post by bcbc on 2011-02-06
> **Goroman said:**
> YOU ARE THE MAN!!! As simple as a SHIFT Key to save my life.

Thank You very much...

Ah, good to hear!

Sometimes it seems the kernels don't get updated properly (or the post install generation of the initial ram disk). 

It's possible to repair "sudo update-initramfs -u -k <kernel_version>" (but this didn't seem to work for everyone - see "man update-initramfs" for more info). 

Or maybe uninstall the bad kernel or override the default boot option so you don't have to do it manually each boot.

---

### Post by rblloren on 2011-02-26
I got similar problem too. But I was not able to savor all your instructions.
Already had a copy of ubuntu 10.10 and burnt it in cd, is this the liveCD your talking?.

If it is, I already tried and it and still was not able to login and could not see the partition and could not work on the GRUB.
Help! :)

---

### Post by dwllui on 2011-03-01
Hi guys, I have a similar problem described here. Would anyone have any idea how to resolve this?

[http://ubuntuforums.org/showthread.php?p=10509980#post10509980]("http://ubuntuforums.org/showthread.php?p=10509980#post10509980")

---

### Post by thehad on 2011-03-01
Solved a similar problem (ubuntu 10.04). At startup, after an upgrade, I got a black screen with this text:

No init found. Try passing init= bootarg.
BusyBox v1.13.3 ...jada jada..
(initramfs)

I was not able to start a previous kernel nor was I able to start in safe mode.

This solved my problem:
Restart computer with a live-Cd.
Open a terminal window.
At the command prompt, write:
sudo fsck -f /dev/sd??

You must change sd?? to something else.
I used sdb6, simply because that is where my system is installed. Use the command "sudo fdisk -l" to find your system partition unit name. Maybe it is sda3 or sdb2 or sda1 or something else!? You may also use system/administration/disktools to find out what unit sd?? to use.

Run the fsck-command described above and then restart. Voila, everything works! Run a system update.

See also
[http://www.uluga.ubuntuforums.org/showthread.php?t=1549842&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1549842&page=2)
or
[http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=52672](http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=52672)

---

### Post by dwllui on 2011-03-01
Thanks for your response. But my current problem is booting into the live cd itself kicks me out to busybox with initramfs: unable to find medium containing live file system. As you can see here [http://ubuntuforums.org/showthread.php?p=10509980#post10509980]("http://ubuntuforums.org/showthread.php?p=10509980#post10509980"), I have verified that the live cd works on other computers and I have also checked that the md5sum is correct. 

Right now, I can boot into Windows 7 without any problems, but recovering the partition installed with Ubuntu using the disk management is not possible and booting in Ubuntu using the livecd gets me into busybox. Tried various other methods such as GParted, Parted Magic, but all seems to be failing.

---

### Post by thehad on 2011-03-01
> **dwllui said:**
> Thanks for your response. But my current problem is booting into the live cd itself kicks me out to busybox with initramfs: unable to find medium containing live file system. As you can see here [http://ubuntuforums.org/showthread.php?p=10509980#post10509980]("http://ubuntuforums.org/showthread.php?p=10509980#post10509980"), I have verified that the live cd works on other computers and I have also checked that the md5sum is correct. 

Right now, I can boot into Windows 7 without any problems, but recovering the partition installed with Ubuntu using the disk management is not possible and booting in Ubuntu using the livecd gets me into busybox. Tried various other methods such as GParted, Parted Magic, but all seems to be failing.

Ok, I understand. Unfortunately I can not help you there. Historically these issues have also occured with multiple disk installations. Anyway, 
a longshot is to shut off the ACPI setting in BIOS. Also, dubbelcheck that the Cd-rom is the startup disk in BIOS. Good luck!

---

### Post by thehad on 2011-03-01
Live Cd not working.
If you get as far as to the grub menu, then try different boot options.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by moody_mark on 2011-11-16
> **thehad said:**
> 
I was not able to start a previous kernel nor was I able to start in safe mode.

This solved my problem:
Restart computer with a live-Cd.
Open a terminal window.
At the command prompt, write:
sudo fsck -f /dev/sd??

See also
[http://www.uluga.ubuntuforums.org/showthread.php?t=1549842&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1549842&page=2)
or
[http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=52672](http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=52672)

I know this is an old-ish thread, but just wanted to say thanks to the above poster, this helped me fix a friend's PC, was running Ubuntu 10.10 their desktop froze and they pulled the plug. This must have corrupted some data on the disc, anyway, I booted with a knoppix DVD, run fdisk -l to find the partition name and then fsck /dev/sda1 (change for your disc), and after a few fixes, we were back in business. Thanks!

---

### Post by r3delmasry on 2011-12-17
hello
i have this error but in my USB 
i cant start ubuntu from my usb 
any help please ?

---

### Post by elijahmuha on 2012-02-02
> **thehad said:**
> Solved a similar problem (ubuntu 10.04). At startup, after an upgrade, I got a black screen with this text:

No init found. Try passing init= bootarg.
BusyBox v1.13.3 ...jada jada..
(initramfs)

I was not able to start a previous kernel nor was I able to start in safe mode.

This solved my problem:
Restart computer with a live-Cd.
Open a terminal window.
At the command prompt, write:
sudo fsck -f /dev/sd??

You must change sd?? to something else.
I used sdb6, simply because that is where my system is installed. Use the command "sudo fdisk -l" to find your system partition unit name. Maybe it is sda3 or sdb2 or sda1 or something else!? You may also use system/administration/disktools to find out what unit sd?? to use.

Run the fsck-command described above and then restart. Voila, everything works! Run a system update.

See also
[http://www.uluga.ubuntuforums.org/showthread.php?t=1549842&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1549842&page=2)
or
[http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=52672](http://www.ubuntu-se.org/phpBB3/viewtopic.php?f=200&t=52672)

This worked for me as well on an installation of Ubuntu Server 10.04 LTS.  Thanks for the help!

---

