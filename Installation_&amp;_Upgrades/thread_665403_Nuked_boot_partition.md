---
title: "Nuked /boot partition"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by sammydee on 2008-01-12
Hi all

I recently changed the partition structure on my hard disk. Before I did, I backed up all my / folder except /boot which is on a different partition to a separate hard disk.

I repartitioned the disk and restored the / partition but obviously realised I'd forgotten /boot. Without grub or a kernel I'm clearly not going to get back into my system, so i need a bit of help.

I think if I boot up into a linux cd, chroot into my hard disk linux install, mount a partition as /boot and then do a grub install and a kernel deb package install it should work just fine. I'm a little sketchy on exactly how chroot works though, so I'd appreciate a little bit of help with the details.

any ideas?

Thanks! Sam

---

### Post by Pumalite on 2008-01-12
[http://www.ss64.com/bash/chroot.html](http://www.ss64.com/bash/chroot.html)

---

### Post by sammydee on 2008-01-12
Do you think my method will work?

Sam

---

### Post by Pumalite on 2008-01-12
Read the link I gave you, learn to use 'chroot' and you'll be fine.

---

### Post by sammydee on 2008-01-15
Well I tried the chroot method and it didn't work.

In the end I just grabbed the entire home folder and stuck it on a usb disk, then reinstalled ubuntu and put all the files back again.

---

