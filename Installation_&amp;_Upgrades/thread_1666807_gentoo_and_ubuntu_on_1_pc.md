---
title: "gentoo and ubuntu on 1 pc"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by ob.server on 2011-01-14
i have compiled kernel (manually) and one of my  hdd now contains gentoo installation an of type ext4. on another hdd  ubuntu is installed. grub2 is on hdd with ubuntu. when i sudo  update-grub2 i get message 
       >              Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.35-24-generic 
Found initrd image: /boot/initrd.img-2.6.35-24-generic 
... 
Found memtest86+ image: /boot/memtest86+.bin 
Found Gentoo Base System release 1.12.14 on /dev/sdb1 
done 
     
but no gentoo entry appears in menu. how to solve this?

---

### Post by dino99 on 2011-01-14
make a 40_custom entry

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

but when update grub it might found it by default. In a terminal, run:

sudo grub-mkconfig
sudo update-grub

note: is gentoo using grub2 ?

sometimes running a fsck on next boot can resolve some issues with grub:

sudo shutdown now -R

---

