---
title: "grub rescue boot repair"
date: 2022-12-29
forum: Installation &amp; Upgrades
---

### Post by i0wnz0r3 on 2022-12-29
when I made the jump from ubuntu 18 to 20.04 my ssd started having boot issues- it would drop me to a initramfs shell - from there i could cryptsetup luksopen. Once unloacked i could exit de initramfs shell then continue on to boot.

I tried using boot-repair to fix my issue but now it sends me to a grub rescue shell - from which i cannot boot.

It shows me on ls:
(hd0) (hd0,msdos1) (hd0,msdos2)

Neither shows me anything when doing LS

Here's de pastebin from boot repair:
[https://paste.ubuntu.com/p/YrpNxFvpQ6/](https://paste.ubuntu.com/p/YrpNxFvpQ6/)

Thanks for all the help in advance!

---

### Post by i0wnz0r3 on 2022-12-29
here's a second paste after I unplugged my md array:

[https://paste.ubuntu.com/p/NchYQcWdJY/](https://paste.ubuntu.com/p/NchYQcWdJY/)

---

