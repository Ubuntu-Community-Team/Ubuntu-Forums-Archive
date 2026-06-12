---
title: "Most recent linux kernel won't install"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by malachi1990 on 2010-02-11
Hi!

In today's upgrade, there was was an update to the kernel, and it's apparently unable to find a certain file, so it won't install.  Here is the output of dpkg --configure -a

Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

Thank your for your time.

---

### Post by zika on 2010-02-11
> **malachi1990 said:**
> Hi!

In today's upgrade, there was was an update to the kernel, and it's apparently unable to find a certain file, so it won't install.  Here is the output of dpkg --configure -a

Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

Thank your for your time.[http://ubuntuforums.org/showthread.php?t=1403446](http://ubuntuforums.org/showthread.php?t=1403446)
[http://ubuntuforums.org/showthread.php?t=1403449](http://ubuntuforums.org/showthread.php?t=1403449)

---

### Post by dino99 on 2010-02-11
update first, new packages have been upload several hours ago  :o

---

### Post by zika on 2010-02-11
> **dino99 said:**
> update first, new packages have been upload several hours ago  :oI do not think upgrade is possible before this glitch is solved ... That glitch prevents from upgrade-ing... At least that was the case on my machine...

---

### Post by dino99 on 2010-02-11
from one of your previous post:

 Re: Problem with update-initramfs after upgrade
you can do it like that:
Code:

cd /
sudo wget [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch)
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patch

---

### Post by zika on 2010-02-11
> **dino99 said:**
> from one of your previous post:

 Re: Problem with update-initramfs after upgrade
you can do it like that:
Code:

cd /
sudo wget [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch)
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patchThis is not from my post, but it doesn't make a difference. I circumvented this problem by brutal editing... Solution is in one of two therad mentioned above and...  Enjoy!

---

### Post by glasen on 2010-02-11
Why not just install the lastest version of the "udev"-package? The bug is fixed in this version since yesterday.

---

### Post by dino99 on 2010-02-11
dogs glancing their tails

---

### Post by zika on 2010-02-11
> **glasen said:**
> Why not just install the lastest version of the "udev"-package? The bug is fixed in this version since yesterday.At least at my machine, the bug we are talking about prevented dpkg finishing previous upgrade and prevented any further upgrading... Listen, I've solved "my problem" yesterday, so ...

---

### Post by aamukahvi on 2010-02-11
```
cd /
sudo wget http://launchpadlibrarian.net/39011493/udev-firmware.patch
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patch
```
> **zika said:**
> This is not from my post, but it doesn't make a difference. I circumvented this problem by brutal editing... Solution is in one of two therad mentioned above and...  Enjoy!

It's a bit tricky, because you can't just copy/paste the whole thing or it will only run the first two lines (until the first sudo prompt). Copy one line at a time and it works :)

---

### Post by zika on 2010-02-11
> **aamukahvi said:**
> ```
cd /
sudo wget http://launchpadlibrarian.net/39011493/udev-firmware.patch
sudo patch -Np0 < udev-firmware.patch
sudo rm udev-firmware.patch
```
It's a bit tricky, because you can't just copy/paste the whole thing or it will only run the first two lines (until the first sudo prompt). Copy one line at a time and it works :)As I, already, said, several times, I prefer "brutal editing" because I, that way, at least have an illusion that, I know what I'm doing... Nevertheless, patch mechanism is a good tool...

---

### Post by malachi1990 on 2010-02-11
Thanks for the help, and sorry for posting a duplicate. I didn't notice the initramfs thread in my earching.

---

### Post by aamukahvi on 2010-02-11
> **zika said:**
> As I, already, said, several times, I prefer "brutal editing" because I, that way, at least have an illusion that, I know what I'm doing... Nevertheless, patch mechanism is a good tool...

Ah, got it. I thought by "makes no difference" you meant "it's not working for me".

---

