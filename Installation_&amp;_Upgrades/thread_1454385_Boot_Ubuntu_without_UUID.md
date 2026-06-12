---
title: "Boot Ubuntu without UUID"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by eldaria on 2010-04-14
Hello.

I installed Ubuntu 9.04 on My father-in-law's computer a while ago.
He has since then upgrade to 9.10, and yesterday he installed som according to updatemanager important updates, and he now has a broken system.

The tricky part here is that he lives far away, he does not speak English, and is not computer literate at all.
So all comunication with him goes through the phone and my wife translates.

But from what I have found, he get's a similair error to this that I found on the swedish ubuntu forum:
```

Begin : Waiting for root file system... ...
Done.
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)

ALERT! /dev/disk/by-uuid/fc2a95-a209-4e07-8d7c-ff84b2e5b531 does not exist. Dropping to a shell

(initramfs)


```

The UUID is different but the error is the same.

He does not have a live CD, so I need to get this system up and running so I can at least log in remotly.

Is there a way I can modify grub to boot with the /dev/sda instead of UUID. I tried to just modify it in the GRUB boot menu, during boot, but it will still drop me to a shell?

The reason is, that if I can just get the computer up and running, I can log in remotely and try to fix it.

---

### Post by -humanaut- on 2010-04-14
hmm... thats tricky My only suggestion would be to see if he can boot from an earlier kernel

---

### Post by drs305 on 2010-04-14
I'm not sure from your post if this is what you tried or not:

Toggle to the Ubuntu menu option.
Press "e", This should open up the commands for that menu entry.
Cursor to the start of the "search" line and hold down the DEL key until the entire line is removed.
On the "linux" line, change the "root=<uuid>" portion with "root=/dev/sdXY" , for example:

> linux	/boot/vmlinuz-2.6.32-19-generic root=/dev/sd**a5** ro   quiet splash

Once he has made the changes, CTRL-x to boot.

Note: There was a bug which caused all these error messages. The solution was to create an empty file on the partition. Unfortunately, you would need to boot to the LiveCD or find another way to mount the Linux partition. From the LiveCD (which I know he doesn't have), the procedure was to mount the linux partition and then create the file:
```
sudo mount -t ext**4** /dev/sd**xy** /mnt
sudo touch /mnt/testfile
```
Change to "ext3" if that is the format used.

If he does get into Ubuntu, Grub 2 has an option to not use UUIDs in the /etc/default/grub file. Uncomment the line > #GRUB_DISABLE_LINUX_UUID=true
and then run 
```
sudo update-grub
```

Good luck.

---

### Post by eldaria on 2010-04-14
> **-humanaut- said:**
> hmm... thats tricky My only suggestion would be to see if he can boot from an earlier kernel

I tried to select the previous kernel version 2.6.31-19 instead of 2.6.31-20, but it gave the same situation, only emergency shell.


> **drs305 said:**
> I'm not sure from your post if this is what you tried or not:

Toggle to the Ubuntu menu option.
Press "e", This should open up the commands for that menu entry.
Cursor to the start of the "search" line and hold down the DEL key until the entire line is removed.
On the "linux" line, change the "root=<uuid>" portion with "root=/dev/sdXY" , for example:



This Is what I tried, but it did not work, but I only tried /dev/sda and /dev/sda1 it could be that root is not on sda1, I honestly can not remember if I spli it in multiple partiions, it is a while ago.
What I do know is that fdisk -l does not work in busybox.  ;-) but I will try the other sda# also.


> **drs305 said:**
> 
Once he has made the changes, CTRL-x to boot.

