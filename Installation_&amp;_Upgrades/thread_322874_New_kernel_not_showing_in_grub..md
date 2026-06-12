---
title: "New kernel not showing in grub."
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by hougtimo on 2006-12-21
Hi,

I have just got the k7smp kernel for my pc (as i run an athlon64 X2 4200+) and someone mentioned that i would get a speed increase if i did. So i installed it using > sudo apt-get install linux-k7-smp. It seems to have installed successfully, but it won't show up in grub when I boot, only the default 386 kernel is listed.

Any help is greatly appreciated. Running Edgy by the way.

Tim

---

### Post by hal10000 on 2006-12-21
try to remove and reinstall the package:
sudo apt-get remove linux-k7-smp
sudo apt-get install linux-k7-smp
when reinstalling you have to get a message like "updating grub ....."
After install, you should have some new files in your /boot directory:
vmlinuz-2.6.17-10-k7-smp 
System.map-2.6.17-10-k7-smp
initrd.img-2.6.17-10-k7-smp

---

### Post by ukch on 2006-12-21
Just run: ```
sudo update-grub
```

It should add all the existing kernels to the menu.lst.

---

### Post by hal10000 on 2006-12-21
@ukch:
that' right, but update-grub should appear automatically if you install it with apt-get?????

---

### Post by jgcamp99 on 2006-12-21
Running Edgy ? The K7 kernels are obsoleted, there's a generic kernel that encompasses this now.

---

### Post by mlind on 2007-01-02
To get grub run automatically after a new kernel install, make sure you have following stanza in your **/etc/kernel-img.conf**
```

postinst_hook = /usr/sbin/update-grub
postrm_hook = /usr/sbin/update-grub
do_bootloader = No

```

---

