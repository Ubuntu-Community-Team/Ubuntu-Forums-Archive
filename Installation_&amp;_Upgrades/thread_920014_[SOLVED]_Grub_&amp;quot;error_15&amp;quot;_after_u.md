---
title: "[SOLVED] Grub &amp;quot;error 15&amp;quot; after upgrade to 8.04"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by jordan28 on 2008-09-14
Yesterday, I upgraded my Gutsy system to 8.04, using update manager to fetch and install the files. As prompted, I tried to reboot my system, however when trying to load the kernel (2.6.24-19-generic) the following appears:

Error 15: File not found

I return to the grub menu and have several other kernel options, but they all return the same error message. I can only access the command line.

How can I get my system to boot? Do I need to alter my menu.lst file? During the upgrade process, I was asked if I wanted to install the new version of menu.lst over the existing locally edited version. I chose the new. I am running Ubuntu as my only OS on my Laptop, and do not have a liveCD. 

Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-09-14
OK, if you can boot up your Live CD, open a terminal, and do:
```
sudo fdisk -l
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Post the results of the above, and I think we should have enough info to get your Ubuntu booting again.

---

### Post by jordan28 on 2008-09-14
Thanks for your help, however I do not have a live CD - I upgraded through update manager. As far as I know, my only options are the command line within grub.

---

### Post by caljohnsmith on 2008-09-14
OK, I think we can still get your Ubuntu going again. Reboot, and when you get the Grub boot menu, press "c" to get the Grub CLI. Then do:
```
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), remember what it is. Next do:
```
grub> reboot
```
Now in the Grub menu, select your first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)", press "e" to edit it, change the (hdX,Y) to be whatever you got from above, press return to save the change, and then press "b" to boot. That should work assuming that the rest of the Ubuntu entry is correct. Let me know how it goes.

---

### Post by jordan28 on 2008-09-14
When I enter  "grub>find /boot/grub/stage1" in the CLI, I get the same 'Error 15: File not Found' message

This is the present command for booting the 2.6.24.19-generic kernel:

```
root (hd0,2)
kernel /boot/vmlinuz-2.6.24.19-generic root=UUID=f92f34a9-cc78-4a1-8fbf-987221fbf987 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
```

So I assume you mean that I should replace the UUID with the details of my Ubuntu partition? I already tried inserting the text "(hd0,2)" for UUID, but it didn't change anything. If I could find the numbers for my ubuntu partition another way should it work?

---

### Post by caljohnsmith on 2008-09-14
Well, if you are getting a Grub menu on start up, you should be able to at least locate the menu.lst in the Grub CLI:
```
grub> find /boot/grub/menu.lst
grub> find /grub/menu.lst
```
One of those should return the (hd0,X) for your Ubuntu partition.

---

### Post by jordan28 on 2008-09-14
Yes, grub> find /grub/menu.lst

returns

(hd0,2)

However, when I go to edit the CLI entry to boot the kernel, the root (hdX,Y) line is already in the form (hd0,2). Here it is:

```
root (hd0,2)
kernel /boot/vmlinuz-2.6.24.19-generic root=UUID=f92f34a9-cc78-4a19-8fbf-987221fbf987 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
```

---

### Post by caljohnsmith on 2008-09-14
OK, we're making progress. Try next:
```
grub> find /boot/vmlinuz-2.6.24.19-generic
grub> find /boot/initrd.img-2.6.24-19-generic

```
It should find those files on (hd0,2) of course. If it doesn't, try maybe an earlier vmlinuz and initrd file, such as the 2.6.24.18-generic or earlier.

---

### Post by Ptero-4 on 2008-09-14
> **jordan28 said:**
> Thanks for your help, however I do not have a live CD - I upgraded through update manager. As far as I know, my only options are the command line within grub.

I think he was talking about your gutsy liveCD (or the one of whatever ubuntu release you installed from scratch).

---

### Post by jordan28 on 2008-09-14
Ok, Here is what I'm getting:
```

grub> find /boot/vmlinuz-2.6.24.19-generic

Error 15: File not found

grub> find /boot/initrd.img-2.6.24.19-generic

Error 15: File not found
```

And when I try for earlier kernel versions in my menu list:

```
grub> find /boot/vmlinuz-2.6.22.15-generic

Error 15: File not found

grub> find /boot/initrd.img-2.6.22.15-generic

Error 15: File not found
```

And so on and so forth for the other 2 versions in my menu list:

2.6.20.17-generic
2.6.20.16-generic

---

