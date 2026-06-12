---
title: "Install New Custom Kernel"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by thahir1986 on 2010-01-09
Hi friends,

I am new to this forum and ubuntu too...so i'm not sure this is correct catagery to post my new thread.

I am trying to install new custom kernel with rtai patch on my Ubuntu 9.04 Os.

I' following below link to compile new kernel.

[http://qrtailab.sourceforge.net/rtai_installation.html](http://qrtailab.sourceforge.net/rtai_installation.html)

I got error while install the kernel image..:(  .i dont know y....? Please help me....

root@system3:/usr/src# dpkg -i linux-image-2.6.28.7-rtai_2.6.28.7-rtai-10.00.Custom_i386.deb 
(Reading database ... 353751 files and directories currently installed.)
Preparing to replace linux-image-2.6.28.7-rtai 2.6.28.7-rtai-10.00.Custom (using linux-image-2.6.28.7-rtai_2.6.28.7-rtai-10.00.Custom_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.28.7-rtai ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28.7-rtai
Found kernel: /vmlinuz-2.6.28-14-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.28.7-rtai (2.6.28.7-rtai-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28.7-rtai-10.00.Custom was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28.7-rtai-10.00.Custom was configured last, according to dpkg)
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28.7-rtai
Found kernel: /vmlinuz-2.6.28-14-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28.7-rtai.postinst line 1186.
dpkg: error processing linux-image-2.6.28.7-rtai (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28.7-rtai


Thanks in advance.....

---

### Post by thahir1986 on 2010-01-10
Please any one reply me regarding the issue

---

### Post by Malta paul on 2010-01-10
If you want to change you Kernel there are .deb versions available from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Be careful you may lose your graphics, you can go back to the generic drive before you reboot,but you may have to install your graphic driver in the boot-up terminal mode.

---

### Post by geoffjay on 2010-03-15
Did you ever find a solution to this problem? I'm getting the same error using 9.04 and a 32bit kernel compiled for the AMD64/Opteron architecture.

---

### Post by geoffjay on 2010-03-15
I just found out what my problem was, I had already installed the nvidia driver and the installation was failing while reading /etc/kernel/postinst.d/nvidia-common so I moved it out of the way and it installed correctly.

---

### Post by thahir1986 on 2010-06-19
Thanks Jay, sorry for the the late reply.

---

