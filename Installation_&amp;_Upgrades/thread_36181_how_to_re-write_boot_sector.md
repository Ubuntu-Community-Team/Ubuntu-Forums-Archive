---
title: "how to re-write boot sector?"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by southy on 2005-05-22
Hi there, 
slight problem here where you can perhaps give me a hint.
yesterday the system wouldnt shut down correctly - stuck at "unmounting local devices". 
When I wanted to boot up today, it wouldnt find a system on the drive.
So I booted from CD, fscked (-f), all fine, can mount the drive, read data, all well. 
Now I guess I have to re-write the bootloader. 
But when I do a "grub-install /dev/hdb" or "/dev/hdb1" (which one is correct anyway?) 
it always gives me 
```
root@ubuntu:/ # grub-install /dev/hdb
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/ # grub-install /dev/hdb1
Could not find device for /boot: Not found or not a block device.

```

What reason could that be? When I mount it manually, /mnt/hdb1/boot is readable and data is present there.
Anyone a hint about what I can do?
Do I understand correctly that /dev/hdb1/boot is the bootsector of the partition?
So /dev/hdb/boot is the bootsector of the whole disk? So this one would need to be re-written? But how?


And, besides: does anyone know what reason it could be that the system always crashes (freezes) when I insert a CD or DVD? Thats a little annoying on the long run.

Thanks for all your help and greetings,
southy

---

### Post by philcolbourn on 2005-05-22
[QUOTE=southy]Hi there, 
slight problem here where you can perhaps give me a hint.
yesterday the system wouldnt shut down correctly - stuck at "unmounting local devices". 
When I wanted to boot up today, it wouldnt find a system on the drive.
So I booted from CD, fscked (-f), all fine, can mount the drive, read data, all well. 
Now I guess I have to re-write the bootloader. 
But when I do a "grub-install /dev/hdb" or "/dev/hdb1" (which one is correct anyway?) 
it always gives me 
```
root@ubuntu:/ # grub-install /dev/hdb
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/ # grub-install /dev/hdb1
Could not find device for /boot: Not found or not a block device.

```

What reason could that be? When I mount it manually, /mnt/hdb1/boot is readable and data is present there.
Anyone a hint about what I can do?
Do I understand correctly that /dev/hdb1/boot is the bootsector of the partition?
So /dev/hdb/boot is the bootsector of the whole disk? So this one would need to be re-written? But how?


And, besides: does anyone know what reason it could be that the system always crashes (freezes) when I insert a CD or DVD? Thats a little annoying on the long run.

Thanks for all your help and greetings,
southy[/QUOTE]
 I'll get you started...

get into grub command line interface from a cd (such live ubuntu).

NOTE: my ubuntu boot partition was in hda5 which is grub hd0,4

setup --prefix=/boot/grub (hd0)
root (hd0,4)
kernel (hd0,4)/boot/vm<use tab to get kernel image> root=/dev/hda5 ro
initrd (hd0,4)/boot/initrd<use tab again to get the right initrd image>
boot

when it works and you are back into ubuntu,
check /boot/grub/menu.1st

Now I forget... Is there a grub command that must be run?
Is there an easier way?

---

### Post by southy on 2005-05-22
Ok, strange things happen here: 
Just rebooted to try as you suggested, and - just for the records - tried booting without the live-cd and.. guess what: it booted from the hard drive.
I don't know why, because grub-install did not once terminate without that error, so one should think, there's no working bootsector there, but - there is.
either grub-install suceeded in spite of the errors, or the bootsector miraculously healed itself. 
Anyhow, many thanks to you, phil, for the suggestions - don't need to try them now.

Thanks anyway.

Southy

---

