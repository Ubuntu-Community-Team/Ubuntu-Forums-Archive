---
title: "Upgrade from 8.04 to 10.04 - ubuntu won't start up"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Bino on 2010-10-13
Since I noticed a new version of Ubuntu (10) was out and I was still running an old version (8.04) I thought about upgrading. With the update manager is selected update to 10.04 and everything went on it's way. 

During the process I got asked if I wanted to update the GRUB loader. Since I also use Windows and with a previous update of GRUB I couldn't start into it anymore I selected, "keep this version" (which I think is now causing this trouble).

The upgrade completed and restarted, however,  Ubuntu now doesn't start anymore.
I get prompted with:

mount: mounting none on /dev failed: No such device
udevd(896): error getting socket: Invalid argument
...

And the system just stops.

Any idea how to fix this?

edit: I started Ubuntu with the live CD and typed gedit /booot/grub/menu.lst which gave me a blank file. Is that normal?

---

### Post by Elfy on 2010-10-13
You need to mount the install first. 

```
sudo fdisk -l
```

get the partition the install is on then mount it somewhere - will be sdxy - where x is a letter and y a number

```
sudo mkdir /mnt/tmp
```

```
sudo mount -t ext3 /dev/sdxy /mnt/tmp 
```(change xy to suit)

```
gksudo gedit /mnt/tmp/boot/grub/menu.lst
```

---

### Post by Bino on 2010-10-13
From the menu.lst file the part that loads ubuntu

```
title		Ubuntu
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eb86d580-46c0-4459-9f73-9255dd49493f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
```

Is this correct? If not, to what do I need to change it to?

---

