---
title: "Too many &quot;update-initramfs&quot; lines in update"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by tarobs on 2007-01-30
Yesterday (January 30, 2007, +8:00 GMT), I ran the update manager (I'm using Ubuntu 6.10 Edgy) and had an error (of some sort). A ***_lot_*** of the following line appeared when I expanded the terminal panel of the update manager:

> update-initramfs: Generating /boot/initrd.img-2.6.17-10-386

And then, it ended with:

> sudo: can't open /etc/sudoers: Too many open files in system

So, I decided to force quit the update manager and then I opened the Synaptic Package Manager to see if there is any error. It prompted me to manually run the following command to fix the problem because I interrupted the dpkg during the update:

```
sudo dpkg --configure -a
```

So, I did it in the terminal, but the same results (repeating "update-initramfs..." line, eventually ending with the "can't open..." line.

Does anyone know what the problem is?

---

