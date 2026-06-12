---
title: "reinstall lost kernel"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by ehmdjii on 2008-03-17
hello, i accidentally apt-get removed my existing kernel and now ubuntu wont boot anymore since grub cant find a kernel.

is there a way to reinstall just the kernel without having to reinstall the whole system?

maybe with the livecd?

thanks!

---

### Post by jeffus_il on 2008-03-17
I think you can boot the live cd and then chroot to your Ubuntu filesystem on disk and then run the install of the kernel. I don't remember the exact steps, and don't really want to experiment on my system, but post if you have problems and I am sure I (or someone else) can help.

---

### Post by ehmdjii on 2008-03-17
thank you, where do i find the root which is installed on disk?

/media/disk or /dev/sda6 ?

---

