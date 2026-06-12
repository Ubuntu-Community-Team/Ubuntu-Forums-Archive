---
title: "Meaning of entries in /boot/grub/menu.lst"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by sg42 on 2009-12-12
Hi:

Looking at my /boot/gsub/menu.lst after a long time, i see a large number of entries of the form:

title        Ubuntu 9.04, kernel 2.6.28-XX-generic
title        Ubuntu 9.04, kernel 2.6.28-XX-generic (recovery mode)

where XX varies

I was wondering if anyone could explain what the different entries mean. Below is a copy of my menu.lst file.

Cheers.




```
title        Ubuntu 9.04, kernel 2.6.28-17-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.28-17-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.28-17-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.28-16-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.28-16-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.28-15-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.28-15-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.28-14-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.28-14-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.28-13-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.28-13-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.28-11-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.28-11-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-14-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.27-14-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, kernel 2.6.24-23-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.24-23-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.24-23-generic

title        Ubuntu 9.04, kernel 2.6.22-16-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.22-16-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.22-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.22-16-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.22-16-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.22-16-generic

title        Ubuntu 9.04, kernel 2.6.20-17-generic
root        (hd0,2)
kernel        /vmlinuz-2.6.20-17-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro quiet splash vga=773 
initrd        /initrd.img-2.6.20-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.20-17-generic (recovery mode)
root        (hd0,2)
kernel        /vmlinuz-2.6.20-17-generic root=UUID=de57202b-4cfd-4de3-8b3c-92c2267eb10a ro  single
initrd        /initrd.img-2.6.20-17-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,2)
kernel        /memtest86+.bin
quiet

```

---

### Post by coffeecat on 2009-12-12
The XX simply refers to different Ubuntu versions of the same kernel - that is, if the 2.6.YY number stays the same. During the life cycle of an Ubuntu distribution, the upstream kernel developers issue security patches for a particular kernel which the Ubuntu devs incorporate into the kernel and reissue the kernel with an incremented XX number. This is in case the patched kernel gives problems with certain hardware combinations. And that is why you get such a large choice in menu.lst - the older versions are not uninstalled in case you need to boot into them if the latest kernel is problematic for you.

I see from the bewildering number of kernels that you must have done several dist-upgrades. It looks like Feisty > Gutsy > Hardy > Intrepid > Jaunty. Am I right? :?

If you want to tidy up you can uninstall unwanted kernels by using Synaptic. Don't do it by editing menu.lst - you'll still have all the old kernel stuff all over the place. If you want to uninstall them, search Synaptic for the form 2.6.YY-XX and mark anything corresponding for uninstallation. Your menu.lst will get rewritten and simplified automatically if you do this.

---

### Post by phillw on 2009-12-12
+1 .. It is also advised to keep the last release of your kernel also (the next lowest number to your current one)

Phill.

---

### Post by sg42 on 2009-12-12
Thanks.  I'm currently doing my dist-upgrade to Karmic. Will follow your suggestions once that's done.

Cheers.

---

### Post by Ginsu543 on 2009-12-12
In order to remove a particular kernel using Synaptic, you must remove three files related to that kernel:

1) linux-headers-2.6.XX-xx
2) linux-headers-2.6.XX-xx-generic
3) linux-image-2.6.XX-xx-generic

Once you've removed the kernels you want in Synaptic, you can delete the references to those kernels in menu.lst. That way you won't have a long list in your boot menu.

---

