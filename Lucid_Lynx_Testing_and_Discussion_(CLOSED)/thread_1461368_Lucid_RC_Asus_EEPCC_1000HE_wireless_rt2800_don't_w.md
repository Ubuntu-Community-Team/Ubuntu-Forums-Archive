---
title: "Lucid RC: Asus EEPCC 1000HE wireless rt2800 don't work"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by int on 2010-04-24
The wireless of Asus EEPCC 1000HE don't work.


It's an rt2800pci, And give conection for 2/10minuts and lost conection after.
I have to retry and retry to connect again for other 2/10minuts.
I have a clean Lucid RC installed. with all packages up-to-date.

I already try with linux-backports-modules-wireless-lucid-generic but it's the same.

When I'm connecting give some errores in dmesg:

```
===> rt_ioctl_giwscan. 16 (16) BSS returned, data->lenght = 1926
==> rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
...
..
..

```

---

