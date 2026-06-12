---
title: "Can't boot from USB after install?"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by hopelessone on 2012-10-02
Hi,

I installed LVM to USB, 
200MB /boot
15GB /
15gb /home
1gb swap

During install I selected "dont install grub" since I'll be using the USB somewhere else.

In my laptop I hold F12 and select the USB and get a black screen with a cursor.

If I install from dash "Startup Disk Creator" the USB boots.

What do I need to do to boot correctly?

Thanks

---

### Post by darkod on 2012-10-02
You need to install grub2 to the usb. By telling it not to install a bootloader, how did you expect to boot from it?

---

### Post by hopelessone on 2012-10-02
I thought grub was computer specific, so i didnt install it.
cheers i'll look up how to install grub2 on a usb

---

### Post by hopelessone on 2012-10-02
OK did
```
grub-install --force --no-floppy --root-directory=/media/f7ad4fed-622f-4ac9-b361-c1636714204a /dev/sdi
```

went ok

Boots into:
GRUB>

how do i get it to boot? cant see what to edit in the grub.cfg

---

### Post by darkod on 2012-10-02
If that was the correct root partition and the usb is /dev/sdi, it should have worked.

You can also work with /dev/sdiX, it might be easier. Mount it at some temporary point like /mnt first:
sudo mount /dev/sdiX /mnt
sudo grub-install --root-directory=/mnt /dev/sdi

Also, you need to do that from ubuntu of the same version, either a hdd installation of the same version or the same cd you used to install onto the usb.

---

### Post by hopelessone on 2012-10-03
Hey thanks for the great info.

So next time when installing from alternate cd, when grub detects other operating systems, select no to install to first hdd, then when it asks where to install grub select the /dev/sdi.

Is that right for future ref?

Thanks

---

### Post by darkod on 2012-10-04
Yes, that's right.

Note that the commands in my previous post are probably wrong because I totally forgot you are using LVM.

If you are using LVM and you still want to add grub2 to the usb, the procedure would be slightly different. Are you still interested?

---

### Post by hopelessone on 2012-10-04
I'm gonna do a reinstall because a few files became corrupted anyway..will give it a shot..

thanks

---

