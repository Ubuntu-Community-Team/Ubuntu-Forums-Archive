---
title: "New way to install. Can it be done without ever having a cd."
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by rick3878894 on 2008-03-11
"New way to install, maybe?" Can it be done without ever having a cd. I am currently running Damn Small Linux (dsl) and have all of the ubuntu cd files (I decompressed them from the iso) on a small partion. I want to know if there is a way for me install from there or from the internet. Any ideas? If you do plaese be as detailed as you can I am not so... educated.


:guitar:

---

### Post by Jimmey on 2008-03-11
Try [this]("https://help.ubuntu.com/community/Installation?highlight=%28install%29")

---

### Post by rick3878894 on 2008-03-11
The link isn't working bro. could be something that requires cookies.

---

### Post by rick3878894 on 2008-03-11
It may also be my browser. If you can post what your trying to get me to that be awsome.

---

### Post by Jimmey on 2008-03-11
The Live CD is also known as the "Desktop Installer". It is the default Ubuntu installation CD. The ISO you downloaded has the name "desktop" in its name, these are the instructions to use. If your ISO has "alternate" in its name, you are using an alternate installation CD and should see the next section. 

UNetbootin is an installer that can do the following automatically. It is available for download at  [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html). 

If you already have a working linux system, installing without external media is easy. You need to create a new partition, copy the CD contents over to it, boot from the new partition, and proceed as if you were installing from a CD. Note that you can't use what will be the root partition for the CD contents, as the installer is stubborn on formatting it (it will fail). 

The benefits of installing without external media are that it can save you time if you are already familiar with the process, and you get a very usable system upon booting into the installer because it is running from a hard drive rather than a CD. 

Step 1. Use gparted to create a new primary partition and format it to ext3. You need slightly more than 700MB of free space on it. 750MB should be sufficient. Let's say the name of the partition is /dev/sda1. If your new ubuntu install is going to coexist with your old system, you might find it convenient to create space for your new system as well at this point using gparted. 

Step 2. Copy CD contents over to the new partition using the command 

 mkdir /tmp/install_cd
 mount ubuntu-7.04-desktop-i386.iso -o loop /tmp/install_cd
 mkdir /mnt/installer
 mount /dev/sda1 /mnt/installer
 cp -r /tmp/install_cd/* /mnt/installer
 cp -r /tmp/install_cd/.disk /mnt/installer
 umount /tmp/install_cd
Replace the name of the iso to whatever you downloaded and /dev/sda1 with whatever your new partition is. 

Step 3. Edit your grub configuration file (typically /etc/grub.conf or /boot/grub/menu.lst) to boot from the new partition by adding the lines 

title installer
        root (hd0,0)
        kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
        initrd /casper/initrd.gz
The first line after the title tells grub which partition contains the installer. hd0 stands for "first hard disk," and the 0 following it standards for first partition. You will need to change this if your installer partition is different from /dev/sda1. sdaN becomes (hd0, N-1), sdbN becomes (hd1,N-1) and so on. As you can see, grub starts counting from 0, which can be confusing. 

Step 4. Reboot, and choose "installer" from the grub boot menu, and continue as if you were installing from CD.

---

### Post by AndyCee on 2008-03-11
Odd. Works for me.

Try this way:

Ubuntu.com -> Community (top of page) -> Documentation (in "Help and information) -> community contributed documentation -> Installation (in "Getting ubuntu")

The page is https, so possibly the problem is due to a browser setting disabling secure http.

Oh, and you've already been answered. Oh well...

---

### Post by rick3878894 on 2008-03-11
hda1 is the first partion write?

---

### Post by Jimmey on 2008-03-11
first partition of the first drive, I'm pretty sure

---

### Post by rick3878894 on 2008-03-12
I tryed and it said file not found. Is there some steps that I can take to trubleshoot at it?

I can't firue out how to run UNetbootin ethier.

---

### Post by zvacet on 2008-03-12
You can try to find partition with 

```
gedit /etc/fstab
```

or 

```
sudo fdisk -l
```

---

