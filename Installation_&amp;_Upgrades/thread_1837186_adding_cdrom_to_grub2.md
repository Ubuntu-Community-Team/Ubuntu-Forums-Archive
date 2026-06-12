---
title: "adding cdrom to grub2"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by kr651129 on 2011-09-01
I would like to add an option to grub to boot from cd rom or usb...I've lost access to my bios and I need to boot from cd or usb and my motherboard wont let me unless I can get into the bios so I am going to flash them back to oem specs.  Ideas?

Thanks

---

### Post by coffeecat on 2011-09-02
I don't know how to boot a CD/DVD from grub, but you can boot an iso from grub. You could copy the ISO of the CD you want to boot onto somewhere convenient on the hard drive and then create a custom grub entry. Here's the howto thread:

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by oldfred on 2011-09-02
I use the  procedure coffeecat posted on directly booting ISOs either on hard drive or on flash drives. Then you do not have to burn CD and can have more than one ISO per flash drive up to space available.

But some where I ran across these entries & saved them. I have not used/tested them as I have not burned a CD for ages.

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

---

