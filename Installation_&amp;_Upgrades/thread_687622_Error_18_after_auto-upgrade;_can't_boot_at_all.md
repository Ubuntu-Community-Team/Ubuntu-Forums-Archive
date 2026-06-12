---
title: "Error 18: after auto-upgrade; can't boot at all"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Scavok on 2008-02-04
I've been running Gutsy Gibbon since it was released and I've kept the software updated with the auto-update mechanism.

Today there were three updates, something about lib header files, which required a restart.

When the machine rebooted, this was displayed:


Error 18: Selected cylinder exceeds maximum supported by BIOS.
Press any key to continue...


When a key is pressed, I get a menu with three options:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+

The first two options yield the same result: Error 18 (same as before)

So at this point my PC has been rendered useless.

---

### Post by Pumalite on 2008-02-04
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Neuge on 2008-02-04
I had this problem with Feisty.  Every time the kernel was updated it for some reason changed the partition pointers in the grub files.  In other words, it was trying to boot from my /home partition.  I had to break out the Live CD and manually edit the grub files.

---

### Post by Pumalite on 2008-02-04
Run:
blkid
And compare UUID's with the ones in /etc/fstab and in /boot/grub/menu.lst

---

### Post by Neuge on 2008-02-04
> **Pumalite said:**
> Run:
blkid
And compare UUID's with the ones in /etc/fstab and in /boot/grub/menu.lstWhen I had this problem the UUIDs were fine, it just changed

```
root     (hd0,6)
```

to

```
root     (hd0,7)
```

in menu.lst.  That may not be exactly correct, I just remember the pointers were all one number off.

---

### Post by Scavok on 2008-02-04
> **Pumalite said:**
> [http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
Thanks for the link.

My BIOS has a hard-coded limit of 137447MB. Sigh.

If I boot from a Live CD, will I be able to access the hard drive so I can back-up my files before I attempt any fix?

---

### Post by Pumalite on 2008-02-04
Boot the Live CD. Go to the Terminal:
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/? /media/ubuntu
You can find out where Ubuntu is with:
sudo fdisk -lu

---

### Post by Scavok on 2008-02-04
> **Pumalite said:**
> Boot the Live CD. Go to the Terminal:
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/? /media/ubuntu
You can find out where Ubuntu is with:
sudo fdisk -lu

Here is the output:

```
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/? /media/ubuntu
**mount: special device /dev/? does not exist**
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000397b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   483861734   241930836   83  Linux
/dev/sda2       483861735   488392064     2265165    5  Extended
/dev/sda5       483861798   488392064     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```
The /dev/sda1 (my primary hard drive) isn't visible in Nautilus--although the hard disk I use for a backup is visible. (It's connected to the secondary IDE controller.)

Given that the BIOS has a hard coded 137GB limit and doesn't support LBA, what should I try next?
ubuntu@ubuntu:~$

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Boot with Livecd and then open terminal and try:

sudo mousepad /dev/sda1/boot/grub/menu.lst

This should work for you to edit the configuration file.

Also there is an option ("howmany=all") in menu.lst to make grub's menu show also earlier kernel images to boot from.

---

### Post by Scavok on 2008-02-04
> **Scavok said:**
> Here is the output:

```
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/? /media/ubuntu
**mount: special device /dev/? does not exist**
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000397b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   483861734   241930836   83  Linux
/dev/sda2       483861735   488392064     2265165    5  Extended
/dev/sda5       483861798   488392064     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```
The /dev/sda1 (my primary hard drive) isn't visible in Nautilus--although the hard disk I use for a backup is visible. (It's connected to the secondary IDE controller.)

Given that the BIOS has a hard coded 137GB limit and doesn't support LBA, what should I try next?
ubuntu@ubuntu:~$

My bad; the primary hard drive _is_ visible in Nautilus--it's called "backup". And my backup drive is visible, too--it's called "disk" :

/media/backup
/media/disk

I'm going to copy /media/backup/home to /media/disk/home so my documents are preserved in case I screw something up.

What I'm not understanding--and would like answers to--are:

1. Why did this automatic software update cause this problem in the first place? As I wrote in my OP, I've been using 7.10 since it came out--and now all of a sudden my PC won't boot? I understand my BIOS has a hard coded limit of 137GB--but what's that got to do with this s/w update/OS/whatever? Nautilus (and the terminal output shown above) correctly reports it's a 250GB drive. Did the OS somehow become so large that it exceeded a BIOS limit or what?

