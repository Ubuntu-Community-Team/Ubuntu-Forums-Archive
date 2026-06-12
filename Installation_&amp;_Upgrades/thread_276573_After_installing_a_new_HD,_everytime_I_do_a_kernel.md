---
title: "After installing a new HD, everytime I do a kernel upgrade, grub fails"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by Ced22 on 2006-10-13
Hello there,

Recently, I have installed a new HD which changed grub's way of seeing the devices. My ubuntu installation is now (hd2,0) instead of (hd1,0). Unfortunately this seems to be configurated in my ubuntu installation, because every time my kernel gets upgraded, the menu.lst entry is changed from (hd2,0) to (hd1,0). I usually get an error 15 and change the line to (h2,0) and everything works again.
It's not a big deal to fix it, but I still wonder where I could change this setting in my ubuntu installation. There _must_ be a line somewhere, saying "ubuntu install drive (hd1,0)" or something like that :-)

I've already looked through a lot of posts, but they all seem to stop when the problem is solved by editing menu.lst and waiting for the next upgrade to break the boot process again :-)

Thanks for any pointers,
Ced

---

### Post by Ced22 on 2006-10-13
I just found a hint in another post, I was checking the manpage of update-grub and found information, that update-grub looks for options in the /boot/grub/menu.lst file. Specifically, the following lines were interesting:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```

The according section in the manpage says:
> This is the grub device from which grub loads the kernel

I suppose this could be the answer to my question. It's the debian automagic kernels list and update-grub which organize the menu.lst everytime a kernel upgrade happens.

Is this correct?

---

### Post by lha on 2006-10-13
> **Ced22 said:**
> I just found a hint in another post, I was checking the manpage of update-grub and found information, that update-grub looks for options in the /boot/grub/menu.lst file. Specifically, the following lines were interesting:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)
```

The according section in the manpage says:


I suppose this could be the answer to my question. It's the debian automagic kernels list and update-grub which organize the menu.lst everytime a kernel upgrade happens.

Is this correct?
Yes it is.

You have to change '#kopt=root=/dev/hda1 ro' (or equivalent), too.

---

### Post by gn2 on 2006-10-13
Sorry, misread original post

---

### Post by Ced22 on 2006-10-13
> **lha said:**
> Yes it is.

You have to change '#kopt=root=/dev/hda1 ro' (or equivalent), too.

Thanks very much for your reply. Actually the kopt setting was still correct, because the device name hasn't changed (my root disc is S-ATA and I added an IDE disc).

I changed the setting and I will wait for the next kernel upgrade to see if it works! Thanks again, mate.

---

### Post by lha on 2006-10-13
> **Ced22 said:**
> Thanks very much for your reply. Actually the kopt setting was still correct, because the device name hasn't changed (my root disc is S-ATA and I added an IDE disc).

I changed the setting and I will wait for the next kernel upgrade to see if it works! Thanks again, mate.

You don't have to wait. Just execute update-grub and check if the new menu.lst looks good. (You need sudo to make it work.)

---

