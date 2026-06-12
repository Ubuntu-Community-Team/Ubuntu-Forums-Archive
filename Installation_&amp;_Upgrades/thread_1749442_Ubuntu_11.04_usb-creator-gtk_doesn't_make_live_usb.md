---
title: "Ubuntu 11.04 usb-creator-gtk doesn't make live usb persistent even if selected?"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by slny on 2011-05-04
I followed the instructions here:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
and used usb-creator-gtk to make a live usb stick, selecting the option to create a casper-rw file for persisting changes.

However, after reboot, all changes were lost.

It seems that the grub entry needs a "persistent" added to the end:
menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
    initrd    /casper/initrd.lz
}

Were the instructions wrong/incomplete or am I missing something else?

This posts also mentions needing to add persistent to grub.cfg:
[http://ubuntuforums.org/showthread.php?p=10745015](http://ubuntuforums.org/showthread.php?p=10745015)

---

