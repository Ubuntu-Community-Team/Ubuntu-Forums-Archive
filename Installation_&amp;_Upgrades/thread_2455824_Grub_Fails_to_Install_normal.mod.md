---
title: "Grub Fails to Install normal.mod"
date: 2020-12-28
forum: Installation &amp; Upgrades
---

### Post by mstarks01 on 2020-12-28
Hello everyone. I'm putting together an Ubuntu Base 20.04 installation and everything is going well expect for the installation of the boot loader. Although everything appears to succeed, it fails to create/link normal.mod in /boot/grub/i386-pc, resulting in a failure to boot. Here are the basic steps I have taken.

1. Boot to Ubuntu live CD
2. Download Ubuntu Base3. Use gparted to create and format two filesystems:
  - /boot, ext4, 500MB, set flag to bootable
  - OS, ext4, remaining size
4. Mount newly created paritions and create filesystem:
  - sudo su -
  - mkdir /mnt/base
  - mount /dev/sda2 /mnt/base
  - tar xvzf /home/ubuntu/Downloads/ubuntu* -C /mnt/base
  - mount /dev/sda1 /mnt/base/boot  
5 Copy over resolv.conf
  - cp /etc/resolv.conf /mnt/base/etc
6 Bind mount and chroot
 - for i in /sys /proc /dev; do mount --rbind $i /mnt/base/$i; done && chroot /mnt/base
7. Install stuff (this also brings grub down as a dependency  - apt update
  - apt install linux-{headers,image}-azure (or whatever kernel is needed) 
8. Install the bootloader
 - grub-install --boot-directory=/boot /dev/sda
I've also tried just:
 - grub-install /dev/sda
And then..
update-grub

The directory structure gets created in /boot, but the only place normal.mod exists is /usr/lib/grub/i386-pc. I suppose I could just link or copy it to /boot/grub/i386-pc, but this seems like it shouldn't be necessary.

---

### Post by dino99 on 2020-12-29
Why don't you let the installer (ubiquity) doing its stuff itself ?  Your own way may break the rules  :o

---

### Post by mstarks01 on 2020-12-29
> **dino99 said:**
> Why don't you let the installer (ubiquity) doing its stuff itself ?  Your own way may break the rules  :o

Ubuntu Base has no installer. It's the most minimal version of Ubuntu able to install other packages, and contains only userland stuff--no kernel or bootloader. It's meant for purpose-built appliances and such.

---

### Post by dino99 on 2020-12-30
Howto:

[https://askubuntu.com/questions/1260465/how-to-install-ubuntu-base](https://askubuntu.com/questions/1260465/how-to-install-ubuntu-base)
[https://wiki.ubuntu.com/Base/InstallationExample](https://wiki.ubuntu.com/Base/InstallationExample)

---

### Post by mstarks01 on 2020-12-30
> **dino99 said:**
> Howto:

[https://askubuntu.com/questions/1260465/how-to-install-ubuntu-base](https://askubuntu.com/questions/1260465/how-to-install-ubuntu-base)
[https://wiki.ubuntu.com/Base/InstallationExample](https://wiki.ubuntu.com/Base/InstallationExample)

Thanks for sharing those. I do appreciate your offer of help, but there are issues with them.

The first one doesn't address the bootloader issue at all.
The second has errors and is problematic in other ways. For example, it has you chroot to /mnt/root and install the kernel there, but that will completely miss the boot partition that was previously mounted. Later it has you copy them over, but that's an extra and unneeded step if you mount boot over the root mount point. As to dependencies, I found that there were several dozen dependencies of the kernel to recursively download, many of which are already satisfied, so it makes much more sense to bind mount like I have done above and run apt inside the chroot. Thirdly, it installs syslinux while I am trying to use grub.

---

### Post by #&amp;thj^% on 2020-12-30
Perhaps change to your licking: [https://askubuntu.com/questions/1290075/xubuntu-20-04-minimal-installation](https://askubuntu.com/questions/1290075/xubuntu-20-04-minimal-installation)

---

