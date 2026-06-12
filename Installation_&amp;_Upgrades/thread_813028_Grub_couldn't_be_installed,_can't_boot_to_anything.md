---
title: "Grub couldn't be installed, can't boot to anything"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by Relasz on 2008-05-30
Hi

As I was installing xubuntu the installer announced 'grub install failed, this is a fatal error'. I was installing it onto my laptop dualbooting with vista, and now I can't boot into anything except the live CD. I turn it on, and if there's not bootable CD inserted, it just tells me that 'there is no bootable devices'.

From there, I went back into the live CD and attempted to manually install grub - but since there's nothing in /boot/grub, it fails with "Not found or not a block device". grub-install gives me that message with every partition.

So, I attempted to install xubuntu on my external harddrive, so I could at least burn a Vista recovery DVD and get back to work, but the installation fails with the same message - 'grub install failed'. Now I can't boot off anything except the live CD and I can't restore the windows boot loader because I don't have Vista DVD.

Please, help. At this point, I will settle quite happily for just booting to windows.

---

### Post by Pumalite on 2008-05-30
How did you partition?. With Vista; you have to allocate space for Ubuntu with the Vista partitioner first. You cannot partition with the Ubuntu CD.

---

### Post by Relasz on 2008-05-30
When I installed Vista, it was installed of 1 of 2 partitions, the second being left for ubuntu. So no, I didn't create it with the ubuntu installer.

---

### Post by Pumalite on 2008-05-30
Are you installing Grub to the MBR?

---

### Post by Relasz on 2008-05-30
I'm not sure... if by that you mean 
```

sudo grub-install /dev/sda

```
it just comes back with 'Could not find device for /boot'. It does this for all possible sda* (/dev/sda1, /dev/sda2, etc).

---

### Post by Pumalite on 2008-05-30
Post:
sudo fdisk -l

---

### Post by Relasz on 2008-05-30
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7       30009   240999097+   7  HPFS/NTFS
/dev/sda3           30010       30401     3148740    f  W95 Ext'd (LBA)
/dev/sda5   *       30010       30401     3148708+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044e70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/sdb2            4257       30514   210917385    f  W95 Ext'd (LBA)
/dev/sdb5            5100       30514   204145956    7  HPFS/NTFS
/dev/sdb6            4257        5099     6771334+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

first drive is laptop drive, second is external. ubuntu is on /dev/sdb1 & /dev/sda5 (thats odd, the external ubuntu partion is showing up as ntfs now...)

---

### Post by Pumalite on 2008-05-30
You have to explain to me better what is the role of your external in this arrangement.

---

### Post by Relasz on 2008-05-30
I attempted to install ubuntu onto it so that I could burn a vista rescue disc, but it failed just like the one on the internal HD did. You can ignore it, if I can get the pc booting to Vista I won't need it.

---

### Post by Pumalite on 2008-05-30
Mount your partition:
sudo mkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
Post:
cat /media/sda5/boot/grub/menu.lst

---

### Post by Relasz on 2008-05-30
```
ubuntu@ubuntu:~$ cat /media/sda5/boot/grub/menu.lst
cat: /media/sda5/boot/grub/menu.lst: No such file or directory

```

---

### Post by Pumalite on 2008-05-30
I assume you are in your Live CD. Did you make the directory first? Did you mount then the partition? If so: then, reinstall

---

### Post by Relasz on 2008-05-30
Yes, I'm on the live CD. It's mounted correctly, I can manually go into the /media/sda5/boot/grub folder but there's no menu.lst there

---

### Post by Pumalite on 2008-05-30
Do sudo grub
find /boot/grub/stage1

---

### Post by Relasz on 2008-05-30
```
grub> find /boot/grub/stage1

Error 15: File not found

```

---

### Post by Pumalite on 2008-05-30
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by meierfra. on 2008-05-30
This will install Grub to the MBR and generate menu.lst


```

sudo mkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
sudo mount -t proc none /media/sda5/proc
sudo mount -o bind /dev /media/sda5/dev
sudo chroot /media/sda5
grub-install /dev/sda 
update-grub

```


Since installing grub failed during the Ubunutu installation, I'm not sure that this will work out. If it fails, report any error messages you got.

Also this won't let you boot into Windows, only Ubuntu. We'll worry about Windows later.

---

### Post by logos34 on 2008-05-30
> **meierfra. said:**
> 
```

sudo mkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
[B]sudo mount -t proc none /media/sda5/proc
sudo mount -o bind /dev /media/sda5/dev[/B]
sudo chroot /media/sda5
grub-install /dev/sda 
update-grub

```


Interesting.  Personally I use this:

> sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
**sudo mount --bind /dev /mnt/ubuntu/dev**
sudo chroot /mnt/ubuntu

Slightly more concise but works the same.

You don't actually need to chroot to run grub-install like you do for update-grub.  As long as you point it to (mounted) root dir:

sudo grub-install **--root-directory=/mount/point** /dev/hda

But there seems to have been some change in Hardy or sometime in Gutsy so that I can no longer use it if root is on a logical partition. I just get the message "/dev/hda? does not have any corresponding BIOS drive." (whether run from root on the hard disk or the live cd). Still works fine for primary partitions.  Maybe someone can confirm this.

---

### Post by meierfra. on 2008-05-30
> you don't actually need to chroot to run grub-install

I know.

> like you do for update-grub. 
That's  the point. The OP does not have a "menu.lst"  So "update-grub" was needed (last line of my code) And as long has one needs to "chroot", one might as well do "grub-install" inside the chroot, to avoid the "--root-directory"

> Hardy or sometime in Gutsy so that I can no longer use it if root is on a logical partition. I just get the message "/dev/hda? does not have any corresponding BIOS drive."

Haven't noticed that, but I will check it out. Usually one gets  "/dev/hda? does not have any corresponding BIOS drive." if /dev/hda is not listed in the device.map

---

### Post by meierfra. on 2008-05-30
deleted

---

