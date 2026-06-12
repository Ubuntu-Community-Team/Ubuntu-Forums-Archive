---
title: "Grub entry for Kernel Updates"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by ne0h on 2008-06-05
I have upgraded from Fiesty to Hardy couple of days back. After upgrade there were 3 times kernel got updated through automatic updates. My laptop have dual boot. So each time kernel got upgraded, it makes an entry to grub. Now my grub has all version entries - which looks cluttered. Are older versions are obsolete? Is it ok to remove them? If yes then how to remove?

[IMG]http://ubuntuforums.org/picture.php?albumid=231&pictureid=730[/IMG]

---

### Post by ilrudie on 2008-06-05
You can remove them from the grub list by editing /boot/grub/menu.lst and commenting out the stanzas that you don't want to appear in the boot menu.  This will leave the old kernels installed in case you later find that something requires and old kernel to work right.  Synaptic can be used to uninstall the old kernels if you don't want them on your system anymore.

To comment a line in the file add a '#' without the single quotes to the beginning of the line.  By stanza I mean the whole section of lines that are with the kernel.  Example stanza:

title           Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=9a3fe049-8288-5555-a21b-eb3a5bc7aeca ro single
initrd          /boot/initrd.img-2.6.24-18-generic


Hope that helps.

---

### Post by kpkeerthi on 2008-06-05
Search for **linux-image** in System -> Admin -> Synaptic. Choose the kernel versions you want uninstalled and mark them for uninstallation. Click Apply. GRUB will be auto-updated in the process.

---

### Post by Hooya on 2008-06-05
Amazing that someone asked this just four hours before I was going to.  I love this forum.

---

