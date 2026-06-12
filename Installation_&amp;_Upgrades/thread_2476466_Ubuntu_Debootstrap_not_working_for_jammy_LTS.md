---
title: "Ubuntu Debootstrap not working for jammy LTS?"
date: 2022-06-27
forum: Installation &amp; Upgrades
---

### Post by gkaufmann on 2022-06-27
I've been trying to install ubuntu-minimal jammy using debootstrap but always the final "root" is incomplete missing /etc and even shell.

Debootstrap-Log inside /mnt (target) finally tells:
> /usr/sbin/debootstrap: 1007: ar: not found

I tried these commands:
1. debootstrap --arch=amd64 jammy /mnt [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu)
2. debootstrap --arch=amd64 --include=ubuntu-minimal --components=main,restricted,universe,multiverse jammy /mnt [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu)

Doing the same with focal release works flawless!

---

