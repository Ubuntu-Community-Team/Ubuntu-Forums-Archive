---
title: "ubuntu on non bios sd card"
date: 2017-05-02
forum: Installation &amp; Upgrades
---

### Post by dojohn on 2017-05-02
I would like to boot ubuntu from the internal sd card reader.

I tried installing ubuntu to an sdxc card, but the installed ubuntu does not boot because the sd card reader, located on a pci bus, is not seen by bios at boot.

I have seen the instructions on [https://help.ubuntu.com/community/BootFromSD](https://help.ubuntu.com/community/BootFromSD)

EDIT1
I had to mkdir the /dev /sys /proc in /mnt and sudo all commands to make them work from the live cd

EDIT2
I now get stuck at the step
$ sudo chroot /mnt
failed to run command &#8216;/bin/bash&#8217;: No such file or directory

I added
sudo mount --bind /bin /mnt/bin
just to make sure bin is there as well, but I get the same chroot error.

Do I need to copy /bin to the SD for chroot to work? EDIT: copied /bin to sd card, still unable to chroot.

How can I chroot to /mnt for this to work? thanks.

---

