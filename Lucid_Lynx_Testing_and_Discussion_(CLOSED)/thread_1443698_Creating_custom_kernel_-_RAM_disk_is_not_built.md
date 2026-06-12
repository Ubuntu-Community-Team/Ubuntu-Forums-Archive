---
title: "Creating custom kernel - RAM disk is not built"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bike-and-snow on 2010-03-31
Hello

I have some experience in creating custom kernels and turning them into DEB packages.

I've done this several times without problems on previous versions of Ubuntu and Debian.

However, a kernel package I've built today for Lucid Beta 1 installs OK but it does not create the initial RAM disk. So it does not boot.

I can of course manually fix this by remembering to run "update-initramfs" each time I install, but this custom kernel is for many users will will not remember to do this. So it needs to work properly.

Here is an installation of a standard kernel in Lucid:

[FONT="Courier New"]
Unpacking linux-image-2.6.32-18-generic (from .../linux-image-2.6.32-18-generic_2.6.32-18.27_amd64.deb) ...
Examining /etc/kernel/preinst.d/
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.32.18.19_amd64.deb) ...
Setting up linux-image-2.6.32-18-generic (2.6.32-18.27) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-18-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.33.1-2-openvisor
Found initrd image: /boot/initrd.img-2.6.33.1-2-openvisor
Found linux image: /boot/vmlinuz-2.6.32-18-server
Found initrd image: /boot/initrd.img-2.6.32-18-server
Found linux image: /boot/vmlinuz-2.6.32-18-generic
Found initrd image: /boot/initrd.img-2.6.32-18-generic
Found linux image: /boot/vmlinuz-2.6.32-15-server
Found initrd image: /boot/initrd.img-2.6.32-15-server
done
Examining /etc/kernel/postinst.d.

Setting up linux-image-generic (2.6.32.18.19) ...
[/FONT]


And here is my kernel (based on 2.6.33.1, added to my repo):

[FONT="Courier New"]
Unpacking linux-image-2.6.33.1-2-custom (from .../linux-image-2.6.33.1-2-custom_2.6.33.1-2_amd64.deb) ...
Done.
Setting up linux-image-2.6.33.1-2-custom (2.6.33.1-2) ...
Running depmod.
Examining /etc/kernel/postinst.d.
Running postinst hook script update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.33.1-2-custom
Found linux image: /boot/vmlinuz-2.6.32-18-server
Found initrd image: /boot/initrd.img-2.6.32-18-server
Found linux image: /boot/vmlinuz-2.6.32-15-server
Found initrd image: /boot/initrd.img-2.6.32-15-server
done
[/FONT]

As you can see, the RAM disk is created OK in the Ubuntu kernel, but not in my custom kernel.

Does anyone know why? I've inspected the postinst script in the package and the initial RAM disk is set to "yes".

I'm building my kernel package as follows:

[FONT="Courier New"]make-kpkg --initrd --revision="2.6.33.1-2" --append-to-version="-2-custom" kernel-image[/FONT]

---

### Post by MacUntu on 2010-03-31
Don't know how to solve it, just confirming the issue.

---

### Post by master_kernel on 2010-03-31
I had solved this -- for some reason later versions of initramfs-tools do not have automatic access to the generation scripts. I'll post back with the fix soon.

---

### Post by master_kernel on 2010-03-31
Here's the fix:
```
cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/
```

Reference: [http://linuxagora.com/vbforum/showthread.php?t=1126](http://linuxagora.com/vbforum/showthread.php?t=1126)

---

### Post by Bike-and-snow on 2010-04-01
Thanks for the reply.

However, I've tried your suggestion on the build machine and rebuilt a new kernel package.

The initial RAM disk is still not created on the machine installing the kernel.

Any ideas?

---

