---
title: "Install a second ubuntu in different hard drive"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by primolarry on 2009-11-16
Hi there,

I'd like to install a second Ubuntu 9.04 for development purposes.

I've prepared a partition in my second drive, so both disk are now like this:

sda1: Windows
sda2: Ubuntu 9.04
sda3: data
sda4: /home

sdb1: swap
sdb2: free for new OS
sdb3: data

My question is, after installing the new Ubuntu in sdb2, how do I upgrade my grub in sda so I can boot both Ubuntus (apart from Windows)

Thanks a lot, regards

---

### Post by darkod on 2009-11-16
I'm quite new to Ubuntu but what I would do is: definitely instruct the second installation not to install grub. When you get to the last scren, before clicking Install there should be button Advanced. That will give you option not to install grub.

After the second installation is done you will boot into your first 9.04 as regular (the second one won't be in grub menu at all), and because both are the same version you should be able to simply copy the same text in menu.lst pointing to the correct partition on the second drive.

If I remember correctly, /boot/grub/menu.lst Just create another entry with the same text and then change the partition it is pointed to.

Edit it, reboot and you should be done. You can open menu.lst now to take a look and see what I am talking about. It's really simple.

PS. Where it says title that's the title that will show in grub menu. Add something to the entry you create for the second installation to make a difference from the first installation so you can tell them apart in grub.

---

### Post by primolarry on 2009-11-16
Thanks for the repply darkroad. Here's the menu.lst part of my current ubuntu 9.04:

> title		Ubuntu 9.04, kernel 2.6.28-13-server
uuid		8b5d792c-6fd3-41ed-ac89-db817fe0b5bf
kernel		/boot/vmlinuz-2.6.28-13-server root=UUID=8b5d792c-6fd3-41ed-ac89-db817fe0b5bf ro splash vga=794 
initrd		/boot/initrd.img-2.6.28-13-server
quiet

How can I find out the uuid of the partition where I am going to install the second ubuntu?

Thanks, regards

---

### Post by darkod on 2009-11-16
sudo blkid

will show you all drives all partitions and their uuid

I have done something similar with fedora years ago and it was my first experience with linux so it took me long to figure out what is kernel and to find the files and what you need to put in menu.lst. Now it looks easy and logical. :)

---

### Post by presence1960 on 2009-11-16
> **primolarry said:**
> Hi there,

I'd like to install a second Ubuntu 9.04 for development purposes.

I've prepared a partition in my second drive, so both disk are now like this:

sda1: Windows
sda2: Ubuntu 9.04
sda3: data
sda4: /home

sdb1: swap
sdb2: free for new OS
sdb3: data

My question is, after installing the new Ubuntu in sdb2, how do I upgrade my grub in sda so I can boot both Ubuntus (apart from Windows)

Thanks a lot, regards
when you install the new Ubuntu install GRUB to sdb2 not MBR by hitting advanced tab in the attached screenshot. This will install GRUB to sdb2 partition. Then boot Ubuntu and open terminal and run ```
gksu gedit /boot/grub/menu.lst
``` that is a lowercase L in .lst

Scroll down to bottom and add:

```
title         Ubuntu 9.04 develpment 
rootnoverify  (hd1,1)
chainloader   +1
```

click Save at top on toolbar & close file. reboot and try booting into the development 9.04 you just added. BTW in the title field you can name it anything you like.

---

### Post by presence1960 on 2009-11-16
oops forgot the screenshot. click advanced and it gives you options where to install GRUB. Put it on the partition /dev/sdb2

---

### Post by primolarry on 2009-11-16
Hi there,

Thanks to presence1960 and darkod for your useful posts. These are the steps that I followed

I installed 9.04, after rebooting I saw my old grub menu, so I could only boot my production Ubuntu and not my new development Ubuntu.

So I edited menu.lst and added a new block with the info of the development ubuntu.

I used "sudo blkid" to find out the UUID and I had to mount the development ubuntu partition to check out the name of the vmlinuz and initrd files.

Then I rebooted, entered into the development Ubuntu, install the desired kernel (in my case, 2.6.28-13-server), reboot again, boot into production and changue again the menu.lst to update vmlinuz and initrd:

> 
title		Ubuntu 9.04 Development
uuid		d84487e9-1c49-4be5-95ad-efe3b2e9064f
kernel		/boot/vmlinuz-2.6.28-13-server root=UUID=d84487e9-1c49-4be5-95ad-efe3b2e9064f ro splash vga=794 
initrd		/boot/initrd.img-2.6.28-13-server
quiet

So finally, it's working. Hope this post is useful to other.

Thanks again, regards

---

