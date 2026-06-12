---
title: "can't boot GUI after release upgrade/install"
date: 2020-12-03
forum: Installation &amp; Upgrades
---

### Post by louisrrr on 2020-12-03
Hi

I am trying to installUbuntu 20.04 LTS on my Thinkpad T450. But I get a black screen at boot

I have a'grub rescue' error first, so I have to do a boot-repair (from live usb), and at next reboot, I see a black screen.

```
$ lspci | grep VGA
VGA compatible controller: Interl Corporation HD Graphics 5500 (rev09)
```

The Ubuntu live USB is running really well.

Can you help ?
Thanks

---

### Post by CelticWarrior on 2020-12-03
Welcome.

Does it have Nvidia as well? A quick google search suggests that.
Please disable Secure Boot in UEFI and try again.

---

