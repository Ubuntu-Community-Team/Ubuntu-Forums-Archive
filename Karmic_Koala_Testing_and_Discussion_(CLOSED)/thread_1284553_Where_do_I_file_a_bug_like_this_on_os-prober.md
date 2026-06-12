---
title: "Where do I file a bug like this on os-prober?"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-10-06
I have grub2 working well with custom entries.  I like it.

The BIG problem is os-prober.  I realize that I have a lot of OS' on my box and some think this is silly.  I now have an excuse.  I am testing grub and os-prober.

I have had a couple of folks ask for a screen shot of my menu.  There are two problems with this;
1> I don't know how to get the screen shot.
2> it would take several to cover the menu.

In view of that and to illustrate the weird os-prober behavior, here is my most impressive /boot/grub/grub.cfg contents;
```

### BEGIN /etc/grub.d/09_custom ###
menuentry "DailyGrub on sda22" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,22)
    search --no-floppy --fs-uuid --set 888f77a5-be78-41b8-bdb5-729c3de5c348
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=888f77a5-be78-41b8-bdb5-729c3de5c348 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
menuentry "KinkyStoner1.0 on sda6" {
        set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 so quiet splash
        initrd /initrd.img
}
menuentry "Kinky Stoner1.0 on sda10" {
        set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 so quiet splash
        initrd /initrd.img
}
menuentry "KinkyA1 on sda16" {
        set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 so quiet splash
        initrd /initrd.img
}
menuentry "KinkyA4 on sda20" {
        set root=(hd0,20)
        linux /vmlinuz root=/dev/sda20 so quiet splash
        initrd /initrd.img
}
menuentry "Jaunty 9.04, kernel 2.6.28-15-generic (on /dev/sda8)" {
        set root=(hd0,8)
        search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
        linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
        initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Stoner1.1, kernel 2.6.28-15-generic (on /dev/sda18)" {
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
menuentry "Mandriva 2009 KDE sda14" {
linux (hd0,14)/boot/vmlinuz
initrd (hd0,14)/boot/initrd.img
}
menuentry "Kinky1.1A4 on sdb16" {
        set root=(hd1,16)
        linux /vmlinuz root=/dev/sdb16 so quiet splash
        initrd /initrd.img
}
menuentry "KinkyB on sdb17" {
        set root=(hd1,17)
        linux /vmlinuz root=/dev/sdb17 so quiet splash
        initrd /initrd.img
}
menuentry "Daily on sdb13" {
        set root=(hd1,13)
        linux /vmlinuz root=/dev/sdb13 so quiet splash
        initrd /initrd.img
}
menuentry "NoUpdate on sdb12 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=0944b738-832a-4d1a-8822-fd5f7a2f65a1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky-Grub2-A2 on sdb10" {
        set root=(hd1,10)
        linux /vmlinuz root=/dev/sdb10 so quiet splash
        initrd /initrd.img
}
menuentry "KinkyStonerA2 on sdb8" {
        set root=(hd1,8)
        linux /vmlinuz root=/dev/sda8 so quiet splash
        initrd /initrd.img
}
menuentry "DailyB on sdb7" {
        set root=(hd1,7)
        linux /vmlinuz root=/dev/sdb7 so quiet splash
        initrd /initrd.img
}
menuentry "Studio9.04-64, kernel 2.6.28-3-rt (on /dev/sdb18)" {
    insmod ext2
    set root=(hd1,18)
    search --no-floppy --fs-uuid --set 0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9 ro quiet splash
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Stoner1.1, 2.6.28-15-generic (sda11)" {
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set b2279de6-cdfd-4516-9ceb-f083533f83ce
    linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sdb11
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "JauntyVB, kernel 2.6.28-15-generic (sdb9)" {
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=f6420b83-12e4-4760-9a79-4fcde04eb797 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Main, kernel 2.6.24-24-generic (sdb6)" {
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Man-Gnome on sdb14" {
linux (hd1,14)/boot/vmlinuz
initrd (hd1,14)/boot/initrd.img
}
menuentry "Man-Both on sdb15" {
linux (hd1,15)/boot/vmlinuz
initrd (hd1,15)/boot/initrd.img
}
### END /etc/grub.d/09_custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-12-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,22)
    search --no-floppy --fs-uuid --set 888f77a5-be78-41b8-bdb5-729c3de5c348
    linux    /boot/vmlinuz-2.6.31-12-generic root=UUID=888f77a5-be78-41b8-bdb5-729c3de5c348 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,22)
    search --no-floppy --fs-uuid --set 888f77a5-be78-41b8-bdb5-729c3de5c348
    linux    /boot/vmlinuz-2.6.31-12-generic root=UUID=888f77a5-be78-41b8-bdb5-729c3de5c348 ro single 
    initrd    /boot/initrd.img-2.6.31-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Kinky Stoner1.0 on sda10 (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyA1 on sda16 (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyA4 on sda20 (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /vmlinuz root=/dev/sda20 so quiet splash
    initrd /initrd.img
}
menuentry "Adding DailyGrub on sda22 (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /vmlinuz root=/dev/sda22 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStoner1.0 on sda6 (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /vmlinuz root=/dev/sda6 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode) (on /dev/sda10)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro single
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "linux (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc
    initrd (hd0,11)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e failsafe
    initrd (hd0,11)/boot/initrd.img
}
menuentry "2.6.27-desktop586rc8-2mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
}
menuentry "desktop586 2.6.27.19-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.19-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.14-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.14-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.14-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.14-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.21-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.21-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.21-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.24-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.24-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.24-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-2mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.24-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.24-2mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.24-desktop586-2mnb.img
}
menuentry "linux (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc
    initrd (hd0,13)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 failsafe
    initrd (hd0,13)/boot/initrd.img
}
menuentry "2.6.27-desktop586rc8-2mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
}
menuentry "desktop586 2.6.27.19-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.19-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.21-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.21-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.21-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.24-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.24-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.24-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-2mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.24-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.24-2mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.24-desktop586-2mnb.img
}
menuentry "KinkyA1 on sda16 (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "Adding DailyGrub on sda22 (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /vmlinuz root=/dev/sda22 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyA4 on sda20 (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /vmlinuz root=/dev/sda20 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky Stoner1.0 on sda10 (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStoner1.0 on sda6 (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /vmlinuz root=/dev/sda6 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode) (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro single
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda10) (Stoner1.0-32) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda8) (Jaunty-32) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "KinkyA4 on sda20 (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /vmlinuz root=/dev/sda20 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyA1 on sda16 (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky Stoner1.0 on sda10 (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStoner1.0 on sda6 (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /vmlinuz root=/dev/sda6 so quiet splash
    initrd /initrd.img
}
menuentry "Adding DailyGrub on sda22 (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /vmlinuz root=/dev/sda22 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode) (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro single
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "KinkyStoner1.0 on sda6 (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /vmlinuz root=/dev/sda6 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky Stoner1.0 on sda10 (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyA1 on sda16 (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyA4 on sda20 (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /vmlinuz root=/dev/sda20 so quiet splash
    initrd /initrd.img
}
menuentry "Adding DailyGrub on sda22 (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /vmlinuz root=/dev/sda22 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu, Linux 2.6.31-12-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-12-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro single y
    initrd /boot/initrd.img-2.6.31-12-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/memtest86+.bin 
}
menuentry "Kinky-Grub2-A2 on sda10 (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky1.1A4 on sda16 (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyB on sda17 (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /vmlinuz root=/dev/sda17 so quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /vmlinuz root=/dev/sda13 so quiet splash
    initrd /initrd.img
}
menuentry "DailyB on sda7 (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=8a59ea24-d06a-45ce-bd11-665efb66be2b ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=8a59ea24-d06a-45ce-bd11-665efb66be2b ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set b2279de6-cdfd-4516-9ceb-f083533f83ce
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=b2279de6-cdfd-4516-9ceb-f083533f83ce ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set b2279de6-cdfd-4516-9ceb-f083533f83ce
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=b2279de6-cdfd-4516-9ceb-f083533f83ce ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set b2279de6-cdfd-4516-9ceb-f083533f83ce
    linux /boot/memtest86+.bin 
}
menuentry "NoUpdate on sda12 2.6.31-10-generic (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=0944b738-832a-4d1a-8822-fd5f7a2f65a1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky1.1A4 on sda16 2.6.31-10-generic (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=e62bedbe-f9d8-43a1-a39a-32e651a233c0 ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda13 2.6.31-10-generic (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=75c3506e-1719-4bee-8e65-72dc253bfa1c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky-GrubA2 on sda10 2.6.31-10-generic (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8a59ea24-d06a-45ce-bd11-665efb66be2b ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA2-Stoner on sda8 (2.6.31-10-generic) (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=7e2c2a59-d3b7-4a97-a996-d5b77de048b0 ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=0944b738-832a-4d1a-8822-fd5f7a2f65a1 ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sdb12)" {
    insmod ext2
    set root=(hd1,12)
    search --no-floppy --fs-uuid --set 0944b738-832a-4d1a-8822-fd5f7a2f65a1
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=0944b738-832a-4d1a-8822-fd5f7a2f65a1 ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Daily on sda13 2.6.31-11-generic (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /vmlinuz root=/dev/sda13 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky1.1A4 on sda16 (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "JauntyA6 on sda17 2.6.31-11-generic (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /vmlinuz root=/dev/sda17 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky-Grub2-A2 on sda10 (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStonerA2 on sda8 (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "DailyB on sda7 (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=ff15be1a-8a1e-41a9-a78a-c7335f3af9fd ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sdb13)" {
    insmod ext2
    set root=(hd1,13)
    search --no-floppy --fs-uuid --set ff15be1a-8a1e-41a9-a78a-c7335f3af9fd
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=ff15be1a-8a1e-41a9-a78a-c7335f3af9fd ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "linux Man-Gnome (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz BOOT_IMAGE=linux_Man-Gnome root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent vga=788
    initrd (hd0,13)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426
    initrd (hd0,13)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 failsafe
    initrd (hd0,13)/boot/initrd.img
}
menuentry "desktop 2.6.29.1-4mnb (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz-2.6.29.1-desktop-4mnb BOOT_IMAGE=desktop_2.6.29.1-4mnb root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.29.1-desktop-4mnb.img
}
menuentry "desktop 2.6.29.6-1mnb (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz-2.6.29.6-desktop-1mnb BOOT_IMAGE=desktop_2.6.29.6-1mnb root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.29.6-desktop-1mnb.img
}
menuentry "linux (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent vga=788
    initrd (hd0,13)/boot/initrd.img
}
menuentry "desktop 2.6.29.6-2mnb (on /dev/sdb14)" {
    insmod ext2
    set root=(hd1,14)
    search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
    linux /boot/vmlinuz-2.6.29.6-desktop-2mnb BOOT_IMAGE=desktop_2.6.29.6-2mnb root=UUID=ac84960d-354b-4a68-b527-16b7aa09d126 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.29.6-desktop-2mnb.img
}
menuentry "linux (on /dev/sdb15)" {
    insmod ext2
    set root=(hd1,15)
    search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=198c1ffe-6026-4959-88dd-a0d5479ee440 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent
    initrd (hd0,14)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb15)" {
    insmod ext2
    set root=(hd1,15)
    search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=198c1ffe-6026-4959-88dd-a0d5479ee440 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426
    initrd (hd0,14)/boot/initrd.img
}
menuentry "desktop 2.6.29.6-2mnb (on /dev/sdb15)" {
    insmod ext2
    set root=(hd1,15)
    search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
    linux /boot/vmlinuz-2.6.29.6-desktop-2mnb BOOT_IMAGE=desktop_2.6.29.6-2mnb root=UUID=198c1ffe-6026-4959-88dd-a0d5479ee440 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent vga=788
    initrd (hd0,14)/boot/initrd-2.6.29.6-desktop-2mnb.img
}
menuentry "alt_linux-nonfb (on /dev/sdb15)" {
    insmod ext2
    set root=(hd1,15)
    search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
    linux /boot/vmlinuz-2.6.29.6-desktop-2mnb BOOT_IMAGE=alt_linux-nonfb root=UUID=198c1ffe-6026-4959-88dd-a0d5479ee440 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426
    initrd (hd0,14)/boot/initrd-2.6.29.6-desktop-2mnb.img
}
menuentry "desktop 2.6.29.1-4mnb (on /dev/sdb15)" {
    insmod ext2
    set root=(hd1,15)
    search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
    linux /boot/vmlinuz-2.6.29.1-desktop-4mnb BOOT_IMAGE=desktop_2.6.29.1-4mnb root=UUID=198c1ffe-6026-4959-88dd-a0d5479ee440 resume=UUID=fa1fe727-c838-41e0-a165-986838a1e426 splash=silent
    initrd (hd0,14)/boot/initrd-2.6.29.1-desktop-4mnb.img
}
menuentry "failsafe (on /dev/sdb15)" {
    insmod ext2
    set root=(hd1,15)
    search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=198c1ffe-6026-4959-88dd-a0d5479ee440 failsafe
    initrd (hd0,14)/boot/initrd.img
}
menuentry "Kinky1.1A4 on sda16 (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyB on sda17 (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /vmlinuz root=/dev/sda17 so quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /vmlinuz root=/dev/sda13 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky-Grub2-A2 on sda10 (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStonerA2 on sda8 (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "DailyB on sda7 (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=e62bedbe-f9d8-43a1-a39a-32e651a233c0 ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sdb16)" {
    insmod ext2
    set root=(hd1,16)
    search --no-floppy --fs-uuid --set e62bedbe-f9d8-43a1-a39a-32e651a233c0
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=e62bedbe-f9d8-43a1-a39a-32e651a233c0 ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "KinkyB on sda17 (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /vmlinuz root=/dev/sda17 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky1.1A4 on sda16 (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /vmlinuz root=/dev/sda13 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky-Grub2-A2 on sda10 (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStonerA2 on sda8 (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "DailyB on sda7 (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=8d13ec26-872b-4eda-8e3a-ba4caa719f44 ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sdb17)" {
    insmod ext2
    set root=(hd1,17)
    search --no-floppy --fs-uuid --set 8d13ec26-872b-4eda-8e3a-ba4caa719f44
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=8d13ec26-872b-4eda-8e3a-ba4caa719f44 ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-3-rt (on /dev/sdb18)" {
    insmod ext2
    set root=(hd1,18)
    search --no-floppy --fs-uuid --set 0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9 ro quiet splash
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode) (on /dev/sdb18)" {
    insmod ext2
    set root=(hd1,18)
    search --no-floppy --fs-uuid --set 0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9
    linux /boot/vmlinuz-2.6.28-3-rt root=UUID=0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9 ro single
    initrd /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb18)" {
    insmod ext2
    set root=(hd1,18)
    search --no-floppy --fs-uuid --set 0fd0e812-dad2-419f-a0a5-c0ce6eedfdc9
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode) (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/memtest86+.bin 
}
menuentry "DailyB on sda7 (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky1.1A4 on sda16 (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyB on sda17 (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /vmlinuz root=/dev/sda17 so quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /vmlinuz root=/dev/sda13 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky-Grub2-A2 on sda10 (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyStonerA2 on sda8 (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=48350e8b-dc94-45fb-a360-cec458a663e7 ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 48350e8b-dc94-45fb-a360-cec458a663e7
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=48350e8b-dc94-45fb-a360-cec458a663e7 ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "KinkyStonerA2 on sda8 (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky1.1A4 on sda16 (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /vmlinuz root=/dev/sda16 so quiet splash
    initrd /initrd.img
}
menuentry "KinkyB on sda17 (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /vmlinuz root=/dev/sda17 so quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /vmlinuz root=/dev/sda13 so quiet splash
    initrd /initrd.img
}
menuentry "Kinky-Grub2-A2 on sda10 (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "DailyB on sda7 (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=7e2c2a59-d3b7-4a97-a996-d5b77de048b0 ro quiet splash
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode) (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set 7e2c2a59-d3b7-4a97-a996-d5b77de048b0
    linux /boot/vmlinuz-2.6.31-11-generic root=UUID=7e2c2a59-d3b7-4a97-a996-d5b77de048b0 ro single
    initrd /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=f6420b83-12e4-4760-9a79-4fcde04eb797 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=f6420b83-12e4-4760-9a79-4fcde04eb797 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.04.1, memtest86+ (on /dev/sda6) (MAIN) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda7) (SuperOS) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/memtest86+.bin 
}
menuentry "Memory test (memtest86+) (on /dev/sda8) (KinkyA2-64) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```
This is on /dev/sda from DailyGrub with / on sda22 and /home on sda23.

