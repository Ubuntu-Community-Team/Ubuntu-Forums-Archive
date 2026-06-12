---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by Loan_Refi on 2010-11-19
Hello, I need help fixing my grub2;

My problem error at startup;
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Today I installed Ubuntu 10.10 to a USB Drive using "UNetbooting" so that I can install Ubuntu 10.10 on my friends computer. I obviously made a mistake and somehow altered my own Grub2 by pointing the UUID to the USB Drive "I think". 

Using UNetbooting from; [http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)  I used Ubuntu 10.10 ISO and pointed to my USB Drive as /sdb and started to create the bootable USB.

I have 5 Kernels so to post this problem I logged into the 2nd kernel from the list, but if I try to use the 1st Kernel it fails to boot up and I get this Kernel Panic error message.


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done

:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Does anyone know what I need to do to fix Grub2 to be able to boot into my first kernle?

Your help is appreciated!
Thanks!

---

### Post by lmarmisa on 2010-11-19
Try to reinstall your first kernel using Synaptic.

Find a package named linux-image-2.6.32-26-generic and select Mark for reinstallation and Apply.

---

### Post by phillipdhall on 2010-11-28
I am also having this problem. I thought it was exclusively related to updating to the 32-26 kernel, since the 32-25 option boots fine. However I similarly created a unetbootin image on a USB drive while the update was downloading, so now I wonder.

Either way, I tried reinstalling the 32-26 packages with no improvement. I will continue browsing for answers. Thanks!

---

### Post by PavelMan on 2011-08-07
I have a 2.6.38 - same problem.
unknown-block(0,0) - does anybody know what it means?

---

