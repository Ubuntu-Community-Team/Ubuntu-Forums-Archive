---
title: "Install Vista with Ubuntu?"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by D4Y.V on 2010-04-10
Hi, I'm not sure how to BEGIN. I have a disk for Windows 32bit Vista, and I just tried putting the disk in and running it through Wine, and it said something like "Not enough disk space; make room and retry install". I'm to afraid to install if from the Boot up menu... If possible I'd like to have a Duel Boot with both Ubuntu and Windows, because Windows is only really for games for me...
I'm not sure how to make my disk size smaller, I certainly don't have enough data on here to fill  250 GB... Is there a way to do this without wiping my Drive?
If ANYONE can help, I'd appreciate it.

---

### Post by SnickerSnack on 2010-04-10
Do you have only one partition?

Running "sudo fdisk -l" (that's the letter l [ell], not the number 1 [one]) from the terminal should let you know that.  Mine says 
```

zsharon@Weierstrass:~$ sudo fdisk -l
[sudo] password for zsharon: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xb6cc0bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         833     6297448+  27  Unknown
/dev/sda2   *         834       13159    93184000    7  HPFS/NTFS
/dev/sda3           13160       41346   213086129    5  Extended
/dev/sda5           13160       15239    15719571   83  Linux
/dev/sda6           15239       17318    15719571   83  Linux
/dev/sda7           17318       19397    15719571   83  Linux
/dev/sda8           19398       19953     4200966   82  Linux swap / Solaris
/dev/sda9           19953       24287    32764536   83  Linux
/dev/sda10          24287       41346   128961756    b  W95 FAT32

```
because I have device sda partitioned into several partitions.  There are 3 primary partitions: sda1 is the windows recovery partition, sda2 is the windows partition, and sda3 is an extended partition where linux is held.  sda5 through sda10 are logical partitions where linux (and also a large shared media partition) is stored.

I would guess that you don't have partitions set up for dual booting, so that is the first order of business.  However, resizing partitions is somewhat risking business afaik, and I can't help you with it since I don't know it well enough.  The last time I tried it, I ended up corrupting a bunch of files.

Unless someone more knowledgeable comes along to help with that, you may have to do a complete reinstall, setting the partitions first.  edit: by that, I mean that you may need to reinstall ubuntu, and during that install process, partition the drive.  It's not difficult; the installer is easy to use.

---

### Post by D4Y.V on 2010-04-10
I can't thank you enough for actually replying, in the past 13 topics I've made here asking for help on things, I've been replied to in 3 of them. thank you...

```
dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19290   154946893+  83  Linux
/dev/sda2           19291       19452     1301265    5  Extended
/dev/sda5           19291       19452     1301233+  82  Linux swap / Solaris
dave@dave-desktop:~$ 



```
This is what I've got, is there anything I can do from here? Do I have enough space?
If I reinstall ubuntu and change the size of the Partition thingy, would I keep my files that I have already on Ubuntu now? Then I can install Vista?

Any help appreciated again.

---

### Post by SnickerSnack on 2010-04-10
> **D4Y.V said:**
> I can't thank you enough for actually replying, in the past 13 topics I've made here asking for help on things, I've been replied to in 3 of them. thank you...

No problem.  I know what it's like as I have 2 or 3 threads right now with no responses.

> **D4Y.V said:**
> 
```
dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19290   154946893+  83  Linux
/dev/sda2           19291       19452     1301265    5  Extended
/dev/sda5           19291       19452     1301233+  82  Linux swap / Solaris
dave@dave-desktop:~$ 



```
This is what I've got, is there anything I can do from here? Do I have enough space?
If I reinstall ubuntu and change the size of the Partition thingy, would I keep my files that I have already on Ubuntu now? Then I can install Vista?

Any help appreciated again.

So, you have two primary partitions, one with linux, and the other with swap space.  Notice how sda5 in is the same place as sda2?

You're either going to have to resize partitions, or reinstall.  In the case of the former, I can't help you.  In that case of the latter, well, you'll have to backup your data.  This is one reason why I keep /home as its own partition, /dev/sda9 on my current laptop.  So, you need to backup your entire home directory somewhere, though an external harddisk is probably best.  Then, reinstall ubuntu and setup the partitions.  It isn't too hard, so just post here if you need help with that.

I'm going out for the evening, so I can't help you until tomorrow, though maybe someone else will in the meantime.

One thing I can say right now is that you need to have as much swap as you have RAM, you can only have at most 4 primary partitions, only one of those can be extended (to hold logicals), and I think you can have as many logicals as you want (or the max is just very high).

Good Luck.

---

### Post by D4Y.V on 2010-04-10
Thank you, kind sir. I can't believe your generosity.
So if I CAN resize the partition I will be able to is what your saying?
Well I don't have a device that can so much as hold 26.6Gb. I'm inclined to do the Latter.
Now, some way to resize the partition...
ANY HELP FROM ANYONE IS STILL WELCOME!

---

### Post by Mark Phelps on 2010-04-11
You're not going to be able to resize the partitions from inside Ubuntu because you have to unmount them to work on them.

You should first go to distrowatch.com, look for GParted down on the bottom right, click that link, click the download mirrors link, and under GParted LiveCD, click the Testing releases link, then click the gparted-live-05.205.iso link.  This will download an ISO file to your PC.  Open a PC burning app (probably have Brasero by default) and burn the image to a CD.

When you have that CD, you can boot from it and resize partitions because it doesn't mount any partitions.

Use it to shrink your Ubuntu partion to leave 30GB free for Vista.

You can not install and Windows OS using Wine.  So, you will have to boot from the Vista DVD to do the install.  When it boots, there will be a way to choose the unallocated space.  Use that to install Vista.

When done, you will lose the ability to boot Ubuntu because Vista will overwrite the MBR.  Post back here when done and folks will provide you directions on reinstalling GRUB.

---

### Post by D4Y.V on 2010-04-11
OK, thanks so much, I have the CD now, and I'm about to boot from it.
If anything goes wrong I'll reply through my PS3. Wish me luck!

---

### Post by D4Y.V on 2010-04-11
OK As i select Where I want to install Windows I select "Disk0 Partition 2" which is 30Gb and press next...
"Windows is unable to find a system volume that meets its criteria for installation"
...WHAAAAAAAAT?
I then resize the Partition to 40Gb but the same message comes up... 
Help... please...

---

### Post by oldfred on 2010-04-11
Is it a primary partition, formated NTFS and have the boot flag. Or is it totally empty space and a primary partition is available.

Edit some links, if older info be sure of version of grub to reinstall:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by SnickerSnack on 2010-04-12
> **D4Y.V said:**
> OK As i select Where I want to install Windows I select "Disk0 Partition 2" which is 30Gb and press next...
"Windows is unable to find a system volume that meets its criteria for installation"
...WHAAAAAAAAT?
I then resize the Partition to 40Gb but the same message comes up... 
Help... please...

Here's my current advice: if you have important data, borrow an extra HD (or USB drive) from someone you know, borrow someone's computer/internet for a few hours and download and burn an ubuntu live cd.  Then, make a backup of all important data before you do anything else.

From what you've posted, it sounds like you've done something wrong, and while it may be reparable, it's safest to backup your data first.

So, even if you have to take a few days to do that, it's better to do that now before doing anything else.  Also, you'll be able to show us the output of "sudo fdisk -l".

As mentioned above, windows will only install to a primary partition, and IIRC, it wants the first primary (or second if there's a "windows recovery" partition).  So, I think even if you have the right kind of partition, if it's listed after the linux partition, you may have a problem.  Though, if that is the only problem, it should be fixable.

---

### Post by D4Y.V on 2010-04-12
```
dave@dave-desktop:~$ sudo fdisk -l
[sudo] password for dave: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         489       14068   109081350   83  Linux
/dev/sda2           14069       19290    41943040    7  HPFS/NTFS
/dev/sda3           19291       19452     1301265    5  Extended
/dev/sda5           19291       19452     1301233+  82  Linux swap / Solaris
dave@dave-desktop:~$ 



```
This is what I got from a new sudo fdisk -l.
Is there any instruction from there, or anything?

---

### Post by oldfred on 2010-04-12
Linux/grub does not use a boot flag, windows has to have one, but some BIOS require a boot flag on a primary partition (assumes windows I guess).

You can use gparted, right click on sda2, and manage flags to put a boot flag on sda2.

---

