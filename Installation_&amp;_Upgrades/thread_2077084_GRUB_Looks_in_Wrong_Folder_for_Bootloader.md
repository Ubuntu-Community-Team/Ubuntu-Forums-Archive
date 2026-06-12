---
title: "GRUB Looks in Wrong Folder for Bootloader"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by stevo1977 on 2012-10-27
I have my /boot directory installed on its own partition. When I tried to boot it went to <grub rescue> and when I checked the prefix it said

```
prefix=(hd0,msdos1)/boot/grub
```
The problem is, that partition *is* the boot directory so that path is basically looking for grub in "/boot/boot/grub". I can get it to boot by using

```
set prefix=(hd0,msdos1)/grub
```
but I have to do that at every boot.

I'd like to find a way to make that solution more permanent. I looked around in /etc/default/grub but couldn't find where that path is defined. Obviously I could just create the new directory /boot/boot/ and move the grub folder there but that seems stupid. Any ideas?

Cheers,
stevo

---

### Post by oldfred on 2012-10-27
How do you have it mounted in fstab?

I would think if mount is consistent with location then just reinstall to sda would work.
sudo grub-install /dev/sda

---

### Post by stevo1977 on 2012-10-27
And that did it. Thank you kindly, oldfred. I had reinstalled grub from a live cd a few times, but once I got the OS going I had not tried reinstalling grub again. Thanks again!

Cheers,
stevo

---

