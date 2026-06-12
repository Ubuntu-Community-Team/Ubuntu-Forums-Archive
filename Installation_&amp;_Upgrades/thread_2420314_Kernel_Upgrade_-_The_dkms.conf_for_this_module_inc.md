---
title: "Kernel Upgrade - The dkms.conf for this module includes a BUILD_EXCLUSIVE directive w"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by sethu47 on 2019-06-03
I was trying to upgrade my Ubuntu Kernel from 4.4.0 to 5.0.0

Here is my current System info
#

Ubuntu 18.04.2 LTS

sanal@MyThink:~/APPS/Kernel-5$ uname -a
Linux MyThink 4.4.0-145-generic #171-Ubuntu SMP Tue Mar 26 12:43:40 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
sanal@MyThink:~/APPS/Kernel-5$ 

#

---------------------

Here is the packages I downloaded from ubuntu official site

sanal@MyThink:~/APPS/Kernel-5$ ls -l
total 65216
-rw-r--r-- 1 sanal sanal 10638288 Mar  4 07:02 linux-headers-5.0.0-050000_5.0.0-050000.201903032031_all.deb
-rw-r--r-- 1 sanal sanal  1142340 Mar  4 07:13 linux-headers-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
-rw-r--r-- 1 sanal sanal  8312764 Mar  4 07:12 linux-image-unsigned-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
-rw-r--r-- 1 sanal sanal 46674464 Mar  4 07:12 linux-modules-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
sanal@MyThink:~/APPS/Kernel-5$ 



----------------------------

Here is the error I'm receiving 


sanal@MyThink:~/APPS/Kernel-5$ sudo dpkg -i linux-modules-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb
(Reading database ... 348989 files and directories currently installed.)
Preparing to unpack linux-modules-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb ...
Unpacking linux-modules-5.0.0-050000-generic (5.0.0-050000.201903032031) over (5.0.0-050000.201903032031) ...
Setting up linux-modules-5.0.0-050000-generic (5.0.0-050000.201903032031) ...
Processing triggers for linux-image-unsigned-5.0.0-050000-generic (5.0.0-050000.201903032031) ...
/etc/kernel/postinst.d/dkms:
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.0.0-050000-generic
W: initramfs-tools configuration sets RESUME=UUID=92c73a56-3dd4-45e0-a67b-a50b601c608a
W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=6fd29ae4-f8bd-49d1-b4a4-68f3accdede5)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.0.0-050000-generic
Found initrd image: /boot/initrd.img-5.0.0-050000-generic
Found linux image: /boot/vmlinuz-4.4.0-145-generic
Found initrd image: /boot/initrd.img-4.4.0-145-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
sanal@MyThink:~/APPS/Kernel-5$

-----------------------------------------------

Kernel Download link - [https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0/linux-modules-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.0/linux-modules-5.0.0-050000-generic_5.0.0-050000.201903032031_amd64.deb)

This failure is causing my VirtualBox to get failed. Because of Module not found.
"[TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] [FONT=monospace]NS_ERROR_FAILURE (0x80004005)[/FONT]
[/TD]
[/TR]
[/TABLE]
"


Please help me.

---

### Post by dino99 on 2019-06-03
Downlaod from: [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by jeremy31 on 2019-06-03
The virtualbox dkms packages from the repo are likely to have issues with the 5.0 kernels and fail to build.  I am not sure how you are using a 4.4 kernel with 18.04 as it uses 4.15 kernels with 18.04.2 might use 4.18

---

### Post by sethu47 on 2019-06-05
I tried installing 4.15 - but issue persists. When I go with 4.18, it works but my whole OS seems to be hung a while after loggedin. I really dont want to have a fresh ubuntu installation on my laptop. Its running ubuntu since 10.04 - almost 9 years. 

Please suggest me some, so i can try on my box without breaking any.

-sm

---

### Post by sethu47 on 2019-06-05
ok.. here the try, I booted to 4.4.0-145. But, I'm not able to locate headder module for current kernel. It seems to be a bug in VirtualBox, but I tried their fix to use 6.0 new release. Issue still persists.


root@MyThink:~# uname -r
4.4.0-145-generic
root@MyThink:~# 
root@MyThink:~# /sbin/vboxconfig
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
This system is currently not set up to build kernel modules.
Please install the Linux kernel "header" files matching the current kernel
for adding new hardware support to the system.
The distribution packages containing the headers are probably:
    linux-headers-generic linux-headers-4.4.0-145-generic
This system is currently not set up to build kernel modules.
Please install the Linux kernel "header" files matching the current kernel
for adding new hardware support to the system.
The distribution packages containing the headers are probably:
    linux-headers-generic linux-headers-4.4.0-145-generic


There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.  If your system is using EFI Secure Boot you may need to sign the
kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load
 them. Please see your Linux system's documentation for more information.
root@MyThink:~#

---

### Post by jeremy31 on 2019-06-08
Does it work after ```
sudo apt install linux-headers-$(uname -r)
```

---

### Post by sethu47 on 2019-06-11
root@MyThink:~# sudo apt install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-4.4.0-145-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-4.4.0-145-generic' has no installation candidate
root@MyThink:~#

---

### Post by sethu47 on 2019-06-11
sudo sed -i 's/bionic/disco/g' /etc/apt/sources.list Then we need to disable third-party repositories (PPAs) with the command below.
 sudo sed -i 's/^/#/' /etc/apt/sources.list.d/*.list After you disable third-party repositories, run the following  commands to update software sources and upgrade software to the latest  version available in the Ubuntu 19.04 repository. This step is called  minimal upgrade.
 sudo apt update

sudo apt upgrade Once minimal upgrade is finished, run the following command to begin full upgrade.
 sudo apt dist-upgrade


[https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-18-04-to-ubuntu-19-04-directly-from-command-line](https://www.linuxbabe.com/ubuntu/upgrade-ubuntu-18-04-to-ubuntu-19-04-directly-from-command-line)

---

