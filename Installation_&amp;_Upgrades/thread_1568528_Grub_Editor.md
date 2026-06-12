---
title: "Grub Editor"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by AZinOH on 2010-09-05
I've just finished an upgrade (not a clean install) from 8.04 to 10.04. It went smoothly, except that Grub still lists all the old kernels for 8.04. In the old version, there used to be a QGrubedit that I used to remove them, but that appears to be no longer an option. Is there a way to get this done other than using the CLI? Thanks for any assistance.

---

### Post by zvacet on 2010-09-06
If you don´t need Hardy kernels remove them from synaptic.Type linux-image in search box and then remove kernels wuth lower number.After that 

```
sudo update-grub
```

---

### Post by kansasnoob on 2010-09-06
> **AZinOH said:**
> I've just finished an upgrade (not a clean install) from 8.04 to 10.04. It went smoothly, except that Grub still lists all the old kernels for 8.04. In the old version, there used to be a QGrubedit that I used to remove them, but that appears to be no longer an option. Is there a way to get this done other than using the CLI? Thanks for any assistance.

Since you upgraded from Hardy to Lucid you probably still have legacy grub, you can find out by running in terminal:

```
grub-install -v
```

Basicall 0.9* is legacy grub and 1.9* is grub2.

If you still have legacy grub you should be able to sort the menu by installing "startupmanager", under the Advanced tab you can limit the number of kernels to display. I recommend selecting "2" because it's always best to have one older kernel to fall back on just in case an update fouls things up.

---