### Post by jordan28 on 2008-09-14
Thank you Ptero, that makes sense. Unfortunately, I am living abroad and didn't think to bring my live CD. It seems it would take 6-10 weeks to ship a liveCD. If you or anyone else has any suggestions on how I can get my system up and running that would be appreciated. It seems that reinstalling my OS is an option from the grub menu, and while my most important files are backed-up, it would be nice not to be forced to use that option.

---

### Post by Ptero-4 on 2008-09-15
> **jordan28 said:**
> Thank you Ptero, that makes sense. Unfortunately, I am living abroad and didn't think to bring my live CD. It seems it would take 6-10 weeks to ship a liveCD. If you or anyone else has any suggestions on how I can get my system up and running that would be appreciated. It seems that reinstalling my OS is an option from the grub menu, and while my most important files are backed-up, it would be nice not to be forced to use that option.
Are you on a DellBuntu? or a System76 PC? If so you might want to re-post at the Dell, or System76 subforums.

---

### Post by jordan28 on 2008-09-15
Yes I am on a DellBuntu. Here's a recent development that may be relevant:
```

grub> null (hd0,
Possible partitions are:
Partition num: 0, Filesystem type unknown, partition type 0xde
Partition num: 1, Filesystem type is fat, partition type 0xb
Partition num: 2, Filesystem type is ext2fs, partition type 0x83
Partition num: 4, Filesystem type unknown, partition type 0x82
Partition num: 5, Filesystem type is ext2fs, partition type 0x83

grub> find /vmlinuz
 (hd0,1)

grub find /sbin/init
 (hd0,5)

grub> null (hd0,5)/
Possible files are: lost+found boot bin cdrom dev etc home initrd initrd.img lib media mnt opt proc root sbin srv sys tmp usr var vmlinuz initrd.img.old vmlinuz.old

```

This seems to tell me that root partition is in partion (hd0,5) Also, then the following is the boot script for the latest kernel version. This is what my Grub is trying to run:

```
root (hd0,2)
kernel /boot/vmlinuz-2.6.24.19-generic root=UUID=f92f34a9-cc78-4a19-8fbf-987221fbf987 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
```

I see that root is pointed to the partion (hd0,2) Is this significant? Does it mean that some of my necessary boot files need to be moved to a different location? I'm reading up on the Grub shell, but not sure how to proceed. Any further input would be greatly appreciated.

---

### Post by caljohnsmith on 2008-09-15
Sorry I couldn't respond sooner; I think what's going on is you have two linux partitions, (hd0,2) and (hd0,5), and it looks like (hd0,2) is probably just a dedicated Grub partition, while your main Linux install is on (hd0,5). I have a hunch that all you need to do is change the "root (hd0,2)" in your Ubuntu Grub entry to use (hd0,5) and that might be all it takes to boot your Ubuntu. Give that a try first and we can work from there.

---

### Post by jordan28 on 2008-09-15
Problem Solved. (At least I was able to get it boot this one time.)

By looking around in my Hard-drive partitions, I found out that my root folder system was in a different hard-drive partition. Also, I found out that I needed to bypass my /boot directory, because my vmlinuz file was in my root folder system. 

Instead of running

[INDENT]root (hd0,2)
kernel /boot/vmlinuz-2.6.24.19-generic root=UUID=f92f34a9-cc78-4a19-8fbf-987221fbf987 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
[/INDENT]
I ran the following

```
root (hd0,1)
kernel /vmlinuz-2.6.24.19-generic root=UUID=f92f34a9-cc78-4a19-8fbf-987221fbf987 ro quiet splash
initrd /initrd.img-2.6.24-19-generic
quiet
```

And it booted. I'm wondering if now that I've booted I need to change the locations of my vmlinuz and initrd.img files to prevent future errors. Thanks to those that pointed me in the right direction!

---

### Post by caljohnsmith on 2008-09-15
Glad you got Ubuntu to boot. :) So it looks like all your Ubuntu boot files are located on your sda2 (hd0,1) FAT partition. I wouldn't know why they would be there when you have a /boot directory in your main Ubuntu install sda6 or (hd0,5). Also your Grub files are located on sda3 or (hd0,2). Before you go any further, be sure to modify your /grub/menu.lst on your sda3 partition with your changes so you don't have to manually modify your Grub menu every time on start up.

I personally would move all your boot files from sda2 over to /boot on sda6 to consolidate them. It's certainly not necessary, but I can't think of any reason why you would need to leave them on sda2 in case you want your boot files with the main Ubuntu install.

---

