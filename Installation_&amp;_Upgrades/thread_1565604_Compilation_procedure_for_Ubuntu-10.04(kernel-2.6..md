---
title: "Compilation procedure for Ubuntu-10.04(kernel-2.6.32)"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by grsandeep85 on 2010-09-01
Hi ,

       I am using the ubuntu 10.04 with kernel-2.6.32 i have download the ubuntu kernel source(linux-source-2.6.32) and i have added the my driver in the source now i need to compile the custom kernel of this source and build it. Can anyone brief about the compilation steps and procedure for this ubuntu version.

Thanks & Regards,
Sandeep

---

### Post by andrewthomas on 2010-09-01
read [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

and post back if you have any questions.

---

### Post by grsandeep85 on 2010-09-02
Hi,

    I had followed the link provided by you so that it compiled successfully now i had struck with the command
sandeep@sandeep-desktop:~/src/linux-source-2.6.32$ sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postrm.d/initramfs /etc/kernel/postrm.d/initramfs
cp: cannot create regular file `/etc/kernel/postrm.d/initramfs': No such file or directory
sandeep@sandeep-desktop:~/src/linux-source-2.6.32$ 

How to proceed with further..

---

### Post by andrewthomas on 2010-09-02
> **grsandeep85 said:**
> Hi,
```

    $ sudo cp /usr/share/doc/kernel-package/examples/etc/kernel/postrm.d/initramfs /etc/kernel/postrm.d/initramfs
cp: cannot create regular file `/etc/kernel/postrm.d/initramfs': No such file or directory
```

Why are you doing this?  Did you install the kernel using dpkg?
```
sudo dpkg -i /path/to/file
```

---

### Post by grsandeep85 on 2010-09-03
> **andrewthomas said:**
> Why are you doing this?  Did you install the kernel using dpkg?
```
sudo dpkg -i /path/to/file
```



Hi,

     I tried installing the kernel using dpkg but it logged error as follows 

sandeep@sandeep-desktop:~/src$ ls
linux-headers-2.6.32.15+drm33.5-san_2.6.32.15+drm33.5-san-10.00.Custom_i386.deb  linux-source-2.6.32
linux-image-2.6.32.15+drm33.5-san_2.6.32.15+drm33.5-san-10.00.Custom_i386.deb
sandeep@sandeep-desktop:~/src$ sudo dpkg -i linux-image-2.6.32.15+drm33.5-san_2.6.32.15+drm33.5-san-10.00.Custom_i386.deb
Selecting previously deselected package linux-image-2.6.32.15+drm33.5-san.
(Reading database ... 181315 files and directories currently installed.)
Unpacking linux-image-2.6.32.15+drm33.5-san (from linux-image-2.6.32.15+drm33.5-san_2.6.32.15+drm33.5-san-10.00.Custom_i386.deb) ...
Done.
Setting up linux-image-2.6.32.15+drm33.5-san (2.6.32.15+drm33.5-san-10.00.Custom) ...
Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs 2.6.32.15+drm33.5-san /boot/vmlinuz-2.6.32.15+drm33.5-san
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32.15+drm33.5-san /boot/vmlinuz-2.6.32.15+drm33.5-san
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32.15+drm33.5-san.postinst line 341.
dpkg: error processing linux-image-2.6.32.15+drm33.5-san (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32.15+drm33.5-san
sandeep@sandeep-desktop:~/src$ 

How to resolve this.

---

### Post by grsandeep85 on 2010-09-03
Hi,

          The issue got resolved for by using the following commands

sudo apt-get purge nvidia-common
sudo apt-get install nvidia-common

---

