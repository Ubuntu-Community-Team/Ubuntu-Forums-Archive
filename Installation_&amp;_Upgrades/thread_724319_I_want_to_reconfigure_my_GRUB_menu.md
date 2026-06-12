---
title: "I want to reconfigure my GRUB menu"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by werg on 2008-03-14
Hi, my GRUB menu is somewhat badly configured, as it doesn't list the OS installations I have in the order I would like it to. 

For primary Ubuntu installations, the format in which they are registered in the GRUB menu differs from that of secondary ones. For example, a primary installation is registered as such:


For example

title Ubuntu, kernel ...
root ...
kernel ...
initrd ...
quiet
savedefault
boot

title Ubuntu, kernel ... (recovery mode)
root ...
kernel ... ro single
initrd ...
boot

title Ubuntu, memtest86+
root ...
kernel /boot/memtest86+.bin
quiet
boot

While a secondary one is registered differently. How, then, do I retrieve the necessary information out of a secondary installation so that I can register it as a primary installation?

P.S.: the GRUB menu in question is in the said secondary installation.

Thank You

---

### Post by sandysandy on 2008-03-14
u can edit the menu.lst file .

code is >  gksudo gedit /boot/grub/menu.lst 

please take backup of menu.lst before attempting anything.

regards

---

### Post by Pumalite on 2008-03-14
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by werg on 2008-03-14
Okay, here is the content of my GRUB menu file.

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2dcf273a-aa96-4767-8b09-a33981e8d3d4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2dcf273a-aa96-4767-8b09-a33981e8d3d4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.

title		Ubuntu 7.10 (7.10) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 (7.10) (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

See how the primary installation has root located at UUID=2dcf273a-aa96-4767-8b09-a33981e8d3d4 while the secondary installation has the root located at /dev/sda5? I want to change that. How can I retrieve the necessary information about the installation on /dev/sda5?

---

### Post by Pumalite on 2008-03-14
At the Terminal:
blkid
(bad idea)

---

### Post by werg on 2008-03-14
Bad idea? Why?

---

### Post by Pumalite on 2008-03-14
Because that installation of yours (different that the other one, prefers itt the way it is. In my opinion is a better simpler way)

---

### Post by werg on 2008-03-14
Okay. One more question; it seems as though every time I boot from the installation on /dev/sda5, it gets 'mounted' instead of just regularly booting, as it would if it were the primary installation. Would you know how to change this?

---

