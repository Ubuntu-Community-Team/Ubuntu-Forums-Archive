---
title: "Ubuntu 14.04 nvidia driver 340 not correctly supported"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2014-09-14
Hi,

I recently installed cuda 6.5 development kit and it comes with nvidia driver 340. Unfortunately, it seems that Ubuntu 14.04 64 bit has some problems with those drivers. I tried with latest kernel available from standard repository (3.13.0-35) and with latest kernel available from package (3.16.2 utopic) in ubuntu kernel mainline [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=M;O=D). The driver are also available via PPA org-edgers/ppa. During the installation of the kernel the system is unable to correctly add some module. The exact error is reported below.
```

Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Error! Bad return status for module build on kernel: 3.13.0-35-generic (x86_64)
Consult /var/lib/dkms/nvidia-340-uvm/340.32/build/make.log for more information.

```
However, the file /var/lib/dkms/nvidia-340-uvm/340.32/build/make.log is empty.
What can I do?
Thank you

---

### Post by Vladlenin5000 on 2014-09-14
It's not clear exactly how you finally installed the 340 drivers. The source and method might give us a clue about what's happening.

---

### Post by erotavlas on 2014-09-15
I installed cuda with the following commands:
 sudo dpkg -i cuda-repo-ubuntu1404_6.5-14_amd64.deb
sudo apt-get install cuda-runtime-6-5 cuda-6-5 cuda-command-line-tools-6-5 cuda-cublas-6-5 cuda-cublas-dev-6-5 cuda-cudart-6-5 cuda-cudart-dev-6-5 cuda-cufft-6-5 cuda-cufft-dev-6-5 cuda-core-6-5 cuda-curand-6-5 cuda-curand-dev-6-5 cuda-cusparse-6-5 cuda-cusparse-dev-6-5 cuda-documentation-6-5 cuda-driver-dev-6-5 cuda-drivers cuda-npp-6-5 cuda-npp-dev-6-5 cuda-repo-ubuntu1404 cuda-toolkit-6-5 cuda-visual-tools-6-5 
Then the updating process installed also nvidia-driver-340. Now if I tried to update kernel I get the following result.
```

sudo apt-get install linux-headers-generic-lts-trusty linux-image-generic-lts-trusty 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.13.0-35-generic linux-headers-generic
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-35-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed
  linux-headers-3.13.0-35-generic linux-headers-generic
  linux-headers-generic-lts-trusty linux-image-3.13.0-35-generic
  linux-image-extra-3.13.0-35-generic linux-image-generic
  linux-image-generic-lts-trusty
0 to upgrade, 7 to newly install, 0 to remove and 0 not to upgrade.
Need to get 5,900 B/52.6 MB of archives.
After this operation, 207 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic-lts-trusty amd64 3.13.0.35.42 [1,782 B]
Get:2 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic amd64 3.13.0.35.42 [2,336 B]
Get:3 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic-lts-trusty amd64 3.13.0.35.42 [1,782 B]
Fetched 5,900 B in 0s (15.1 kB/s)                           
Selecting previously unselected package linux-image-3.13.0-35-generic. (Reading database ... 418461 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-35-generic_3.13.0-35.62_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-35-generic (3.13.0-35.62) ... 
Selecting previously unselected package linux-headers-3.13.0-35-generic.
Preparing to unpack .../linux-headers-3.13.0-35-generic_3.13.0-35.62_amd64.deb ...
Unpacking linux-headers-3.13.0-35-generic (3.13.0-35.62) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_3.13.0.35.42_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.35.42) ...
Selecting previously unselected package linux-headers-generic-lts-trusty.
Preparing to unpack .../linux-headers-generic-lts-trusty_3.13.0.35.42_amd64.deb ...
Unpacking linux-headers-generic-lts-trusty (3.13.0.35.42) ...
Selecting previously unselected package linux-image-extra-3.13.0-35-generic.
Preparing to unpack .../linux-image-extra-3.13.0-35-generic_3.13.0-35.62_amd64.deb ...
Unpacking linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_3.13.0.35.42_amd64.deb ...
Unpacking linux-image-generic (3.13.0.35.42) ...
Selecting previously unselected package linux-image-generic-lts-trusty.
Preparing to unpack .../linux-image-generic-lts-trusty_3.13.0.35.42_amd64.deb ...
Unpacking linux-image-generic-lts-trusty (3.13.0.35.42) ...
Setting up linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-35.62 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-35.62 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Error! Bad return status for module build on kernel: 3.13.0-35-generic (x86_64) ////////// error
Consult /var/lib/dkms/nvidia-340-uvm/340.32/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.2-031602-generic
Found initrd image: /boot/initrd.img-3.16.2-031602-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-headers-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Setting up linux-headers-generic (3.13.0.35.42) ...
Setting up linux-headers-generic-lts-trusty (3.13.0.35.42) ...
Setting up linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-35.62 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-35.62 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.2-031602-generic
Found initrd image: /boot/initrd.img-3.16.2-031602-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (3.13.0.35.42) ...
Setting up linux-image-generic-lts-trusty (3.13.0.35.42) ...

```
The file /var/lib/dkms/nvidia-340-uvm/340.32/build/make.log is empty...

---

### Post by oldfred on 2014-09-15
I only install from repository.
But if you install from nVidia or a .deb you have to make sure it it integrated into every kernel you install.
see 
man dkms
       dkms status

 If from ppa or nVidia you may need to manually make new initramfs.
 man mkinitramfs

One user posted this with a much old version:
 To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernel module gets updated automatically when a new kernel is installed. and does not need to be manually re-installed.

Often better to use repository, or if you must have newest use ppa.
      
 Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)

 Running The Oibaf PPA On Ubuntu 14.10
[http://www.phoronix.com/scan.php?page=news_item&px=MTc4NTk](http://www.phoronix.com/scan.php?page=news_item&px=MTc4NTk)

---

### Post by obocheng on 2014-09-16
I am not a English speaker...
I install nvidia drivers 340.32 on Ubuntu 14.04
Here:[https://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidiadriver/451248#451248?newreg=fcbc77b021554abb999af3083e49ac99href](https://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidiadriver/451248#451248?newreg=fcbc77b021554abb999af3083e49ac99href)
the second answer helped me a lot
and it works well
maybe it can help you :)

But after I use command:sudo apt-get dist-upgrade
I reboot my computer then system shows low graphics and the desktop disappered, just left wallpaper
I have tryed to reinstall nvidia drivers,but errors.
Now,I have no idea...

---

