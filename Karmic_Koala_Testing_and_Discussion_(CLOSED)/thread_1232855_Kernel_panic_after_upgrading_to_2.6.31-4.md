---
title: "Kernel panic after upgrading to 2.6.31-4"
date: 2009-08-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-06
After upgrading and rebooting the machine freezes. I enabled text mode to see what was happening and a I saw a bunch of errors related to sierra wireless but then the screen froze with this being the last screen:

[[IMG]http://img11.imageshack.us/img11/9691/img5404e.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=img5404e.jpg)


Also, I thought I upgraded to 2.6.31-5. See screenshot of Synaptic: 

[[IMG]http://img170.imageshack.us/img170/5076/synaptic.th.png[/IMG]](http://img170.imageshack.us/my.php?image=synaptic.png)

But grub only shows 2.6.31-4 (and older ones)
Since 2.6.31-4 fails I have to boot with 2.6.31-3.

Am I missing something?

---

### Post by budluva04 on 2009-08-06
check in /boot and make sure the 31-5 kernel is there...

$ sudo update-grub

should find your new kernel

---

### Post by andresmh on 2009-08-06
Thanks. It did find it:

```

andresmh@karmicx300:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found linux image: /boot/vmlinuz-2.6.31-4-generic
Found initrd image: /boot/initrd.img-2.6.31-4-generic
Found linux image: /boot/vmlinuz-2.6.31-3-generic
Found initrd image: /boot/initrd.img-2.6.31-3-generic
Found linux image: /boot/vmlinuz-2.6.31-2-generic
Found initrd image: /boot/initrd.img-2.6.31-2-generic
Found linux image: /boot/vmlinuz-2.6.30-8-generic
Found initrd image: /boot/initrd.img-2.6.30-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
andresmh@karmicx300:~$ cd /boot/
andresmh@karmicx300:/boot$ ls
abi-2.6.30-8-generic     config-2.6.31-2-generic      initrd.img-2.6.31-2-generic  System.map-2.6.31-2-generic  vmcoreinfo-2.6.31-3-generic  vmlinuz-2.6.31-4-generic
abi-2.6.31-2-generic     config-2.6.31-3-generic      initrd.img-2.6.31-3-generic  System.map-2.6.31-3-generic  vmcoreinfo-2.6.31-4-generic  vmlinuz-2.6.31-5-generic
abi-2.6.31-3-generic     config-2.6.31-4-generic      initrd.img-2.6.31-4-generic  System.map-2.6.31-4-generic  vmcoreinfo-2.6.31-5-generic
abi-2.6.31-4-generic     config-2.6.31-5-generic      initrd.img-2.6.31-5-generic  System.map-2.6.31-5-generic  vmlinuz-2.6.30-8-generic
abi-2.6.31-5-generic     grub                         memtest86+.bin               vmcoreinfo-2.6.30-8-generic  vmlinuz-2.6.31-2-generic
config-2.6.30-8-generic  initrd.img-2.6.30-8-generic  System.map-2.6.30-8-generic  vmcoreinfo-2.6.31-2-generic  vmlinuz-2.6.31-3-generic
andresmh@karmicx300:/boot$ 

```

---

