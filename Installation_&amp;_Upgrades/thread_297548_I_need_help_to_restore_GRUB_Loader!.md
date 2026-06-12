---
title: "I need help to restore GRUB Loader!"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by diekus on 2006-11-11
Hi.

I recently installed Windows Vista RC2 to check out Microsoft's new proposal for OSs... but the damn thing blew out the GRUB loader and I need to enter again to Ubuntu (6.06 Dapper).

Is there any way to restore GRUB and keep Vista and Dapper?

Thanks

---

### Post by Tyl3r on 2006-11-11
Boot from the live cd and use this sequence of commands:
```
sudo mkdir /mnt/root
sudo mount /dev/partition /mnt/root
sudo grub-install --root-directory=/mnt/root/boot /dev/partition
```

Where "partition" is the name of the partition with ubuntu, for example hda1, hda3, sda1, ecc...

---

### Post by diekus on 2006-11-11
don't pay atention to this. it works...

:D thanks



it says...

> 
ubuntu@ubuntu:/dev$ sudo grub-install --root-directory=/mnt/root/boot /dev/sda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda



but when i restart no grub... just damn vista...

---

### Post by dabotsonline on 2006-11-16
Hey guys, I have the following problem: [http://www.ubuntuforums.org/showpost.php?p=1763829&postcount=86](http://www.ubuntuforums.org/showpost.php?p=1763829&postcount=86)

Any suggestions?

Cheers

---

### Post by seshomaru samma on 2006-11-17
dabotsonline,
Try this:
Boot into the live CD 
open a terminal and run :
```
sudo grub
```
then:
```
[COLOR="Red"]find /boot/grub/stage1[/COLOR]
```
replace the question marks in the following command with the output of the last command :
```
root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
```

setup (hd0)
```
and
```
quit
```

---

### Post by dabotsonline on 2006-11-17
seshomaru samma, that worked perfectly, thank you so much!

---

### Post by gentlemanmasher on 2006-11-18
This works great.

---

### Post by ajmorris on 2006-12-21
alternatively install a boot loader such as Acronis. It acesses both windows and grub (and lilo), only problem is you have to re-install it when you re-install windows or linux.

---

### Post by andykrueger on 2006-12-23
Thanks a million for the instructions, seshomaru samma.  I just did a Windows reinstall today and thought it had wiped the Ubuntu partition when it vanished from GRUB, but this was all I had to do to get back in.  Cheers!

---

