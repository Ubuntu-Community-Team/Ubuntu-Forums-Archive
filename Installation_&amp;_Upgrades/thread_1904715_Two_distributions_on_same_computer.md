---
title: "Two distributions on same computer"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by Warlon on 2012-01-05
I'm planning on installing ubuntu server edition and linux mint debian on my laptop and I was wondering will there be problems with grub menu because of this? I mean, will kernel updates erase the other distro from the menu?

---

### Post by KdotJ on 2012-01-05
No at all, its perfectly common to have multiple Linux distros installed on one machine. New kernel updates will just be added to the grub menu.

---

### Post by oldfred on 2012-01-05
Grub will update, but you have to manage it.

Only one grub in the MBR will be the default and the one you have as your main install ( or second install if you do not specify otherwise). You have to run the sudo update-grub in the first install to get it's menu updated, so the os-prober in the second/main install on a sudo update grub finds the new kernel entries in both installs.

I have several installs and with multiple kernels it started to get confusing. I turned off the os-prober and added a custom entry to 40_custom to boot the partition which boots the newest kernel. Ubuntu always puts a updated link in / (root) to the newest kernel on updates. Other distributions may not.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. (He called it daily as it was his testing version of the next release which was having a lot of kernel updates, you can call it anything.)

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by ottosykora on 2012-01-05
yes something like that I have on an install with w7, xp, w98se, ubuntu, debian, fedora.

I am using in that case a separate small partition for the main grub, the one starting in MBR. In this partition, the grub points then to the different partitions containing the operating systems, but this partition will never be updated as there are no exact kernels specified there, just set root etc. as generic pointers.


This makes the whole setup independent of any kernel updates in the partitions, there is in each an other copy of grub (linux) and this get updated on install of new kernel by the installer under normal condition. 
This way I do not need to take care of any grub updates myself, the menu of the grub loaders in the PBR are set to short time, so they do not bother me to much.

---

