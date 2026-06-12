---
title: "Kernel Issues"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by bootbat on 2010-02-14
Hello All,

I feel like a complete n00b at this point. I was careless and deleted the Kernel using synaptic package manager. I was trying to delete the older entries but did not realize that I also selected the current one. Thus, I do not get an option to boot to Karmic at GRUB. It only shows the memtest entry and Windows XP.

So I booted using the Ubuntu 9.10 LiveCD and tried the following:

1. sudo su

2. mkdir /mnt/os

3. mount /dev/sdb /mnt/os

At this point, I keep getting the following error:

[PHP]mount: /dev/sdb already mounted or /mnt/os busy[/PHP]

I tried rebooting, making a different directory to mount my sdb to but it keeps repeating the same message again and again. I need to be able to boot to the drive. Any assistance will be greatly appreciated. Please let me know if you need anymore information.

---

### Post by darkod on 2010-02-14
First, you need to be aware of linux marking for disks/partitions.
/dev/sda, /dev/sdb, etc are disks. You can't mount it like that. If it has a number that is marking the exact partition on that disk.
So, you could mount /dev/sda1, or /dev/sda5 for example. Now it depends which partition is your root partition, you need to mount it.
I have no idea how to add a kernel even if you mount it. Have you found some tutorial?

---

### Post by phillw on 2010-02-14
@ darkod - you get his partition mounted for him - lol

To the OP, can you please post the result of ```
sudo fdisk -l
``` So we can see what you have on your hard drive(s)

Once we have the correct partiton mounted you'll needs to run ```

sudo apt-get install linux-image
``` to get a new kernel and, I guess do an update of grub.

```
sudo update-grub
```

Regards,

Phill.

---

### Post by darkod on 2010-02-14
> **phillw said:**
> 

Once we have the correct partiton mounted you'll needs to run ```

sudo apt-get install linux-image
``` to get a new kernel and, I guess do an update of grub.

Regards,

Phill.

Someone has been deleting kernels. :D

PS. And the OP will need to chroot I guess, if I understand it right. Just mounting doesn't allow you to install it.

---

### Post by phillw on 2010-02-14
> **darkod said:**
> Someone has been deleting kernels. :D

PS. And the OP will need to chroot I guess, if I understand it right. Just mounting doesn't allow you to install it.

Not found anything on chrooting, mind you I've never not had any kernel at all to boot from :-\

Regards,

Phill.

---

### Post by bootbat on 2010-02-14
Thank you all for your help. Here are the results for fdisk:

[HTML]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07512eb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4869    39110211    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a9e9a9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris[/HTML]

So I understand that I need to mount /dev/sdb1. I did that and also completed 

[HTML]root@ubuntu:/home/ubuntu# chroot /mnt/os[/HTML]

Do I need to: [HTML]sudo apt-get install linux-image[/HTML] now?

---

### Post by phillw on 2010-02-14
I'd give that a go - It'll sharp complain if it is not happy !!

Assuming that goes okay, do the update of grub, whenit is rebuilding the .cfg file, you should see the entry for linux kernel added to it - If it does not add it, then it hasn't worked !!

Regards

Phill.

---

### Post by darkod on 2010-02-14
I think there were few more commands to run before chroot. To fully mount /dev/sdb1, you would need to:

mount --bind /proc /mnt/os/proc
mount --bind /dev /mnt/os/dev
mount --bind /sys /mnt/os/sys
After that run chroot and the install command.

---

### Post by bootbat on 2010-02-14
Thanks Phill. Here's what I get - 

```
ubuntu@ubuntu:~$ sudo apt-get install linux-image
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  linux-image
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,152B of archives.
After this operation, 32.8kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com karmic/main linux-image 2.6.31.14.27 [3,152B]
Fetched 3,152B in 0s (3,944B/s)    
Selecting previously deselected package linux-image.
(Reading database ... 120319 files and directories currently installed.)
Unpacking linux-image (from .../linux-image_2.6.31.14.27_i386.deb) ...
Setting up linux-image (2.6.31.14.27) ...
```

I think this is not right..Shouldn't it download the latest one? linux-image_2.6.31.14.27_i386.deb sound old to me.

Anyway, I tried:

```
root@ubuntu:/home/ubuntu# sudo update-grub
grub-probe: error: cannot find a device for /.
```

It didn't rebuild the GRUB 2 .cfg file. Does not go through for some reason.

Any ideas?

Thank you for your help already.

---

### Post by bootbat on 2010-02-14
I think we got this figured out. I tried Darko's suggestion. Here's what I get now:

```
root@ubuntu:/home/ubuntu# mount --bind /proc /mnt/os/proc
root@ubuntu:/home/ubuntu# mount --bind /dev /mnt/os/dev
root@ubuntu:/home/ubuntu# mount --bind /sys /mnt/os/sys
root@ubuntu:/home/ubuntu# chroot /mnt/os
root@ubuntu:/# sudo apt-get install linux-image
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image is already the newest version.
The following packages were automatically installed and are no longer required:
  firefox-3.6-branding
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Debian background: B-1B_over_the_pacific_ocean.tga
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-generic (2.6.31.19.32) ...
Setting up linux-image (2.6.31.19.32) ...
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
Generating grub.cfg ...
Found Debian background: B-1B_over_the_pacific_ocean.tga
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```

Let me reboot and let you all know. 

Thank you once again. You guys rock!!

---

### Post by phillw on 2010-02-14
> **darkod said:**
> I think there were few more commands to run before chroot. To fully mount /dev/sdb1, you would need to:

mount --bind /proc /mnt/os/proc
mount --bind /dev /mnt/os/dev
mount --bind /sys /mnt/os/sys
After that run chroot and the install command.


Cheers darkod - I'm going to make a note of this one !!!!

Phill.

---

### Post by rahilm on 2010-02-14
don't forget to mark this thread as SOLVED if you succeed.

---

### Post by bootbat on 2010-02-14
Phill, Darko.

Sending you guys a beer each:-). Thank you so much for your help today. This has been solved now. Appreciate all your help and assistance.

---

### Post by bootbat on 2010-02-14
Hey rahilm....I marked it in the subjectline...Do I need to do anything else?

---

### Post by rahilm on 2010-02-14
Actually, there is a link called "Thread Tools" just above the thread , If you click it, a list comes down, there you will find the option to Mark the Thread as SOLVED

---

### Post by darkod on 2010-02-14
Yeah, I remembered those commands from reinstalling grub2 tutorials. If grub.cfg exists and is correct, you only need to mount the root partition and reinstall. But if you need to recreate grub.cfg you need those three commands too so you can fully chroot into your install.
I also remembered them from when kansasnoob is helping someone remove/install grub and I figured you had to do them for remove/install of packages to work. :)
Glad you got it sorted.

---

