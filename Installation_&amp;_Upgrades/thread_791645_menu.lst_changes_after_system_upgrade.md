---
title: "menu.lst changes after system upgrade"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by rodrigosprimo on 2008-05-12
Hi there, somethings I install Ubuntu in some friend machine with dual boot. The problem is that when this user update his Ubuntu system (with the update-manager or with apt-get upgrade) the process overwrite the file /boot/grub/menu.lst and erase the Windows boot entry.

I've seen this problem since Ubuntu 5.10 (when I've started using the distro). Is there a way to tell the system do add new entries to the file and not to overwrite it? Another way to solve this?

Thanks, Rodrigo.

---

### Post by Rallg on 2008-05-12
Read the menu.lst file. Where is the boot item for Windows? If it is contained within the "automagic kernels" section, each update to Grub will over-write it.

Be sure that the Windows boot item is before, or after, the "automagic kernels" section. You can edit menu.lst using

gksudo gedit /boot/grub/menu.lst

Let us know if that is the problem, or not.

---

### Post by bapoumba on 2008-05-12
> **Rallg said:**
> 
sudo gedit /boot/grub/menu.lst

Just a safe note:
```
gksudo gedit /boot/grub/menu.lst
```

---

