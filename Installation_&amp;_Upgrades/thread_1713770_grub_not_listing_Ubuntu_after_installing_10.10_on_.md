---
title: "grub not listing Ubuntu after installing 10.10 on PC alongside 64studio, Win installs"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by haszari on 2011-03-24
I've just installed Ubuntu 10.10 (desktop, 32 bit) on a machine that already has 2 older installs of 64studio (a variant of debian) and Windows XP. The install completes successfully, but the grub menu on reboot is the old menu listing Windows and the 2 64Studio installations - the new Ubuntu doesn't seem to be there.

I am fairly certain that the previous grub install is pre-grub2, and I understand that Ubuntu 10.10 installs grub2 - is this perhaps a factor?

Anyway if someone can give me some info on how to get the new Ubuntu install to boot I'd really appreciate it - thanks.

---

### Post by zvacet on 2011-03-26
Try in terminal

```
sudo apt-get install --reinstall libdebian-installer4
```

```
sudo os-prober
```

```
sudo update-grub
```

---

### Post by haszari on 2011-04-02
Almost there - os-prober finds all the things I want to boot into, but update-grub fails with this error:

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

How do I solve this? 

thanks for the help :)

---

