---
title: "can't boot into newly Compiled kernel 2.6.20 from scratch"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by alimovz on 2007-06-08
Hey guys,

I downloaded the sources from kernel.org for 2.6.20. Ran make xconfig, ran make. bzImage was created, I copied it into the /boot directory as vmlinuz-2.6.20. Then I ran make modules-install which created direcotry /lib/modules/2.6.20 with everything that is supposed to be in there eg modules.dep etc..
I also made a initrd.img by running mkinitrd -o /boot/initrd.img.
Here is the grub menu.lst lines:
title 2.6.20 Custom Built Kernel
root (hd0,2)
kernel /boot/vmlinuz-2.6.20 root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img


When I select this option in the grub menu, an error message shown on the screen after like 10 seconds that says:
Can't open /lib/modules/2.6.20 no such file or directory
can't load /lib/modules/2.6.20/modules.dep no such file or directory
...
...
And so on.

But that directory is there!! make modules-install created it. I checked, the directory exists!!

Does any one have any ideas? What is wrong there?

Thanks.

---

### Post by Bachstelze on 2007-06-08
Try /dev/hda3 instead of /dev/sda3 in your kernel line.

---

### Post by alimovz on 2007-06-08
For some reason these commands work:
sudo sudo make-kpkg --initrd --append-to-version=-custom kernel_image
sudo dpkg -i linux-image-2.6.21-custom_2.6.21-custom-10.00.Custom_i386.deb

They essentially do the same thing, but they actually work. The only difference that I noticed is the commands above will automatically update your menu.lst file, while simply running make you will have to modify the file manually.  Weird.

---

