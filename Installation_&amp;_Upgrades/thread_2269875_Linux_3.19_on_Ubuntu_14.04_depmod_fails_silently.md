---
title: "Linux 3.19 on Ubuntu 14.04: depmod fails silently"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by jamapii on 2015-03-18
Hi,

I try to install a kernel 3.19 on Ubuntu 14.04 with make modules bzImage, sudo make modules_install install.

This works for 3.17 and in fact always worked for me for any kernel on any distribution as far back as that method existed.

However, now there is a silent failure when calling

depmod -v -w 3.19.1

It generates mostly empty files, and modules don't load automatically.
/lib/modules/3.19.1/modules.alias is only 45 bytes

No error messages

How come, what can be done (apart from using an older kernel)?

---

### Post by jamapii on 2015-03-18
ok, maybe I found it. I compressed the modules, CONFIG_MODULE_COMPRESS=y, and maybe kmod-15 of Ubuntu can't handle it. kmod-19 of Gentoo can. I made an initramfs with these compressed modules, this emits some error messages from update-initramfs, and will check if this works.

---

### Post by jamapii on 2015-03-18
last post disappeared

i compressed the modules and kmod-15 in ubuntu can't handle it. kmod-19 can, then making initramfs works with error messages but it boots incorrectly, i guess if kmod can't handle it it is expected

edit:
previous post reappeared...

with non compressed modules it works

---

