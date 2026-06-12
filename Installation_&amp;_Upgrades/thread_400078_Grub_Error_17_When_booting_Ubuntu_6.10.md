---
title: "Grub Error 17 When booting Ubuntu 6.10"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by BlobbDobb on 2007-04-03
Hi,
This is my first time using Linux.
My install was not the easiest. But I struggled through (I'm sure its been worth it!) The problems started that I was not able to run the LiveCD (I use ATI RADEON X700 Graphics card, Ubuntu tries to use the ATI driver, when it should be using radeon or flgrx) So, when I finally got that working I realised that I didn't want GRUB on my MBR. (I already have a partition boot manager on my MBR “BootIt NG”. Allowing GRUB to overwrite my MBR would mean I might have been unable to use all the features that are available in BootIt. So, I downloaded the Alternate CD (Which was surprisingly difficult to find) and installed GRUB onto the Partition that I had created from Bootit and installed Linux onto (I used the Ext3 filesystem) I did not have enough partitions left to create a Swap partition. Here is a list of my partitions:

hd0 (I have one hard-drive)
MBR – BootIt NG : FAT
2  - Ubuntu/Grub : Ext3
3  - File Storage for XP : NTFS
4  - Windows XP Home Edition

I reboot and when BootIt opens I boot Ubuntu. This brings up GRUB, well, a command-line version of GRUB. So, I had NO idea what to do. I tried some logical commands first (Boot = Error cannot boot until Kernel loaded, Kernel = Filename/command/directory does not exist etc.) then I read somewhere to try putting in Root. So I typed in Root (hd0,1) (worked my way through the numbers) most of them brought up errors, (hd0,1) didn't so I typed it again. However, it did not have Any response. It didn't bring back an error, but neither did it bring back any positive feedback. Then, just out of luck or exasperation I hit the 'Esc' key, which brought me to GRUB's Boot menu. I tried booting  “Ubuntu, kernel 2.6.17-10-generic” and it didn't work, bringing back error 17 and “Cannot mount partition”. So Then I tried the Recovery and Mem. Test Partitions. Recovery and Mem. Test both worked. When I booted Recovery I put “startx” into the commandline and Voila, I got the GUI.

Of course, this is a very big pallaver (Ulsterism for Hassle) to go through to boot Ubuntu.

What I would basically like to do is just to hit (not literally) Ubuntu in BootIt and then for it to start booting. If the GRUB thing is a necessity then I suppose I could bear that, but having to key in “root (hd0,1) and then startx” is quite annoying.

I looked in my Menu.list to see what could be causing problems but I can't work out what difference makes the Recovery bootable and the Normal not.

Here are their entries in my menu.list file.
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

Any help is much appreciated – Any chance I can just delete the Grub directory or something, and have it boot without it? GRUB isn't really necessary, seeing as I have BootIt installed (And yes, I would rather have BootIt than have GRUB, no offence)

Thanks very much,
I'm really looking forward to using Ubuntu, (If I get the boot working!)
Congrats on all the work, the operating system (once installed ;-) ) is really user friendly compared to what I was expecting.

---

### Post by BlobbDobb on 2007-04-04
I can't help but wonder if anyone is gonna post some help? There have been over 80 views and not a single reply, am I just a hopeless case? Does anyone need more information. If no-one replies I think I'll just fire away and delete the /boot/grub directory or something...

---

### Post by geirha on 2007-04-04
I can't see anything wrong with that grub-config either. But since you get error 17 which means it's unable to mount the partition, perhaps there's an error with the filesystem. You should try booting the livecd and run **sudo fsck.ext3 /dev/sda2** from a terminal.

To get more than 4 partitions you need to have one partition as an extended partition. You could achieve this by removing your linux-partition (since you can't use ubuntu yet I guess) and create an extended partition in it's place, then on the extended partition you can make lots more (logical) partitions. I'm not 100% sure if the extended partition needs to be the last partition though, in such a case you would have to move the windows partitions to the left first. In any case, if you would choose to try this, you'll probably have to use your windows recovery cd to make windows boot again.

As for deleting /boot/grub, I'm not sure if that would work, because next time a kernel update ticks in, it will try to create two sections in menu.lst for the new kernel. This would fail I think, and maybe also the update will fail...

---

### Post by BlobbDobb on 2007-04-04
> **geirha said:**
> I can't see anything wrong with that grub-config either. But since you get error 17 which means it's unable to mount the partition, perhaps there's an error with the filesystem. You should try booting the livecd and run **sudo fsck.ext3 /dev/sda2** from a terminal.

To get more than 4 partitions you need to have one partition as an extended partition. You could achieve this by removing your linux-partition (since you can't use ubuntu yet I guess) and create an extended partition in it's place, then on the extended partition you can make lots more (logical) partitions. I'm not 100% sure if the extended partition needs to be the last partition though, in such a case you would have to move the windows partitions to the left first. In any case, if you would choose to try this, you'll probably have to use your windows recovery cd to make windows boot again.

As for deleting /boot/grub, I'm not sure if that would work, because next time a kernel update ticks in, it will try to create two sections in menu.lst for the new kernel. This would fail I think, and maybe also the update will fail...


Thanks very much. I will try running the live CD command. Does anyone know if there are any GRUB forums out there? Do I need a swap partition?

---

### Post by geirha on 2007-04-04
Don't think you actually need it, but I think you get a little better performance. And having an extended partition there will keep the option open for installing more operating systems in the future, by resizing/moving the existing ones.

I had a look at the site of the boot loader you are using. Did you use this guide for installing ubuntu? [http://www.terabyteunlimited.com/kb/article.php?id=279](http://www.terabyteunlimited.com/kb/article.php?id=279)

---

### Post by BlobbDobb on 2007-04-05
I tried doing fsck.ext3 /dev/sda2 and it did do something, but all that has changed is that my Ubuntu partition is now Unbootable (no matter what I try to boot from) Now, when I type sudo fsck.ext3 /dev/sda2 in the terminal of the live cd the only return i get is "ubuntu@ubuntu:~$ sudo fsck.ext3 /dev/sda2
e2fsck 1.39 (29-May-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>"

Any idea as to what is wrong now?

Edit: NOOooOOOOooooOO! I have just lost both my Ubuntu and my Data storage partitions. They are completely corrupt now. Ok, if there has ever been a time I've wanted to give up its been now, but I'll wait a while longer to see if anyone comes to help. (Speaking of which, I would give you good Karma geirha if this forum had it enabled.)

---

### Post by geirha on 2007-04-05
> **BlobbDobb said:**
> Edit: NOOooOOOOooooOO! I have just lost both my Ubuntu and my Data storage partitions. They are completely corrupt now. Ok, if there has ever been a time I've wanted to give up its been now, but I'll wait a while longer to see if anyone comes to help. (Speaking of which, I would give you good Karma geirha if this forum had it enabled.)

How did that happen? after running fsck on the ubuntu-partition? It could sound like the harddrive is about to crash or something. The result of the filesystem check was not very positive at least. Does it physicaly make any weird noices? How does **sudo fdisk -l /dev/sda** look from the livecd?

---

### Post by BlobbDobb on 2007-04-05
No, its from running the sudo fsck.ext3 /dev/sda2 from the terminal. It made the usual noises a hard drive makes when doing any sort of intensive work, but nothing that made me take notice. I will try sudo fdisk -l /dev/sda from the live CD next.

---

### Post by BlobbDobb on 2007-04-08
To make things a bit easier, I'm going to buy a second Hard Drive for my computer, so any commands I run will be less likely to cause any damage to existing partitions. So, what should I do on my second install attempt?

---

