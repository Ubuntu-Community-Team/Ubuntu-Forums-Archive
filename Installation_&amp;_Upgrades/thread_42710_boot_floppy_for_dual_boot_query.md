---
title: "boot floppy for dual boot query"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by martin_lovick on 2005-06-19
Greetings,

Having tried using a lilo-based boot floppy for dual booting (installking lilo and running mkbootfloppy), I have found this problematic. 

Is there any way of installing grub to a floppy and creating a grub-based boot floppy?

---

### Post by paddy2706 on 2005-06-19
```
**grub-floppy**
Usage: /sbin/grub-floppy [options] <block device>
Create GRUB boot floppy.

options:
        -h, --help      print this message and exit
```

---

### Post by martin_lovick on 2005-06-19
have created a grub boot floppy, but when it boots, it only presents a grub> prompt (as opposed to the menu what is installed to mbr by default).

How do create a grub disk to give the boot menu installed on my mbr?

---

### Post by mingus on 2005-06-20
It is not getting installed correctly or it is not finding menu.lst or there is a problem with menu.lst.

You can re-create menu.lst with:
#update-grub

You can try a different script to install to the floppy:
#grub-install /dev/fd0

You can also install it by running grub interactively using the install command.  We would need to see your fstab to tell you how to use this command.

---

### Post by martin_lovick on 2005-06-20
I think Ive sorted it, the problem was that the disk was formatted to FAT rather than ext2. When this was done, I used grub-install to create the disk.

How about providing the option to create a boot disk during installation? (like most distros do)

...just a thought

---

### Post by mingus on 2005-06-20
[QUOTE=martin_lovick]I think Ive sorted it, the problem was that the disk was formatted to FAT rather than ext2. When this was done, I used grub-install to create the disk.

How about providing the option to create a boot disk during installation? (like most distros do)

...just a thought[/QUOTE]

Right . . . I forgot because I don't format the disk at all (it's just writing a raw sector).

And installation option . . . could not agree with you more.  Pet peeve of mine.

---

