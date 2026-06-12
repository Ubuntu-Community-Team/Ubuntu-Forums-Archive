---
title: "Where is the swap file?"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by steve169 on 2018-04-30
I used a live CD to install Lubuntu 18.04 on a 16-Gb flash drive. I will use it to run Lubuntu independent of any hard drive.

After the installation, Gparted showed there was just one partition spanning the entire flash drive.

Isn't there supposed to be a boot partition and a swap file partition?

---

### Post by sudodus on 2018-04-30
There is a swap file (not a partition) and it is in the top level of the only partition, **/swapfile**.

You can see it (location and size) with the command

```
swapon
```

---

### Post by steve169 on 2018-05-01
Dear Sudodus,

Many thanks from a grateful newbie.

---

### Post by sudodus on 2018-05-01
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

