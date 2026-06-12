---
title: "Retrieve Data from Ubuntu"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2009-12-23
I am not able to boot into Ubuntu for some reason. Is it possible to retrieve the files through windows that I have saved on Ubuntu? Or is there any other method?
 
Thanks.

---

### Post by prshah on 2009-12-23
> **GeorgeOfTheBush said:**
> I am not able to boot into Ubuntu for some reason. Is it possible to retrieve the files through windows that I have saved on Ubuntu? Or is there any other method?
 

Yes. You can install the Ext2/3 IFS drivers from fs-drivers.org in Windows to access your Ubuntu partitions (if they exist).

Install [ext2/3 IFS drivers]("www.fs-driver.org/") in Windows (which will allow you access to linux partitions in Windows; be sure to enable "read-only" mode).

Alternately, you can use a live CD to boot to, then use that to access your Ubuntu partitions and copy your files.

---

### Post by zaphod777 on 2009-12-23
Live CD is easiest I think then copy to a USB drive.

---

### Post by GeorgeOfTheBush on 2009-12-23
Thanks a lot for your replies.
 
I forgot to mention that I have installed ubuntu through wubi on my winxp system on C:\ drive, on the same partition as windows. I have not created any partitions. Can I still access the linux files?
 
Thanks again.

---

### Post by MelDJ on 2009-12-23
> **GeorgeOfTheBush said:**
> Thanks a lot for your replies.
 
I forgot to mention that I have installed ubuntu through wubi on my winxp system on C:\ drive, on the same partition as windows. I have not created any partitions. Can I still access the linux files?
 
Thanks again.

since its through wubi, i guess installing the ext driver will not work as ubuntu is not on a ext filesystem. you can try the live cd though.
what error comes up when you boot ubuntu? have you tried doing a chkdsk?

---

### Post by prshah on 2009-12-23
> **GeorgeOfTheBush said:**
>  I have installed ubuntu through wubi on my winxp system on C:\ drive

Follow this guide [How can I access the Wubi files from Windows?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?") and [How can I access my Wubi install and repair my install if it won't boot?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?") on tips on how to access your files either through Windows or through the live CD.

---

### Post by avl555 on 2009-12-23
The whole ubuntu filesystem is in the filesystem.squashfs file, but i don't know exactly where. You can try C:\wubi\casper\.
Once you have found the file (the whole filesystem of the wubi installation) you need a live cd to recover the files.

So boot with the liveCD.
Then you have to open a terminal (**Applications>Accessories>Terminal**).
Type in the following lines and press enter after each line:
```
sudo mkdir /mnt/mydir
sudo mount filesystem /mnt/mydir -t squashfs -o loop
```If this succeeds (nothing happens) you can recover your files easily.
If it fails (for example, it says it can't mount a squashfs file system), then you have to report what exactly fails (copy the whole output).
If it says the file system is broken, there is anything serious wrong. It will be hard to recover.

If it succeeds, go to Locations>Computer.
If there's an icon called 'mydir', double click it and you can browse your files.
If not, Double click "filesystem", "dev", "mydir".

Now you are in a folder with directory's with short names (dev, root, usr etc.)
Double click "home".
And one of the directory's there should contain your files (I think there's only one).
Backup your files, for example, copy them to a USB stick, and shut down the computer.

you can also say what exactly doesn't work in Ubuntu. That may be much easier.

Now you have your files back, and can reinstall the wubi installation.
But wubi is not for daily use, only to test Ubuntu. If you want, you can try a "dual-boot".
That is, Ubuntu and Windows are really apart from each other.
But it's a bit hard to make a dual boot, and there is a very small change that you lose your files. But don't be afraid! It is better than a wubi installation. I have also a dual boot installation, just to save my Windows installation or if ubuntu doen't work.

---

### Post by prshah on 2009-12-23
> **avl555 said:**
> The whole ubuntu filesystem is in the filesystem.squashfs file, but i don't know exactly where. You can try C:\wubi\casper\.

The correct disk images are in \wubi\root.disk, home.disk, etc. They are not squashfs filesystems, but disk images.

Contents on squashfs filesystems are readonly.

---

### Post by GeorgeOfTheBush on 2009-12-23
ok. so is it possible to retrieve the linux files?

---

### Post by GeorgeOfTheBush on 2009-12-23
output of **sudo mount filesystem /mnt/mydir -t squashfs -o loop**
 
```
 
filesystem: No such file or directory

```
 
Other posts in the forum talk about fixing the sh:grub error as below.
 
```

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

```
 
Unfortunately I am unable to find any **vmlinuz-*** entry inside **/boot** directory.
Please help.

---

### Post by prshah on 2009-12-23
> **prshah said:**
> Follow this guide [How can I access the Wubi files from Windows?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?") and [How can I access my Wubi install and repair my install if it won't boot?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?") on tips on how to access your files either through Windows or through the live CD.

Did you try the links from post #6? Can you post back errors received?

---

### Post by GeorgeOfTheBush on 2009-12-23
To add to my worries, **root.disk **is missing now.

The last thing I did was to run **chkdsk /r** on windows. Now I am unable to find the root.disk at the location **C:\ubuntu\disks** where swap.disk is there.


I had around 30GB of free space b4 installing ubuntu thru wubi. Now the free space is back to 30GB. **Looks like chkdsk has erased root.disk.** What do I do now? Will I still be able to get my files?

---

