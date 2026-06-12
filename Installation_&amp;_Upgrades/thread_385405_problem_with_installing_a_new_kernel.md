---
title: "problem with installing a new kernel"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by pollyp on 2007-03-15
Hi all,

I've built custom kernels a couple of times now, but have run into a real puzzler. I have a 6.10 install, and I grabbed the 2.6.17.114-ubuntu source and recompiled it to get kernel_image and kernel-header. I got my .deb files, and while the install appears to go fine, the new kernel never gets into the grub file, and the /boot/vmlinuz-<blah> file never gets created. 

Here's the play-by-play:

make oldconfig
make-kpkg clean
make-kpkg --initrd --append-to-version=-mdv2 kernel_image kernel_headers

[wait a while, then cd to /usr/src]

# dpkg -i linux-image-kdump_2.6.17.14-ubuntu1-mdv2-10.00.Custom_i386.deb 
Selecting previously deselected package linux-image-kdump.
(Reading database ... 104550 files and directories currently installed.)
Unpacking linux-image-kdump (from linux-image-kdump_2.6.17.14-ubuntu1-mdv2-10.00.Custom_i386.deb) ...
Done.
Setting up linux-image-kdump (2.6.17.14-ubuntu1-mdv2-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17.14-ubuntu1-mdv2
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@tlc:/usr/src# dpkg -i linux-headers-2.6.17.14-ubuntu1-mdv2_2.6.17.14-ubuntu1-mdv2-10.00.Custom_i386.deb 
Selecting previously deselected package linux-headers-2.6.17.14-ubuntu1-mdv2.
(Reading database ... 106558 files and directories currently installed.)
Unpacking linux-headers-2.6.17.14-ubuntu1-mdv2 (from linux-headers-2.6.17.14-ubuntu1-mdv2_2.6.17.14-ubuntu1-mdv2-10.00.Custom_i386.deb) ...
Setting up linux-headers-2.6.17.14-ubuntu1-mdv2 (2.6.17.14-ubuntu1-mdv2-10.00.Custom) ...

But the new kernel never makes it into my /boot/grub/menu.lst. Here is what is in my boot directory:

root@tlc:/usr/src# ls /boot
abi-2.6.17-10-generic              memtest86+.bin
config-2.6.17-10-generic           System.map-2.6.17-10-generic
config-2.6.17.14-ubuntu1-mdv2      System.map-2.6.17.14-ubuntu1-mdv2
grub                               vmlinux-2.6.17.14-ubuntu1-mdv2
initrd.img-2.6.17-10-generic       vmlinuz-2.6.17-10-generic
initrd.img-2.6.17.14-ubuntu1-mdv2

Here is what my root looks like:

total 108
drwxrwxrwt  10 root root  4096 2007-03-15 13:57 tmp
drwxr-xr-x 104 root root  4096 2007-03-15 13:57 etc
lrwxrwxrwx   1 root root    38 2007-03-15 13:57 initrd.img -> boot/initrd.img-2.6.17.14-ubuntu1-mdv2
lrwxrwxrwx   1 root root    35 2007-03-15 13:57 vmlinux -> boot/vmlinux-2.6.17.14-ubuntu1-mdv2
drwxr-xr-x   3 root root  4096 2007-03-15 13:57 boot
drwxr-xr-x  12 root root 13520 2007-03-15 13:51 dev
drwxr-xr-x   4 root root  4096 2007-03-15 13:51 media
drwxr-xr-x   8 root root  4096 2007-03-15 13:18 root
drwxr-xr-x  11 root root     0 2007-03-15 09:08 sys
dr-xr-xr-x 103 root root     0 2007-03-15 09:08 proc
drwxr-xr-x   2 root root  4096 2007-03-15 08:51 sbin
drwxr-xr-x   3 root root  4096 2007-03-13 14:35 mnt
drwxr-xr-x  12 root root  4096 2007-03-13 13:20 usr
drwxr-xr-x   3 root root  4096 2007-03-13 12:27 home
drwxr-xr-x   2 root root  4096 2007-03-13 12:27 bin
drwxr-xr-x  17 root root  4096 2007-03-13 12:27 lib
drwxr-xr-x  15 root root  4096 2007-03-13 12:10 var
lrwxrwxrwx   1 root root    33 2007-03-13 10:26 initrd.img.old -> boot/initrd.img-2.6.17-10-generic
lrwxrwxrwx   1 root root    30 2007-03-13 10:26 vmlinuz -> boot/vmlinuz-2.6.17-10-generic
drwxr-xr-x   2 root root  4096 2007-03-13 10:12 initrd
drwxr-xr-x   2 root root  4096 2007-03-13 10:12 opt
drwxr-xr-x   2 root root  4096 2007-03-13 10:12 srv
lrwxrwxrwx   1 root root    11 2007-03-13 10:09 cdrom -> media/cdrom
drwxr-xr-x   2 root root 49152 2007-03-13 10:09 lost+found

I really don't have a clue as to how to proceed. Anybody have any ideas?

Many thanks,

-P.

---

### Post by zvacet on 2007-03-18
[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by noris2go on 2007-04-10
Hi,

Have you found your answer in the master kernel thread ?

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

I looked through all posts there and nothing I could see.

I'll tell you what worked for me (for 2.6.20 source on edgy):

UBUNTUBUILD=1 make-kpkg --initrd --bzimage --append-to-version=-1-custom -revision 2.6.20 kernel-image kernel-headers

UBUNTUBUILD define gets rid of the .3-Ubuntu1 automagically appended EXTRAVERSION defined in the Makefile. 

if you have a dual core CPU: 
export CONCURRENCY_LEVEL=2
would use both cores in the build

The linux-image-kdump does not have and does not install the vmlinuz compressed image although the build does make it. the build makes it here:
   /usr/src/linux/arch/<your arch here>/boot/bzImage
The only way to make it work was to copy+rename the compressed image manually into the /boot before running: 
  dpkg -i linux-image-kdump<your version>.deb
The install script then would not complain and would add all the grub entries.

I read a lot and I cannot figure from all the guides what sets this "kdump" target that I have a feeling is at fault here. Here are the guides I've been reading:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
[http://www.howtoforge.com/kernel_compilation_debian](http://www.howtoforge.com/kernel_compilation_debian)

None of them seem to have anything about this "kdump".
I hope someone can shine some light on this eventually.

---

