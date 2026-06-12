---
title: "Ubuntu 7.10 and Windows Vista"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Eider on 2007-12-17
Today I have installed Ubuntu 7.10 on my Dell computer.
Everything works fine. There's only one problem.


If I select Windows Vista in Grub, my computer restarts and I come back in Grub. I can't go Vista. 

What can I do in order to make the bootloader work?

This is my grub.list:

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d8bccf72-17d7-43f9-8ee6-75dc197dc31f ro quiet splash locale=nl_NL
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=d8bccf72-17d7-43f9-8ee6-75dc197dc31f ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1

My partitions:
sda 1: Dell Utility
sda 2: Ubuntu Linux
sda 3: Windows Vista Home Premium
sda 4: Linux swap

---

### Post by Topsiho on 2007-12-17
I am not sure as I do not use Windows (lucky me), and have never had Vista on my computer (it won't even run with Vista I suppose).
I answer for when I had Windows, it *always* sat in hd0,0 (grub language).
According to your menu.lst hd0,0 (usually called hda1, or sda1) contains Dell Utilities, while Vista sits in sda3, which indeed is hd0,2 in grub parlance.

Also: somewhere up there in this menu.lst an example is given how the entry should look like for windows. You can check with this example whether the entry in your list is OK.

Topsiho

---

### Post by Pumalite on 2007-12-17
Post:
sudo fdisk -lu

---

### Post by Eider on 2007-12-18
I have already solved the problem.

I have used "Repair" on the Vista DVD. Now it works :).

---

