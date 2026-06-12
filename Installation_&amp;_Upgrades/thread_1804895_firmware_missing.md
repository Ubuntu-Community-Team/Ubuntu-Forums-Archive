---
title: "firmware missing"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by r_joy on 2011-07-15
Hi,

New to Ubuntu, I installed 11.4 and had the popular message "device not ready (firmware missing)"

The repositories have endless packages to download, and the various forums that try to trouble shoot this problem seem to be unique per user.

Sorry for being slow.

How do I figure out which package I need?
How do I find that package?
How do I install it?

Thanks

---

### Post by dino99 on 2011-07-15
open a terminal, and run:

sudo update-initramfs -u -v
sudo dpkg-reconfigure -phigh -a
(wait a moment till it end itself, can take time)

sudo apt-get install -f
sudo apt-get install ubuntu-desktop (in case you are using gnome indeed, otherwise replace by the related desktop package)

---

