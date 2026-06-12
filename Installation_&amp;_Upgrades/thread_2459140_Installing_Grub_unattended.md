---
title: "Installing Grub unattended"
date: 2021-03-11
forum: Installation &amp; Upgrades
---

### Post by deever2 on 2021-03-11
Hi folks!

I'm trying to install Ubuntu (focal) from a Live system using debootstrap with the attached bootstrap-ubuntu script.
This works fine when I manually confirm the dpkg dialogs and select /dev/sda.
However I'd like to run this completely unattended and when I replace the linux-generic install line with
```
DEBIAN_FRONTEND=noninteractive chroot /mnt apt-get install -yq linux-generic
chroot /mnt grub-install /dev/sda
chroot /mnt update-grub
```
, Grub won't be installed, at least not in a state that makes it boot the system.

Can anyone help me, please?

---

### Post by deever2 on 2021-03-13
Just for the record:I had to preseed the answer with this:
```
echo "deb http://archive.ubuntu.com/ubuntu focal universe" >> /mnt/etc/apt/sources.list
chroot /mnt apt-get update
chroot /mnt apt-get install -y debconf-utils
disk=$(find /dev -type l -lname '*/sda' -path '*/by-id/*')
chroot /mnt debconf-set-selections << HERE_I_AM
grub-pc    grub-pc/install_devices    multiselect    $disk
HERE_I_AM
chroot /mnt apt-get install -y linux-generic
...
```

---