As you can see, the funky os-prober entries start with the second entry from that source.

The Mandriva entries almost work.  You can hit "e" and change the last  X (hdY,X) in the entry to match the first X in the entry and it is fine.

I have the idea that maybe the folks working on this problem would like to see this.  They probably don't get stuff from folks quite as silly as I am.

Where in flinderation do I file this?  I have launchpad up right now and I'll be jiggered if I can figure out what I need to do.

I know, not only silly but a noob too.  Geeze, a silly noob that is also a grumpy geezer.

---

### Post by 23meg on 2009-10-06
```
ubuntu-bug os-prober
```.

---

### Post by ranch hand on 2009-10-06
> **23meg said:**
> ```
ubuntu-bug os-prober
```.
Thank you very much.  I am on the wrong OS right now, main drive Jaunty where most of my time is spent.

I will be back over to that drive later though and do that.  I do not know how I missed that one.  I just tried it here and canceled it before the poor thing had a breakdown.  It would have trouble finding grub2 here.

I would just go nuts for grub2 if this was even a little better.

Boy are we ever going to hear about it when this is released though.

---

### Post by ranch hand on 2009-10-07
Well, I better mark this as solved.

That was fun and had links to all the info this silly, grumpy geezer noob needed.

I hope that is helps, they have made tremendous progress since A2 and I am really getting to like grub2 a whole lot.

