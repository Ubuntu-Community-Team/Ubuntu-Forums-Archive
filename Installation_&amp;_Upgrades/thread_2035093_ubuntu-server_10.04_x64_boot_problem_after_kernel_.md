---
title: "ubuntu-server 10.04 x64 boot problem after kernel upgrade linux-image-2.6.32-41.9"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by tester100 on 2012-07-29
Hi guys

I have a problem here which is getting frustrating now..


several weeks ago i have upgraded one of our ubuntu-server machines here, previously we were running it on kernell image 2.6.32-21  , after upgrading it to 2.6.32-41 problems started.

on boot up, if for any instance the machine needs rebooting, the boot menu pops up and it will select new kernell image, but then it gets stuck on boot, it wont boot up gives me some errors i think related to grup 89098098avavw9e8230983209erf error , so i have to reboot machine again, and manually select the previous older kernel image version in order to boot normally.

the problem is that machine sits on a remote location where the main and principal access is done via ssh.

so needles to say if machine reboots for any issue someone needs to move there fisically in order to select old version kernell to boot system up.

is there any configuration possible to adjust grub to select automatically my old version kernell 2.6.32-21

any help or comments are welcome.

thxs
tester100

---

### Post by tester100 on 2012-07-29
Hi guys

digging back again

on the boot/grub folder i have found the following grub config

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, com Linux 2.6.32-41-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    linux    /boot/vmlinuz-2.6.32-41-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro   quiet
    initrd    /boot/initrd.img-2.6.32-41-server
}
menuentry 'Ubuntu, com Linux 2.6.32-41-server (modo de recuperaÃ§Ã£o)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    echo    'Carregando Linux 2.6.32-41-server ...'
    linux    /boot/vmlinuz-2.6.32-41-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-41-server
}
menuentry 'Ubuntu, com Linux 2.6.32-40-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    linux    /boot/vmlinuz-2.6.32-40-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro   quiet
    initrd    /boot/initrd.img-2.6.32-40-server
}
menuentry 'Ubuntu, com Linux 2.6.32-40-server (modo de recuperaÃ§Ã£o)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    echo    'Carregando Linux 2.6.32-40-server ...'
    linux    /boot/vmlinuz-2.6.32-40-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-40-server
}
menuentry 'Ubuntu, com Linux 2.6.32-39-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    linux    /boot/vmlinuz-2.6.32-39-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro   quiet
    initrd    /boot/initrd.img-2.6.32-39-server
}
menuentry 'Ubuntu, com Linux 2.6.32-39-server (modo de recuperaÃ§Ã£o)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    echo    'Carregando Linux 2.6.32-39-server ...'
    linux    /boot/vmlinuz-2.6.32-39-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-39-server
}
menuentry 'Ubuntu, com Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro   quiet
    initrd    /boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, com Linux 2.6.32-21-server (modo de recuperaÃ§Ã£o)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    echo    'Carregando Linux 2.6.32-21-server ...'
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-21-server
}

```


So when ubuntu rebots, it jumps straight to the latest version kernel 2.6.32.41 and after selecting it it completely fails to boot.

if i just remove it and leave it like this, is it possible that my system boots straight in the older kernel image ?

```
## BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, com Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro   quiet
    initrd    /boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, com Linux 2.6.32-21-server (modo de recuperaÃ§Ã£o)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668
    echo    'Carregando Linux 2.6.32-21-server ...'
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=1da00c7b-6846-4aaf-8ea7-4c8c5e3f5668 ro single 
    echo    'Carregando ramdisk inicial ...'
    initrd    /boot/initrd.img-2.6.32-21-server
}
### END /etc/grub.d/10_linux ###

```


shall i delete all others in config? this way the menu window on reboot will only show up the older kernel version and it will boot ok..

has anyone tested this before ?

---

