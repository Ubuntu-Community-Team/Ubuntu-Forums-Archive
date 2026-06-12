---
title: "how to increase screen resolution on laptop"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by niko11 on 2015-01-09
hi, I am new with lubuntu.
I installed lubuntu on an old laptop Gericom Webshox Performance, but the automatically detected screen resolution is only 640x480.
With Windows XP it was 1024x768.

Setting the better resolution with xrandr and lxrandr does not work. I always get the information that there is only 640x480 available.

What can I do?
(using lubuntu with 640x480 is not practicable)

Niko11

---

### Post by sudodus on 2015-01-09
Welcome to the Ubuntu Forums :-)

Maybe it will help if you edit the file **/etc/default/grub**

```
sudo nano /etc/default/grub
```

from

```
# Uncomment to disable graphical terminal (grub-pc only)
[COLOR=#ff0000]#[/COLOR]GRUB_TERMINAL=console
```

to

```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
```

and make it active by running

```
sudo update-grub
```

and reboot the computer.

---

### Post by niko11 on 2015-01-09
thank you very much: now I have the desired resolution:p

how can I mark this threat as solved?

Niko11

---

### Post by sudodus on 2015-01-09
I'm glad it works :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

