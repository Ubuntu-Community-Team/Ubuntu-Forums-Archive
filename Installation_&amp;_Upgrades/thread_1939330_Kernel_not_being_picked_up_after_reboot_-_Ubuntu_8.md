---
title: "Kernel not being picked up after reboot - Ubuntu 8.10"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by anirvana on 2012-03-11
Hello all,
  I am trying to update the kernel on a VPS I inherited. The system runs Ubuntu 8.10, and we cannot upgrade the entire distro. (for certain reasons), hence we are trying to upgrade at least the kernel.

This is what I did :
- download the linux headers and images for a newer kernel
- install using dpkg -i 
- reboot the server

The problem:
- system does not boot with new kernel
- I cannot locate any grub/lilo config files! so that I can try to modify them and force boot with new kernel

What I need:
- Any advice/pointers about what am I doing wrong, or any suggestions about how to locate bootloader and modify it will be great!

Commands I ran:
```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-natty/linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb
sudo dpkg -i linux-headers-2.6.38-020638_2.6.38-020638.201103151303_all.deb
sudo dpkg -i linux-headers-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb
wget http://mirror.anl.gov/pub/ubuntu//pool/main/w/wireless-crda/wireless-crda_1.12_amd64.deb
sudo dpkg -i wireless-crda_1.12_amd64.deb
(the first time round it complained about this wireless-crda package so I installed it and redid the process)
sudo dpkg -i linux-image-2.6.38-020638-generic_2.6.38-020638.201103151303_amd64.deb
sudo reboot

```

What I see after reboot:
- kernel 2.6.24 is in use
- when I look in /boot/ I can see the 2.6.38 kernel present, same for when I use dpkg --list | grep linux-images, I see the new kernel
- there is no /boot/grub/menu.lst file
- there is /sbin/grub install in the system
```

$whereis grub
grub: /usr/sbin/grub /etc/grub.d /usr/lib/grub /usr/share/man/man8/grub.8.gz

```

I used the steps I listed below on another local virtual machine that I installed from a 8.10 CD and followed the steps. Kernel got upgraded easily, no problems. So the process works! However, it did not work on the vps.

Any insight is very appreciated.

---

