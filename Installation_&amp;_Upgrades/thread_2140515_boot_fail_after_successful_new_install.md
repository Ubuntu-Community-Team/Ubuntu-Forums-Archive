---
title: "boot fail after successful new install"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2013-04-29
I have downloaded and installed Ubu 12.04 The installation went well, no errors. But on reboot, it says 'root = 092ff536-f1b9-486d-bbe7-f036dbd58bd0 does not exist' and goes to initramfs. This number is definitely correct. I looked at it in Fedora
Any tips out there??

From grub.cfg
menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 092ff536-f1b9-486d-bbe7-f036dbd58bd0
    linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=092ff536-f1b9-486d-bbe7-f036dbd58bd0 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-19-generic
}

---

### Post by jonathanfv on 2013-04-30
Maybe you can try fixing it with boot-repair?

---