2. How does changing a Grub file--that was working fine until today--"fix" this issue? (IMO nothing was broken in the first place.)

Thank you very much for your patience and taking the time to respond to my questions. (I am really lost at this point.)

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Grub can let you to boot from different kernel images. It doesn't fix things, but it let you to boot from older kernel if new apears out of sudden incompatible with your hardware's setup. Also Ubuntu doesn't remove automatically old header files, when it installs new ones.

---

### Post by Scavok on 2008-02-04
> **Odrodzona-Sarmacja said:**
> Boot with Livecd and then open terminal and try:

sudo mousepad /dev/sda1/boot/grub/menu.lst

This should work for you to edit the configuration file.

Also there is an option ("howmany=all") in menu.lst to make grub's menu show also earlier kernel images to boot from.

The "howmany=all" is (was) already set in the file.

The Grub menu looks like the one in my OP. Two OS are listed; Neither one boots (as I wrote in my OP).

Thanks anyway.

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Maybe it locks old image file from being listed in boots options... Try enabling old entries in it. Also try enabling grub to show alternatives. The idea is that it should showthe boot option with older kernel. So you can boot your ubuntu on old kernel. It should look more or less like this:

Windows XP
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.22-generic
Ubuntu 7.10, kernel 2.6.22-generic (recovery mode)
Linux, kernel 2.6.21-generic
Linux, kernel 2.6.21-generic (recovery mode)
Ubuntu 7.10, memtest86+

You get the idea.

---

### Post by Scavok on 2008-02-04
> **Odrodzona-Sarmacja said:**
> Maybe it locks old image file from being listed in boots options... Try enabling old entries in it. Also try enabling grub to show alternatives. The idea is that it should showthe boot option with older kernel. So you can boot your ubuntu on old kernel. It should look more or less like this:

Windows XP
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.22-generic
Ubuntu 7.10, kernel 2.6.22-generic (recovery mode)
Linux, kernel 2.6.21-generic
Linux, kernel 2.6.21-generic (recovery mode)
Ubuntu 7.10, memtest86+

You get the idea.
There's nothing else in /boot to go back to! (Except what was listed in my OP--and neither of those worked.)

Ruined, I say! The update has ruined my installation! :mad:

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Do you have after the update in your grub directory two files called initrd.img-2.6.22-14-generic and initrd.img-2.6.22-14-generic.bak? I wonder... if one of them is the previous one. But I have no idea...

Actually I can't advise you nothing short of reinstalling ubuntu from lifecd and DO NOT update with the "latest" kernel after this. If you have /home partition, then you dont need copy this directory, so you can copy it back after the reinstall.

Good luck!

---

### Post by Scavok on 2008-02-04
> **Odrodzona-Sarmacja said:**
> Do you have after the update in your grub directory two files called initrd.img-2.6.22-14-generic and initrd.img-2.6.22-14-generic.bak? I wonder... if one of them is the previous one. But I have no idea...

Actually I can't advise you nothing short of reinstalling ubuntu from lifecd and DO NOT update with the "latest" kernel after this. If you have /home partition, then you dont need copy this directory, so you can copy it back after the reinstall.

Good luck!

```
ubuntu@ubuntu:~$ ls -l /media/backup/boot
total 17320
-rw-r--r-- 1 root root  424317 2008-02-01 08:00 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2008-02-01 08:00 config-2.6.22-14-generic
drwxr-xr-x 2 root root    4096 2008-02-04 18:49 grub
-rw-r--r-- 1 root root 7238852 2008-02-04 18:49 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7238801 2007-12-19 16:53 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-01 08:00 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1764472 2008-02-01 08:00 vmlinuz-2.6.22-14-generic
ubuntu@ubuntu:~$ 
```

Now the issue is: for menu.lst (current--unusable--menu.lst shown below), where do I find the UUID for the old (.bak) images?

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fea5ba30-1774-458a-a9ad-44c3a1641280 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fea5ba30-1774-458a-a9ad-44c3a1641280 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by confused57 on 2008-02-04
The kernel was upgraded from 2.6.22-14.47 to 2.6.22-14.51...I think what has happened is that the kernel update was placed outside the 137 Gb bios limitation that you have.  Your previous kernel booted OK, because it was located inside 137 Gb.

