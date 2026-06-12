---
title: "sis 630 video card"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by linuxzero on 2005-05-03
I have a sis 630 videro card. After downloaded the ubuntu 5.04
hoary and burn it to a CD, I tried to install it but it failed. It seems it could not detect my video card properly. During installation, it detectes a wrong driver for the card, and it causes my LCD screen turning to white color. Is there a way that I could setup my driver manually during installation. :-x

---

### Post by bored2k on 2005-05-03
sudo dpkg-reconfigure xserver-xorg

---

### Post by linuxzero on 2005-05-03
you mean I should type this "sudo dpkg-reconfigure xserver-xorg" on "boot:" prompt after I press F1 on the first screen of booting from the cdrom.

---

### Post by az on 2005-05-03
Hit escape during your boot to get into the grub menu (if it is not shown) and boot into recovery mode.
Then do it.

---

### Post by linuxzero on 2005-05-04
Thanks!

I fixed it by typing "linux vga=771" on the "boot" prompt.

---

