---
title: "Dual Boot problem Ubuntu (8.04)/XP"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by terklotron on 2008-05-25
Hey guys.

Now,here's a complete newbie Q.

I'm trying to dual Ubuntu and XP.
Problem is I can't boot XP from grub, but Ubuntu works just fine. Grub returns > Error 12 Invalid drive specification Now, if I change the boot priority from BIOS, windows loads flawlessly... but of cause no option to boot Ubuntu.

Menu.lst
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8cbf624-c330-49dd-919f-6d09df3e056e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f8cbf624-c330-49dd-919f-6d09df3e056e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

Can I provide more info? Plz help
thanx:)

---

### Post by louieb on 2008-05-25
Grub start numbering drives and partitions staring with zero. Sometimes it gets lost if the drives are a mix of ide and sata.  The grub installer thought XP is on the 3rd hard drive. Do you have 3 drives? 

Try this edit to your menu.lst and see if windows is on the 2nd drive. Basically just change hd2 to hd1 in your GRUB entry.  

```

title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

---

### Post by terklotron on 2008-05-26
Muahahahahahahaha, thank you so much.
I am now writing to you from IE :-) booted from grub.
You were right, just hd1 instead of hd2.
Great man, thanx

Peace

---

