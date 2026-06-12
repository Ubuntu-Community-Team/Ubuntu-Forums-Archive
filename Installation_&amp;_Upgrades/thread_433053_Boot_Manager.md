---
title: "Boot Manager"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by davecochran19 on 2007-05-04
I have used a dual boot in the past with different versions of windows. I want to learn Linux so I downloaded and installed Ubuntu. Ubuntu comes first on the boot manager. You have to manually select XP. Is there a way to swap this order? My wife gets mad when she forgets and....well you know lol....
There may be a different boot manager. Any help would be greatly appreciated. Remember I know little about Linux but very willing to try.

---

### Post by Tomosaur on 2007-05-04
> **davecochran19 said:**
> I have used a dual boot in the past with different versions of windows. I want to learn Linux so I downloaded and installed Ubuntu. Ubuntu comes first on the boot manager. You have to manually select XP. Is there a way to swap this order? My wife gets mad when she forgets and....well you know lol....
There may be a different boot manager. Any help would be greatly appreciated. Remember I know little about Linux but very willing to try.

Yup, all you have to do is change which OS boots by default. Hit alt+f2, then type:

```

gksudo gedit /boot/grub/menu.lst

```

then input your password (the one you use to log on). This will open the text editor, gedit, with the file which controls grub (the boot manager).

Now, you need to know what is actually in the boot menu. Grub counts from zero, so the first item in the list is 0, second is 1, etc etc. If you hit ctrl+, and type 'default' in the search box (then click ok), you should see a line in the file which says 'default 0'. Change the 0 to whatever number Windows is in the list. For example, if you have 4 items in the boot menu, then Windows would be number 3 (since it's usually the last item in the list). Be careful, because the 'Other Operating Systems:' line IS included in the count. Once you're done, just save the file. Next time you reboot, if you leave grub alone, it should boot into XP.

Alternatively, check the link in my sig for a graphical method to do this.

---

### Post by davidgarcin on 2007-05-04
to change the GRUB bootloader sequence and defaults, you have to edit /boot/grub/menu.lst with this command:

```
sudo gedit /boot/grub/menu.lst
```

At the bottom of this file, you will see different entries for your operating systems.  The order they are in is the order they appear in the menu.  In your case, I suggest setting Windows as the default.  To do this, find the line in the file that says "default 0", and change the 0 to the number of the Windows entry.  For example, your menu.lst may look something like mine:

```
title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=4584a97e-4b52-403a-a1d0-510e2b44af35 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=4584a97e-4b52-403a-a1d0-510e2b44af35 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

## This entry automatically added by the Debian installer for a non-linux OS
## on /dev/sda3
title           Windows Vista
rootnoverify    (hd0,0)
makeactive
chainloader     +1

```

In my case, to set Vista as the default, I would have the line as "default 4".  To set Ubuntu to the default, I have the line default 0.  Remember that any separators you have in the list also count as entries.

---

### Post by davidgarcin on 2007-05-04
heh.... well, this post *was* unanswered when I started....

---

### Post by anatole on 2007-05-04
you have to edit your /boot/grub/menu.lst ; by default, there is a section in the beginning with the caption "default num", the commented text in the file sums it all up pretty well, you have to define which boot entry should be selected by default, note that the count starts with 0, so if you have five entries, like ubuntu, ubuntu recovery mode, memtest, separator and windows, then number 4 should be windows. i'd suggest you read the comment fields of menu.lst, a lot of improvements can be made quite easily to grub, making it a lot more comfortable. just be careful ;)

Edit: haha, took me too long to respond

---