The link Pumalite provided has a guide for making a separate /boot partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

It may end up easier to back up your data & reinstall Ubuntu and make a separate /boot partition when you install or make a smaller root partition(approx 20 Gb) and the rest for /home & swap.

---

### Post by Scavok on 2008-02-04
> **confused57 said:**
> The kernel was upgraded from 2.6.22-14.47 to 2.6.22-14.51...I think what has happened is that the kernel update was placed outside the 137 Gb bios limitation that you have.  Your previous kernel booted OK, because it was located inside 137 Gb.

The link Pumalite provided has a guide for making a separate /boot partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

It may end up easier to back up your data & reinstall Ubuntu and make a separate /boot partition when you install or make a smaller root partition(approx 20 Gb) and the rest for /home & swap.
Using Nautilus or a terminal (sudo cp ...) to backup the folders within /home yields this error:

```
You do not have permissions to write to this folder.
```

The Properties->Permissions has Owner: 1000 and Group: 1000

Now what? (As you can tell I'm new to Linux.)

---

### Post by Scavok on 2008-02-05
> **Scavok said:**
> Using Nautilus or a terminal (sudo cp ...) to backup the folders within /home yields this error:

```
You do not have permissions to write to this folder.
```

The Properties->Permissions has Owner: 1000 and Group: 1000

Now what? (As you can tell I'm new to Linux.)

Figured it out (the backup part) on my own.

In GNOME, go to System -> Administration -> Users

Add a new user: entered my user name and password

Switched user and was able to access my primary and secondary drives so I could do the backup. Whew! What a relief!

I will probably have more questions after I finish the backup and start the re-partitioning of the primary drive so it's compatible with the 137GB BIOS limit. Speaking of the BIOS, I went to the Gateway site to see if a BIOS upgrade was available that would eliminate the 137GB limit. Well, Gateway has sub-contracted upgrades/updates/downloads to a company called MPC. When I entered my PC's serial number, MPC replied that it wasn't in their database and for me to re-try in 30 minutes. After an hour I retried and still NO JOY. They provided a toll-free number to call. Sigh. It's just one thing after another... So much for the "customer care."

---

### Post by Scavok on 2008-02-05
At this point I have backed-up /home, and Firefox's bookmarks.html

Now, pray tell, are my Evolution email contacts and emails?

What else should I backup before I try re-partitioning my primary hard drive?

---

### Post by confused57 on 2008-02-05
> **Scavok said:**
> At this point I have backed-up /home, and Firefox's bookmarks.html

Now, pray tell, are my Evolution email contacts and emails?

What else should I backup before I try re-partitioning my primary hard drive?
This may help:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

Nice job figuring out how to mount your partitions...

---

### Post by Scavok on 2008-02-05
> **confused57 said:**
> This may help:
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

Nice job figuring out how to mount your partitions...

[Inspector Clouseau voice]
Ah, the "Show Hidden Files" ploy.
[/Inspector Clouseau voice]

:)

Thank you very much!

---

### Post by Unterseeboot_234 on 2008-02-05
I too woke up after a Upgrade / Restart to find that I get to re-install Ubuntu. I've lost faith in the auto-upgrade. Thanks for this thread. I will try to rescue my files and contemplate a more stable version of Linux. Ubuntu has offered me a life-cycle of about 6 months maximum usage before re-install everything.

---

### Post by Scavok on 2008-02-05
> **Unterseeboot_234 said:**
> I too woke up after a Upgrade / Restart to find that I get to re-install Ubuntu. I've lost faith in the auto-upgrade. Thanks for this thread. I will try to rescue my files and contemplate a more stable version of Linux. Ubuntu has offered me a life-cycle of about 6 months maximum usage before re-install everything.
This was quite a shock for me--I had been running 7.10 flawlessly since it came out.

What are the odds of having a BIOS with the 137GB limit _and_ having 210GB of data on the drive, when the kernel update came along?

What really P.M.O. is: AFAIK there is no way to "undo" the kernel update--that is physically getting the kernel back the way it was _and_ under 137GB. (I'm not sure that's possible to do.) Sigh.

While I'm still backing up files, I still have to re-partition (or whatever) the primary hard drive. I'm wondering if I'll be able to do that w/o having to reformat/reinstall, or if I can use the partition editor to "move things around?" TBD

---

### Post by Unterseeboot_234 on 2008-02-05
Now, my error is not Error 18. My error has to do with BIOS timing (whatever that is). Load stops at "You may want to try nonAPIsafe. Keyboard does not work after that. The LibC headers are just poison, in my humble opinion.

---

### Post by Scavok on 2008-02-05
At this time I have backed up /home, /.evolution, and /.mozilla

I want to avoid having to redo my installation (esp. getting all the applications and settings redone). Now, since /home accounts for 176GB, I ask: would it be possible to (for example) delete /home, use gparted (or ?) to "move things around" and/or create the necessary (recommended) partitions (given the BIOS 137GB limit), and then reload /home--all without losing my existing applications and settings?

---

### Post by confused57 on 2008-02-05
> **Scavok said:**
> At this time I have backed up /home, /.evolution, and /.mozilla

I want to avoid having to redo my installation (esp. getting all the applications and settings redone). Now, since /home accounts for 176GB, I ask: would it be possible to (for example) delete /home, use gparted (or ?) to "move things around" and/or create the necessary (recommended) partitions (given the BIOS 137GB limit), and then reload /home--all without losing my existing applications and settings?
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000397b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   483861734   241930836   83  Linux
/dev/sda2       483861735   488392064     2265165    5  Extended
/dev/sda5       483861798   488392064     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$
```

Is this drive your root partition and your /home on the other IDE drive?  If that's the case, you "might" be able to just resize your root partition to less than 137 Gb, then create a data partition in the remaining space.  A root partition shouldn't need much more than 20 Gb.

---

### Post by anindya_m on 2008-02-05
It is a good idea to *always* have a small root partition (about 10 GB, maybe a bit more) to begin with, located at the beginning of the drive; /home in particular should have its own partition. This allows reinstallation of the OS (even another distro) without touching the user data/settings.

Do you have a big enough usb drive? Then you could back up onto it using the live cd and repartition the main drive.

---

### Post by Scavok on 2008-02-05
> **confused57 said:**
> ```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000397b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   483861734   241930836   83  Linux
/dev/sda2       483861735   488392064     2265165    5  Extended
/dev/sda5       483861798   488392064     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$
```

Is this drive your root partition and your /home on the other IDE drive?  If that's the case, you "might" be able to just resize your root partition to less than 137 Gb, then create a data partition in the remaining space.  A root partition shouldn't need much more than 20 Gb.

Rebooting with the i386 Desktop LiveCD and with one--and only one--hard disk installed (the one that I originally installed 7.10 onto), and running `sudo fdisk -lu' yields:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000397b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   483861734   241930836   83  Linux
/dev/sda2       483861735   488392064     2265165    5  Extended
/dev/sda5       483861798   488392064     2265133+  82  Linux swap / Solaris
ubuntu@ubuntu:~$
```

BTW: I'm a newbie and am not following your terminology ("root partition," "data partition," etc.). I'm not sure which tool to use (gparted?) or how to make these partitions. Thanks for your patience and sticking with me on getting this resolved.

---

### Post by Scavok on 2008-02-05
> **anindya_m said:**
> It is a good idea to *always* have a small root partition (about 10 GB, maybe a bit more) to begin with, located at the beginning of the drive; /home in particular should have its own partition. This allows reinstallation of the OS (even another distro) without touching the user data/settings.

Do you have a big enough usb drive? Then you could back up onto it using the live cd and repartition the main drive.
As I posted earlier, I have backed-up /home (177GiB) and /.evolution and /.mozilla onto another IDE drive (since removed from the PC for safe keeping).

I tried running gparted--no joy. Then I added me as a user and tried running it again--no joy.

And I don't know the terminal commands to use.

Anyway, as I understand the advice given so far, I should:

(1) delete /home--that will eliminate 177GiB of 183GiB in use--well below the BIOS limit of course. 
(2) Then I should do what? Create partition[s]? (What? How? GRUB? Boot? Root? My head is spinning!) 
(3) Resize partition[s]? (Which one[s]? How?) 
(4) Then create a separate (another) partition for /home?
(5) And eventually, copy the backed-up files back to /home.

Again, I'm a newbie so explicit instructions are needed. And I'd like to do this without having to reinstall all of the applications already installed and configured to my liking (if doing so is in fact possible).

---

