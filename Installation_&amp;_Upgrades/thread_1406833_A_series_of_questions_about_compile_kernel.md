---
title: "A series of questions about compile kernel"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by xiluo3344 on 2010-02-14
Ubuntu9.10,as i want to compile kernel 2.6.32.8 for a beginning of being a new kernel developer.what i did was that download the source package on kernel.org,then run the command below:
make oldconfig
make
make bzImage
make modules
make modules_install
make install
mkinitramfs -o /boot/initrd.img-2.6.32.8 /lib/modules/2.6.32.8
Ok,so far there was no problems.But after i worte the grub.cfg,the system could not into the kernel choose menu,just the grub's command mode(sh:grub>). 


About the grub.cfg,well,i have try for times.As we know that grub.cfg is read-only,first time i use command "chmod" to change it into read-write,then insert as below:


menuentry "Ubuntu, Linux 2.6.32.8" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 18b49966b4994762
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32.8 root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32.8
}
menuentry "Ubuntu, Linux 2.6.32.8 (recovery mode)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 18b49966b4994762
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32.8 root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32.8
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 18b49966b4994762
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 18b49966b4994762
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}

But after reboot the system,there was no kernel menu,only "sh:grub>".For i did not think more,i deleted the all system and reinstall ubuntu 9.10(use wubi).
Secend time,i did not change the grub.cfg in directly.Into the /etc/grub.d/40_custom,i worte the menuentry in it,then 
sudo update-grub
Also it could not useful,now in the grub's command mode i can use command going into the old kernel 2.6.32.14-generic but can not into the new kernel 2.6.32.8,as a point of "unable to mount root fs on unknown-blcok(8,3)".
So what i can do now?

---

### Post by tom4everitt on 2010-02-14
I would try with a normal (non-wubi) installation of ubuntu. Then a simpler menuentry will suffice.

---

