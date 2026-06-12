---
title: "Grub problem"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by pnikkos on 2008-05-11
Hi,

i have a problem with my new ubuntu 8,04 installation.

I have 2 disks in my computer.

The first has 4 partitions:
   1) linux swap
   2) ext3  (ubuntu)
   3) ntfs  (windows)
   4) fat32 (data)

The second has only one partition that is fat32.

I installed windows first in the 3rd partition, and then i installed ubuntu
in the second (and first for the swap).

When i installed ubuntu, grub menu didn't appear at the boot.

Then i run the ubuntu live cd and i run these commands in a terminal:

    sudo grub

    > root (hd1,1)

    > setup (hd1)

    > exit

Now the grub menu appears when i boot but neither ubuntu nor windows are starting. And shows a message like "this partition does not exist".


Nut if i don't leave the computer to boot normally and choose to boot from the first hard drive (that is the same thing) then the computer apperas egain the grub menu and now both the windows and the ubuntu starts normally.


Do you have any idea, what's going wrong?



Here is my /boot/grub/menu.lst file:


title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0fee0616-0a47-4998-9a3f-f7ce7ebda9cf ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0fee0616-0a47-4998-9a3f-f7ce7ebda9cf ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb4
title		Windows NT/2000/XP (loader)
root		(hd1,3)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Rallg on 2008-05-11
Try this: Edit the Grub menu.lst so that it refers to hd0 rather than to hd1. So, (hd1,1) would be changed to (hd0,1) and so forth.

That won't hurt if it is wrong, and it might help. If you don't want to edit menu.lst, I believe you can temporarily edit the Grub choices when the list appears in Grub.

---

### Post by pnikkos on 2008-05-11
I tried this but don;t make any difference.

Also, i noticed something else.

In the grub boot screen i choose to start windows xp. It shows me the message "Error 22: No such partition" and returns me to the grub boot screen again. Then i choose ubuntu and shows the exact message and returns me to the grub boot screen again.. Now if i choose again ubuntu i logon normally.

That isn't work with windows.


Do you have any idea?

Thanks anyway

---

### Post by Rallg on 2008-05-11
Ideas, yes. Good advice, maybe or maybe not.

It sounds as if you have Grub installed in more than one place (this is possible, I have it myself). Perhaps the MBR points to one installation of Grub, which in turn points to a different installation of Grub, with incompatible menus? In my own case, only one of the multiple copies of Grub is functional. I don't know how it could be different; but you asked for ideas.

Also have a look at this thread, where the reliable Pumalite provides a link:
[http://ubuntuforums.org/showthread.php?t=790396](http://ubuntuforums.org/showthread.php?t=790396)

---

