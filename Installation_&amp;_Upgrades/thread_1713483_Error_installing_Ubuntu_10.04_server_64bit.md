---
title: "Error installing Ubuntu 10.04 server 64bit"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by fernandezvara on 2011-03-24
Hi all,

thanks in advance if someone can put some light on this.

I have downloaded and used the Universal USB Installer to make the USB installation stick.

When I boot the computer it doesn't allow me begin the installation, pressing enter on 'Install Ubuntu' makes nothing, it returns me to the menu.

If I try with the rescue mode it works.

Must I make some changes to the stick files? Or am I doing something wrong?

thanks.

-- Antonio

---

### Post by fernandezvara on 2011-03-24
Found the error.

Pressing TAB over the option for install it was using a different path for the kernel location.

I have changed from /install/ubuntu-installer/i386 to /install/ubuntu-installer/amd64 and the installation began.

---

