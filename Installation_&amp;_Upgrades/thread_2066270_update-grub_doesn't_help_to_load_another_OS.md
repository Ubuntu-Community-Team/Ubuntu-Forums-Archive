---
title: "update-grub doesn't help to load another OS"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by enotbear on 2012-10-04
I installed Debian 6.05 on sda2, and Xubuntu 12.04 on sda5. After installed Xubuntu,in GRUB menu Debian doesn't counted.

I choose load xubuntu, then make in terminal

```
lm@ubuntu:~$ sudo update-grub
[sudo] password for lm: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found linux image: /boot/vmlinuz-2.6.32-5-686
Found initrd image: /boot/initrd.img-2.6.32-5-686
Found memtest86+ image: /memtest86+.bin
Found Debian GNU/Linux (6.0.5) on /dev/sda2
done
lm@ubuntu:~$ 

```and after reboot was the same, Xubuntu only.

And in search i found, that it must solve the problem, but  it doesn't.
Please advice, possible it's not enough and there need to make something else?

and here is grub.config lines

```
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root b6de0cc2-41be-4c1b-962e-b26743baad57
        echo    'Loading Linux 3.2.0-23-generic ...'
        linux   /vmlinuz-3.2.0-23-generic root=UUID=e6d01440-31f1-4da8-bde3-d9521374c78c ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-3.2.0-23-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.32-5-686' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root b6de0cc2-41be-4c1b-962e-b26743baad57
        linux   /vmlinuz-2.6.32-5-686 root=UUID=e6d01440-31f1-4da8-bde3-d9521374c78c ro   quiet splash $vt_handoff
        initrd  /initrd.img-2.6.32-5-686
}
menuentry 'Ubuntu, with Linux 2.6.32-5-686 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos1)'
        search --no-floppy --fs-uuid --set=root b6de0cc2-41be-4c1b-962e-b26743baad57
        echo    'Loading Linux 2.6.32-5-686 ...'
        linux   /vmlinuz-2.6.32-5-686 root=UUID=e6d01440-31f1-4da8-bde3-d9521374c78c ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-2.6.32-5-686

```

---

### Post by sahabcse on 2012-10-04
Mount the partition sda2 and copy the debian related entries in grub.cfg and paste it into the xubuntu grub file

---

### Post by darkod on 2012-10-04
It clearly says Debian is found, look at the last line of update-grub before 'done'.

Don't you have entry for Debian after the memtest entries?

---