Note: There was a bug which caused all these error messages. The solution was to create an empty file on the partition. Unfortunately, you would need to boot to the LiveCD or find another way to mount the Linux partition. From the LiveCD (which I know he doesn't have), the procedure was to mount the linux partition and then create the file:
```
sudo mount -t ext**4** /dev/sd**xy** /mnt
sudo touch /mnt/testfile
```
Change to "ext3" if that is the format used.

If he does get into Ubuntu, Grub 2 has an option to not use UUIDs in the /etc/default/grub file. Uncomment the line 
and then run 
```
sudo update-grub
```

Good luck.


I was able to mount sda1 from busybox, I tried this just to see if the filesystem was corrupt and this is why it could not be mounted.
Well i'm not sure if it mounted correctly, I got him to run a 
```
mount /dev/sda1 /
```
from busybox, and it did not give any errors and running just mount after, showed it on the last line.
I did not do any further investigations at the time, but I will try it again tomorrow when we will speak to him again.
If it works, I can at least see if it is the correct partition, and possibbly also correct it assuming busybox has a way of creating that file.

Thank you for the input, I will let you know if we got it working.

---

### Post by drs305 on 2010-04-14
> **eldaria said:**
> This Is what I tried, but it did not work, but I only tried /dev/sda and /dev/sda1 it could be that root is not on sda1, I honestly can not remember if I spli it in multiple partiions, it is a while ago.
Was it 'busybox' or the Grub terminal? If it's Grub, you can tell what drives/partitions Grub recognizes with the "ls" command. You can then explore the contents by expanding the ls command. Examples:
```
ls (hd0,1)/   # Displays contents of the / folder of sda1
ls (hd0,1)/boot  # Displays the available kernels and other boot files

```

> 
I got him to run a 
```
mount /dev/sda1 /
```
from busybox, and it did not give any errors and running just mount after, showed it on the last line.

From a prompt (but not a Grub 2 prompt):
Mount the partition on /mnt or on a new mount point, but not on /. 
```
sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test

```

---

### Post by eldaria on 2010-04-14
> **drs305 said:**
> Was it 'busybox' or the Grub terminal? If it's Grub, you can tell what drives/partitions Grub recognizes with the "ls" command. You can then explore the contents by expanding the ls command. Examples:
```
ls (hd0,1)/   # Displays contents of the / folder of sda1
ls (hd0,1)/boot  # Displays the available kernels and other boot files

```


Hmm, I just tried the ls command from the Grub terminal on a 9.04 machine, and it does not know the command.
I guess by grub terminal you mean pushing 'c' on the bot menu?

---

### Post by drs305 on 2010-04-14
> **eldaria said:**
> Hmm, I just tried the ls command from the Grub terminal on a 9.04 machine, and it does not know the command.
I guess by grub terminal you mean pushing 'c' on the bot menu?

Assuming it's a Grub 2 machine, and you have dropped to the G2 command line by pressing "c" at the Grub menu display, the "ls" command (lowercase L) should show the drives and partitions Grub 2 sees:  (hd0) (hd0,1) (hd0,5) (hd1) (hd1,1) etc

Your G2 prompt on a working system should be "grub>" or "sh:grub>".

You should be able to type "set" and see what modules G2 has loaded. You can also try "insmod normal" to load the "normal" kernel and "insmod linux" but these shouldn't be necessary to get G2 to work.

---

### Post by eldaria on 2010-04-15
Ok I got it working.

I was able to instruct him to modify the grub boot to get the computer up and running, so I could log in remotely.

After this I tried to run a fsck but this is of course not possible on a mounted volume, but fsck -n reported errors on disk, so ran sudo touch /forcefsck

I also ran a sudo update-grub

After reboot, the computer started up without any issues.

So I guess the update-grub was what fixed it, since the fsck would never run if grub was not able to start the computer correctly.

---

### Post by Bkock on 2010-04-15
I have installed ubuntu 10.4 beta 2 on a very basic AMD 1900+ CPU with 500MB
of RAM and a 160gb western digital HD. When loading I receive the following 
ERROR. 
-- I have noticed this problem has occurred in many previous versions. --

1. Any thoughts as to whether on not this will be fixed in the final release??

2. I have read fixes for previous versions with a different ver.GRUB, which 
   the GRUB required modification. What is the current thoughts for a fix
   in ubuntu 10.4 Please make it detailed as I am avid Windows user (sorry)
   but VERY new to Linux but willing to give it a try.
 
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules: ls /dev)

ALERT! /dev/disk/by-uuid/fc2a95-a209-4e07-8d7c-ff84b2e5b531 does not exist. Dropping to a shell

(initramfs)

---

### Post by drs305 on 2010-04-16
Edit: If you just had an update, see rudihawk's post below. The chances of an update going bad are higher than you having the bug discussed in this post. In addition to changing the UUID to "sdXY", you may need to remove the entire "search" line, which also contains a UUID reference.

> **Bkock said:**
> I have installed ubuntu 10.4 beta 2 on a very basic AMD 1900+ CPU with 500MB
of RAM and a 160gb western digital HD. When loading I receive the following 
ALERT! /dev/disk/by-uuid/fc2a95-a209-4e07-8d7c-ff84b2e5b531 does not exist. Dropping to a shell


Take a look at this page created by Meierfra that discusses a bug that produces this result.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix")

There are other causes but this is an excellent place to start.

---

### Post by rudihawk on 2010-04-16
I had the same issue today after updating my system. Fixed it by hitting "e" before the kernel booted from the grub menu.

Then changed the root= argument to

```
root=/dev/sdXX 
``` somehow all this got messed up in the update. 

That allowed it to boot in normally, where I was able to fix the problem properly (more updates, and edited my /etc/fstab)

For some wierd reason it refused to boot properly using UUID's and all my drives assignments got messed around. /dev/sda became /dev/sdc.

---

### Post by Bkock on 2010-04-23
I was able to remove the UUID at start up and inserted /dev/sda1 which allows the system to boot correctly but I noticed this is only a temporary fix. As I am very new to ubuntu / linux I would like to know what fix you performed in /etc/fstab  or how would I edit the grub file and save it so the system would use /dev/sda1 at boot.

Thanks

---

