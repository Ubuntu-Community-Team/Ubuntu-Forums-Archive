---
title: "No mouse pointer after new Ubuntu 14.10 installation"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by andy37927 on 2015-03-17
I just reinstalled Ubuntu on my Lenovo Y50-70 laptop and I have no mouse pointer. Neither the touchpad, nor my Logitech mouse are recognized. Left or right clicking doesn't do anything either.

I tried the following:
```
sudo modprobe -r psmouse
```
and
```
sudo modprobe psmouse
```

They both returned with the this error message:

modprobe: ERROR ../libkmod/libkmod-c:557 kmod_search_moddep() could not open moddep file '/lib/modules/3.2.0-51-generic/modules.dep.bin'

Please help. Thanks.

---

### Post by dino99 on 2015-03-17
i suppose it concern RTL8723BE chipset right ?

[https://www.google.fr/search?q=ubuntu+RTL8723BE&oq=ubuntu++RTL8723BE&aqs=chrome..69i57.21170j0j8&client=ubuntu&sourceid=chrome&es_sm=0&ie=UTF-8](https://www.google.fr/search?q=ubuntu+RTL8723BE&oq=ubuntu++RTL8723BE&aqs=chrome..69i57.21170j0j8&client=ubuntu&sourceid=chrome&es_sm=0&ie=UTF-8)

possible solution done: [https://ask.fedoraproject.org/en/question/42958/how-do-get-the-rtl8723be-wifi-card-working/](https://ask.fedoraproject.org/en/question/42958/how-do-get-the-rtl8723be-wifi-card-working/)

---

### Post by andy37927 on 2015-03-17
It might have something to do with my ethernet controller, because that also doesn't work.

Here it is: Realtek Semiconductor Co., Ltd. RTL 8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev10)

```

sudo ethtool eth0
```

Returned the following:
> 
Cannot get device: No such device
Cannot get wake-lan settings: No such device
Cannot get message-level: No such device
Cannot get link status: No such device
No data available

---

### Post by andy37927 on 2015-03-17
I have been trying to somehow install this: r8168-dkms_8.038.00-1_all.deb
because according to this: [http://ubuntuforums.org/showthread.php?t=2224262](http://ubuntuforums.org/showthread.php?t=2224262) it might work.

I managed to download it under windows but I can't "give it" to my linux any way:
-network doesn't work, so I can't download it as a package
-I can't see the common NTFS partition that I want my windows and linux to both use because: > mount: unknown filesystem type 'NTFS'
-I can't even open it on a FAT32 pendrive because > mount: unknown filesytem vfat

Something is seriously wrong:

This:
```
modinfo vfat
```
Returns with this:
> libkmod: ERROR ../libkmod/libkmod.c:557 kmod_search_moddep: Could not open moddep file '/lib/modules/3.2.0_51_generic/modules.dep.bin'
modinfo: ERROR: Module alias vfat not found

I had none of these problems under the previous installation (same computer, same os, same version), and when I booted it as a live cd (pendrive), everything was fine.

---

### Post by andy37927 on 2015-03-21
I solved it by reinstalling Ubuntu. I did it everything the same way as before, but now it works.

---

