---
title: "Successful: moving Ubuntu to external usb disk"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by ItalOz on 2009-12-07
I have successfully installed 9.10 on to an external HD.
After having configured and played around with it for a while I decided that I like it.
But before moving it into the internal HD of my laptop I have decided to move my old 8.04 to the external HD as well, so that I could always have it back if something goes wrong or if some application does not work as before.

So I logged into my external Ubuntu 9.10 (external) install and since I wanted to move it to a smaller partition of the external disk I could not use the
```
sudo dd if=/dev/hda1 of=/dev/sda1
```
(as per)
[http://ubuntuforums.org/showthread.php?t=599599]("http://ubuntuforums.org/showthread.php?t=599599")
Thus I went for a simple
```
sudo cp -dpR /mnt/old_ubuntu/* /mnt/new_ubuntu/
```
(thanks to kidders)
[http://ubuntuforums.org/archive/index.php/t-431645.html]("http://ubuntuforums.org/archive/index.php/t-431645.html")

It worked very well.

Then I fixed the fstab of the copied system with the UUID of the correct partitions, and that worked as well.

Since I have done everything under my new installation of Ubuntu 9.10 I could use Groub2 and I issued the command
```
sudo update-grub
```

to update the Grub2 that is in my external disk

Grub found:
1) my old ubuntu 8.04 in the internal HD
2) the windows XP that lives also in the internal HD
3) ubuntu 9.10 in the external USB
4) the newly copied Ubuntu 8.04 on the external USB

Then I went to boot the copy on the external and it happened that that it was actually booted still the copy in the internal.

I had to check the specs of Grub2
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")
and in the
```
/boot/grub/grub.cfg
```
file I found out the in the line of the boot the two ubuntu 8.04 where booting from different partitions but then the UUIDs were the same

i.e.
```
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (on /dev/sda5)" {

	insmod ext2

	set root=(hd0,5)

	search --no-floppy --fs-uuid --set badf5f3e-6e2d-4756-a798-2a5f6fc10e1a

	linux /boot/vmlinuz-2.6.24-25-generic root=UUID=badf5f3e-6e2d-4756-a798-2a5f6fc10e1a ro quiet splash

	initrd /boot/initrd.img-2.6.24-25-generic

}
```

and

```
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-25-generic (on /dev/sdb5)" {

	insmod ext2

	set root=(hd1,5)

	search --no-floppy --fs-uuid --set e3bb4ef4-3f05-4432-b631-2543a4989f25

	linux /boot/vmlinuz-2.6.24-25-generic root=UUID=badf5f3e-6e2d-4756-a798-2a5f6fc10e1a ro quiet splash

	initrd /boot/initrd.img-2.6.24-25-generic

}
```

the
	set root=
instructions point to two different partitions while the UUID points to the same.
Result: both boot from /dev/sda5

the workaround is to follow the instructions of 
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")
and copy the menu entry

```
menuentry "MY CUSTOM ENTRY (on /dev/sdb5)" {

	insmod ext2

	set root=(hd1,5)

	search --no-floppy --fs-uuid --set e3bb4ef4-3f05-4432-b631-2543a4989f25

	linux /boot/vmlinuz-2.6.24-25-generic root=UUID= e3bb4ef4-3f05-4432-b631-2543a4989f25 ro quiet splash

	initrd /boot/initrd.img-2.6.24-25-generic

}

```
in the file

```
40_custom
``` in the ```
/etc/grub.d/
``` folder

where I have put the correct UUID.

Then you find this entry at the end of the Grub menu and if you hit it it works, but it seems to me that Grub2 did not do the correct job configuring itself after the issuing of the command

```
sudo update-grub
```

or have I done something wrong?

---

