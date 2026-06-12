---
title: "could not connect to plymouth"
date: 2009-12-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2009-12-23
How can I fix this ???



menuentry "Ubuntu, with Linux 2.6.32-9-generic" {
        set recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 9c393deb-7d00-466c-827b-0e6e767921d2
        linux   /boot/vmlinuz-2.6.32-9-generic root=UUID=9c393deb-7d00-466c-827b-0e6e76792
1d2 ro splash gfxpayload=true vga=786  quiet splash
        initrd  /boot/initrd.img-2.6.32-9-generic
}


Ive tried vga=0x317 and gfxpayload=1024x768x16 and I get slanted colors on top of screen ?

---

### Post by Vanishing on 2009-12-23
> **cecilpierce said:**
> How can I fix this ???



menuentry "Ubuntu, with Linux 2.6.32-9-generic" {
        set recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 9c393deb-7d00-466c-827b-0e6e767921d2
        linux   /boot/vmlinuz-2.6.32-9-generic root=UUID=9c393deb-7d00-466c-827b-0e6e76792
1d2 ro splash gfxpayload=true vga=786  quiet splash
        initrd  /boot/initrd.img-2.6.32-9-generic
}


Ive tried vga=0x317 and gfxpayload=1024x768x16 and I get slanted colors on top of screen ?

As I've said in the other thread, I think you should try to fsck -f.

---

