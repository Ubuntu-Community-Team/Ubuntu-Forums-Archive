---
title: "Trouble installing Karmic on Toshiba laptop"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by Theophylact on 2010-01-24
I have an older Toshiba Satellite 2415-S205 laptop (2 GHz Mobile Pentium 4, 1 GB DDR, brand new 160 GB hard drive). Installing the 32-bit version of Karmic seems to proceed normally, but when I reboot to run Ubuntu, I get the following:

error: no such device: 262a5e7a-26f3-4e04-9e43-2caec78e50b7

press any key to continue

This gets me to a GRUB menu, but any selection other than memtest returns the error.

I've done two installs with exactly the same result.

What's wrong? The laptop runs a brand new installation of Win XP Home SP2 just fine.

---

### Post by tachuela on 2010-01-24
Take a look at /etc/fstab and make sure you have the right UUID. Use your Live CD, mount the partition ('/') and edit the file. You can use 'mnt' or 'media'. Take a look with Gparted to know what to mount.

---

### Post by Theophylact on 2010-01-24
Sorry, you lost me there.

I can run the Live CD, but then what? What's the UUID? How do I mount "/"? Where (and what) is "gparted"? Do I run these sudo from console? 

(Right now it's irrelevant because I've reloaded Win XP, so it's all one NTFS partition anyway.)

---

### Post by kansasnoob on 2010-01-24
From:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> error: no such device: 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
This error is the result of a failure of the GRUB 2 search function. There are various bugs associated with the search function. To boot into your system, highlight the OS you want to boot. Press "e" to edit the menuentry. Delete the entire "search ..." line, then CTRL-x to boot.

Once you have booted into the system, you will modify the /usr/lib/grub/grub-mkconfig_lib file in accordance with this link:
Boot Problems:search

Link referred to:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

I know that's quite some reading but it works :)

---

### Post by tachuela on 2010-01-24
Once you boot the Live CD; you find Gparted under Administration. First run the following:
```
sudo fdisk -lu
```
Let's say that you find '/' in sda1; then:
```
sudo mkdir /media/sda1
```
```
sudo mount -t ext4 /dev/sda1 /media/sda1
```
```
sudo nano /media/sda1/etc/fstab
```
To find UUID:
```
sudo blkid
```

---

### Post by kansasnoob on 2010-01-24
> **tachuela said:**
> Once you boot the Live CD; you find Gparted under Administration. First run the following:
```
sudo fdisk -lu
```
Let's say that you find '/' in sda1; then:
```
sudo mkdir /media/sda1
```
```
sudo mount -t ext4 /dev/sda1 /media/sda1
```
```
sudo nano /media/sda1/etc/fstab
```
To find UUID:
```
sudo blkid
```

That will all be a waste of time. Refer to the links in my previous post please :)

---

### Post by tachuela on 2010-01-24
I learn every day

---

### Post by Theophylact on 2010-01-25
**kansasnoob**, sounds good. I'll try that. 

I've looked at [today's]("http://ubuntuforums.org/showthread.php?t=1312304") [posts]("http://ubuntuforums.org/showthread.php?t=1388766"), and this seems to be a generic problem with laptops and 9.10. Looks like there should be a sticky in this forum to deal with it.

---

### Post by Theophylact on 2010-01-31
Solved! Thanks, **kansasnoob**, that was the ticket; commenting out those three lines in grub did it.

---

### Post by Theophylact on 2010-01-31
The *real* problem seems to be that Karmic uses a version of grub2 that's still in beta. Not good for such an important part of an installation, especially for those who have to be talked into trying Linux for the first time.

---

