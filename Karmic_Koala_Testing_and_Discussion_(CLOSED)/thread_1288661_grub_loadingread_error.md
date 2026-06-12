---
title: "grub loadingread error"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by norm7446 on 2009-10-11
I have installed Karmic on a new 400Gig drive it has been working and loading Ok since install a couple of days ago. But now it will not boot at all. All I get is " grub loadingread error " with no error code to identify the problem.

Any HELP much apreciated......

---

### Post by kansasnoob on 2009-10-11
The only thing I can think of is that Grub needs reinstalling, but before I jump to conclusions would you please boot the Live CD, and running from the live desktop go to Terminal and post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

---

### Post by Zorael on 2009-10-11
That sounds like the grub in the bootsector can't find the grub on the harddrive, either because of changed device node order (/dev/sda1 is suddenly /dev/sdb1), because of changed UUIDs, or because the partition/partition table is borked.

---

### Post by norm7446 on 2009-10-12
Terminal: sudo fdisk -l

Result:


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000213bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47889   384668361   83  Linux
/dev/sda2           47890       48641     6040440    5  Extended
/dev/sda5           47890       48641     6040408+  82  Linux swap / Solaris

Does this tell you anything kansasnoob..

When I say New H/Drive it was only made on 5/10/09...

---

### Post by ranch hand on 2009-10-12
When you have the LiveCD booted, if you can read the files on the HDD, I would follow this;

 [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by kansasnoob on 2009-10-12
> **norm7446 said:**
> Terminal: sudo fdisk -l

Result:


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000213bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47889   384668361   83  Linux
/dev/sda2           47890       48641     6040440    5  Extended
/dev/sda5           47890       48641     6040408+  82  Linux swap / Solaris

Does this tell you anything kansasnoob..

When I say New H/Drive it was only made on 5/10/09...

That guide ranch hand posted is fine, but super simplified, just boot the Live CD and from the live desktop open the terminal and we'll mount and chroot your Ubuntu / partition (and reinstall grub2):

```
sudo mount /dev/sda1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

```
sudo chroot /mnt
```

```
grub-install /dev/sda
```

(If that spits any errors run):

```
grub-install --recheck /dev/sda
```

Then:

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev
```

```
sudo umount /mnt/proc
```

```
sudo umount /mnt
```

```
sudo reboot
```

Should that fail please try to post the output from terminal if it shows any errors.

BTW you can use the same method to run apt-get update, apt-get upgrade, etc. But you may need to use the additional command highlighted below to connect to the internet:

> ```
sudo mount --bind /proc /mnt/proc
```
**```
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```**
```
sudo chroot /mnt
```

Clear as mud?

---

### Post by norm7446 on 2009-10-14
I was just going to try kansasnoob's recommendation with the live CD, but the dam thing booted before I had a chance to get the live CD back in the drive. Dont know why but I is loading fine now !!!!!. Just one of those thing with computers I guess, a touch temperamental at time like everyone else. 

Really enjoying Karmic though now that it is back working..

---

### Post by ranch hand on 2009-10-14
WOW, better mark this as solved so folks know.

I would say you lucked out there.

Edit
I see that you did mark it, just old and blind.

---

### Post by supernova123 on 2009-10-15
I am having the same error, I get "cannot find list of partitions":

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo choot /mnt
sudo: choot: command not found
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
```

and for the record:

```

root@ubuntu:/# fdisk -l

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8eb98eb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         490     3935893+  83  Linux

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a4a12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          79      634536   82  Linux swap / Solaris
/dev/sdb2              80        1962    15125197+   5  Extended
/dev/sdb5              80        1962    15125166   83  Linux
```

Cheers for any help :)

---

### Post by ranch hand on 2009-10-15
Well I can see why you want to set it for sdb.  I think you may have trouble booting sda1.

Your command grub-install /dev/sdb seems to have worked.

Did you try booting after doing this?

I am just on the way out the door for 2 days of processing and shipping calves.  Be back Saturday.

HAVE FUN.  I will.

---

### Post by eris23 on 2009-10-16
I'm also facing "Cannot find list of partitions!".

---