Thanks 23meg

---

### Post by oboedad55 on 2009-10-07
> **ranch hand said:**
> Well, I better mark this as solved.

That was fun and had links to all the info this silly, grumpy geezer noob needed.

I hope that is helps, they have made tremendous progress since A2 and I am really getting to like grub2 a whole lot.

Thanks 23meg

I've only got like seven OSes. I feel like such a gol-durned piker.

---

### Post by ranch hand on 2009-10-07
I think 7 is plenty.  With this testing going on anyway I though I could just screw with several releases at once, in different ways.

I usually have 3 or 4 on the main drive and up to 6 on the other internal (now testing 32bit).  I got into it because I had too much fun (still do) with the bugger.  My wife was not amused when I broke it 5 times the first week.

She seems to think that your box ought to actually run some of the time and be able to retain files.

So I dual booted Hardy/Hardy and trie every thing out on the second one before doing it to the first.  Sucker is still working.  So basically it is just a past time that has gotten out of hand.

I have learned a lot in the last year though.  It is educational.  And FUN.

---

### Post by peter3 on 2009-10-07
I notice that you include no Windows partitions.  While I, too, have many Linux installations spread
across 3 disks, I also have Windows partitions on two of them.  GRUB2 found the original Win2K 
install, but missed Vista and Windows 7 on the third disk.  

Do you have any suggestions for finding them, short of editing grub.cfg by hand (which I have had
considerable success with)?  

Thank you.

---

### Post by ranch hand on 2009-10-07
This is a virus free box.  No Win Jerry Lewis Pro on here.  We have one other computer, an old HP with a 10Gb HDD and it runs Intrepid.

I had the idea from reading the forums here that the detection of Win was just a matter of running update-grub after installation.

Have you tried that?

I would not edit the /boot/grub/grub.cfg file directly at all.  That is silly.  It is over written every time update-grub is run.  That means every kernal update, every grub-pc update, most grub-common updates, and that doesn't count when you may want to run it your self.

You need to go to /etc/grub.d.  This is where most of grub.cfg is generated.

Open the 40_custom file and start a menu entry like this;
```

 echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```
The part;
```

menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}

```
will need replaced with your existing Win entry and edited to fit you other 2 OS' needs.

Make sure that "line wrapping" is not enabled on your text editor (it probably is by default).

Rename your file to 06 to 09_custom an save.  This will put those entries at the top of the menu you get on screen.  Leaving it as 40_custom will put them at the end of that menu.

---

