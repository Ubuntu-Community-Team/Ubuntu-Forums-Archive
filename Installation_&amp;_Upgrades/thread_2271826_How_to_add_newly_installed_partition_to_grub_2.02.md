---
title: "How to add newly installed partition to grub 2.02"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by blahman179 on 2015-04-01
I've had Ubuntu and Windows booting together for a while.

I recently wanted to try out Puppy Arcade, so I created a partition for it and installed it to the newer partition.

The only problem is Puppy Arcade won't show up at boot along side Ubuntu and Windows in grub.

I tried using a Live CD and running Boot Repair, but that disn't work.

Help would be greatly appreciated.

Edit: Running grub-update gives me this;

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done


It doesn't even show up here.

Maybe I installed it wrong?

---

### Post by Bucky Ball on 2015-04-01
Perhaps give us the output of:

```
sudo blkid
```

Open Gparted (install if not already there) and see if the Puppy partition shows up there.

* Please use code tags for terminal output. See the last link in my signature for how. ;)

---

### Post by sammiev on 2015-04-01
This is how it's done.

[http://mylinuxexplore.blogspot.ca/2012/06/how-to-add-puppy-linux-frugal.html](http://mylinuxexplore.blogspot.ca/2012/06/how-to-add-puppy-linux-frugal.html)

---

### Post by oldfred on 2015-04-01
To see all the details, post link to Summary report:

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

