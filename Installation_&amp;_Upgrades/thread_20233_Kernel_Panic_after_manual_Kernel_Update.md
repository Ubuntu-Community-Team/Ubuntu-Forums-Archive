---
title: "Kernel Panic after manual Kernel Update"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by void on 2005-03-15
hi there,

im using ubuntu 4.10 since its release and never had any bigger trouble wih it but one
every time im manually compiling a kernel, im receiving a kernel panic
"dep modules not found in 2.6.8.1" or similar to that

i never had any problems with kernel compiling on other machines (SuSE, Mandrake, Fedora). due to the fact that im quite new to linux im quite sure im missing something,

now to the details:

i have to compile the kernel every time a new one is released because of the following reasons.

1st: the kernel i get via the apt-get update and upgrade procedure is never configured to recognize my 1GB RAM fully, the Highmem Option is always off
2nd: the kernel is also never configured with framebuffer, so i always get a blank screen during the boot up until gdm is starting up.
i know i could use vga=771 but then im getting a low resolution, i dont want

how i configure, make,install and so on my kernel

downloading the sources and the header files
for example the newest ones

linux-source-2.6.8.1 version 2.6.8.1-16.12
linux-headers-2.6.8.1-5-686 version 2.6.8.1-16.12

(one thing i dont know: do i have to do anything with the header files ?
like integrating in the source, could this causing the problem ?)

deleting the old /usr/src/linux-source-2.6.8.1 directory
unpacking the tarball of the new sources in the same dir
changing to the /usr/src/linux dir

make mrproper

copying my old .config file to the new dir

make menuconfig (just to control a few settings, framebuffer and highmem ;))

make bzImage
make modules
make modules_install

then im copying the bzImage, System.map to
/boot/vmlinuz-2.6.8.1-5-686
/boot/System.map-2.6.8.1-5-686

then im creating the init file

mkinitrd -o /boot/initrd-2.6.8.1-5-686.img 2.6.8.1-5-686

finally im adding to the /boot/grub/menu.lst
 
title Ubuntu, kernel 2.6.8.1-5-686
#:2 <-- type: 0 => linux, 1 => windows, 2 => other
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.8.1-5-686 root=/dev/hda7 vga=0x31b ro quiet splash
initrd		/boot/initrd-2.6.8.1-5-686.img
savedefault
boot

after rebooting i always get the message that the modules in /lib/modules/2.6.8.1 
are not found.
they are there, but for the old kernel
afaik have the new ones to be in the /lib/modules/2.6.8.1-5-686 dir

so why is the kernel still using the old modules ?
this is causing the problem isnt it ?

thx in advance

---

### Post by void on 2005-03-21
bump

does anyone know of this problem ?

---

### Post by MiddleBrooker on 2005-03-24
Dear Void,
I don't know your specific problem, but I suggest you to compile and install your kernel through the classical make-kpkg that provide a very simple and efficent way to buil a custom kernel.

```

cd /usr/src/kernel-source-XXX
sudo make mrproper
sudo make menuconfig

--------> Save you kernel configuration

sudo make-kpkg clean
sudo make-kpkg buildpackage --revision=1.0.MyCustomKernel --append-to-version=.240305 kernel_image --initrd binary

```

Now you should have all the kernel packages under /usr/src directory, and you can safely install your custom kernel through:

```


sudo dpkg -i kernel-image....XXX


```

The kernel modules uder /lib/modules/ will be automatically create.

I hope that this can be useful for you.

Best Regards,

MiddleBrooker

---

