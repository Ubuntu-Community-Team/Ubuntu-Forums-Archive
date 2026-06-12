---
title: "Grub problem after installing Ubuntu on same drive as Fedora"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by boersmaa on 2006-09-13
Hi,

I have 2 - 60gb drive in my computer.
in it I had on hda 
100mb boot grub
30gb Fedora FC5 with LVM
2.5gb swap

on hdb
I have windows XP.

I installed Ubuntu 6.06.
It created an extended partition to take the rest.
in the partition, it created a 
new boot grub
installed Ubuntu
and a swap part.

In this Grub it will only boot into Ubuntu and Windows.
It modified the disk information to boot from the Ubuntu partition only
Cannot boot in to Fedora anymore.
All my mail history is in Fedora.
Ubuntu will not mount the Fedora partition.

How do I get my mail data.

Here is my part info:

/dev/hda1   *           1          13      104391   93  Amoeba
/dev/hda2              14        4092    32764567+  8e  Linux LVM
/dev/hda3            9353        9729     3028252+  82  Linux swap / Solaris
/dev/hda4            4093        9352    42250950    f  W95 Ext'd (LBA)
/dev/hda5   *        4093        9134    40499833+  83  Linux
/dev/hda6   *        9135        9352     1751053+  82  Linux swap / Solaris

here is the grub menu.lst from Ubuntu.
title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Fedora Core 5
root            (hd0,1)
kernel          /vmlinuz-2.6.17-1.2174_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd          /vmlinuz-2.6.17-1.2174_FC5.img

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Here is the menu.lst from fedora
title Fedora Core (2.6.17-1.2174_FC5)
root (hd0,0)
kernel /vmlinuz-2.6.17-1.2174_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd /initrd-2.6.17-1.2174_FC5.img

when I enter Fedora the grub from Ubuntu gives me a filesystem error.
and I cannot get grub to boot from the original Fedora boot system.

Any Idea how to fix it so I can boot from both?

Thanks Andy

---

### Post by BoneKracker on 2006-09-14
change the ubuntu menu.lst to show your separate boot partition for fedora

(i.e. "(hd0,0)" instead of "(hd0.1)"

---

### Post by cotcot on 2006-09-14
The bootloader looks for hd(0,1) to find Fedora. Hd(0,1) is hda2 ; your LVM partition. I think it is not possible to boot from LVM. It should boot from the 100mB partition instead. 
Your mails are not lost. 
I suggest to search the menu.lst file from your fedora install (somewhere in the root directory of the LVM partition) and look there how fedora was bootet. Try to copy over the fedora section to the menu.lst made by ubuntu. Unmark the fedora section that was automatically made by ubuntu.
(Please take note of the fact that the ubuntu menu.lst has a section that is automatically made. It is marked with a comment. Please take some time to learn why it is there.)

---

### Post by BoneKracker on 2006-09-15
What's on (hd0,0)?  I was thinking maybe it was boot partition for the Fedora install.  If not, disregard.

By the way, the two linux installs can share the same swap space.

:)

---

### Post by boersmaa on 2006-09-15
I downloaded the alternate disk.
Deleted the ubuntu /dev/hda3
deleted grub /dev/hda1
Deleted swap /dev/hda4
re-installed Ubuntu, with grub on /dev/hda1
/ root and swap became /dev/hda4 and hda3

so now I can boot from outside Ubuntu.

Windows works, Ubuntu works

Added the following to menu.lst
title           Fedora Core 5
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-1.2174_FC5 ro root=/dev/hda2 rhgb quiet
kernel    /vmlinuz-2.6.17-1.2174_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd          /boot/initrd-2.6.17-1.2174_FC5.img
boot


How do I proprely reference the fedora partition on /dev/hda2 in menu.lst?

---

### Post by BoneKracker on 2006-09-18
Assuming, once again, that your hda2 is just the boot partition and the rest of Fedora is on a logical volume as referenced in the original menu.lst (if that's not true, most of what's below would not be valid).

1.  You've got an extra "kernel" line.
2.  Get rid of the "/boot" part of two lines in the Fedora section.  

**Explanation:** 
Grub starts working the kernel and initrd paths from what you've told it is the Grub root (i.e., "(hd0,1)" ).  So you don't need to tell it "/boot".  "/boot" only needs to be part of the path if your boot directory is inside your Linux root partition "/".

**Tip:**
If you don't want to have to remember that, you can put a symlink in your /boot partition that basically points to the directory itself.  
```
cd /boot
ln -s /boot ./

```
If you do that, it will work whether you mistakenly have "/boot" in the path or not.  


In summary, put it back to what it was originally:

title Fedora Core 5
root (hd0,1)
kernel /vmlinuz-2.6.17-1.2174_FC5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd /vmlinuz-2.6.17-1.2174_FC5.img

---

