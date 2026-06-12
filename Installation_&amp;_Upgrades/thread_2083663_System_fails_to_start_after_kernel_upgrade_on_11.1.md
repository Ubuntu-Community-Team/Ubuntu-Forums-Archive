---
title: "System fails to start after kernel upgrade on 11.10 x64"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by slenderman on 2012-11-13
Hello everybody.

Basically, the problem is stated in the title. I had an Ubuntu 11.10 x64, kernel version 3.0.0-12. Recently, because of some reasons, I had to upgrade the kernel to version >=3.3. I have downloaded the binary package files from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/) and installed them. Unfortunately, after that, Ubuntu just failed to boot. I just see the purple screen and nothing happens. Ctrl+Alt+F1 doesn't work. What have I done wrong?

My PC configurations is the following:
CPU: Intel Core i7 3770k (Ivy Bridge)
Mainboard: Asus P8277-V LX, LGA1155
Graphics: Sapphire HD 6450 Flex (based on NVIDIA GT 610)

P.S. I've heard that the nvidia drivers often is a problem if you want to update the kernel. However, I had no nvidia drivers installed when updating.

---

### Post by ercherramon on 2012-11-13
you installed the three packages in the correct order?

```
linux-headers_all.deb

linux-headers-generic_amd64

linux-image-generic_amd64
```

tries to enter the previous kernel and uninstalled everything. and applied:

```
sudo update-grub
```

if you want to try again, install packages in that order. if you still show problem with the kernel, you may need to update your graphics card drivers.

---

### Post by slenderman on 2012-11-13
[ercherramon]("http://ubuntuforums.org/member.php?u=984688"),

Yes, I did it exactly like this, but things did not work out well for some reason.

---

