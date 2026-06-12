---
title: "unable to load ubuntu after installation"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by krishnachaitanya on 2007-08-06
Hi

  I successfully installed ubuntu from live cd but when i restated the machine, i expected it to detect
xp(which i originally had) and ubuntu(which i newly installed), but the machine just went ahead and loaded
windows xp. Now I am unable to understand if it is a partition problem or if i need to do more things.

---

### Post by merlinus on 2007-08-06
Did you choose to install grub during installation?  Did the grub menu appear upon startup?

-merlin

---

### Post by krishnachaitanya on 2007-08-07
I thought grub would be installed by default. During installation it did not ask me anything about grub.
When I restart Windows starts as usual as if ubuntu was never there.

> **merlinus said:**
> Did you choose to install grub during installation?  Did the grub menu appear upon startup?

-merlin

---

### Post by merlinus on 2007-08-07
Try this:

Boot from ubuntu live cd, open a terminal and enter:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute results from find for (hdx,x).  I would expect it to be (hd0,1).

Also, post output of:

```

sudo fdisk -l

```

-merlin

---

