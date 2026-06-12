---
title: "Turning off ACPI in 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by itsmoonsoo on 2009-11-15
How do I edit the new Grub2 kernel to turn ACPI off.  I know how to do it with the old grub by editing menu.lst, but with the new install of koala, menu.lst no longer exists.  Anyone know how to do this?

Thanks!

---

### Post by ajgreeny on 2009-11-15
I'm sure there must be a way to do it with the new and various configuration files in /etc/grub.d.  In fact looking at the files and reading the wiki and other forum threads about grub2, I think you need to edit the file 40_custom and add an entry to it in this form with whatever you added to the kernel line put there.  I have shown [COLOR=Red]acpi=off[/COLOR] as an example.  Don't just copy the entry I show as that relates to my system and UUIDs etc will all be for my system only.
```
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic"{
set root=(hd0,2)
linux/boot/vmlinuz-2.6.28-15-generic root=UUID=10ec6342-7b3f-425c-8655-c637bb65ae72 ro quiet splash [COLOR=Red]acpi=off[/COLOR]
initrd        /boot/initrd.img-2.6.28-15-generic
}
```and then rename the file with another number (06_custom, I think) and make it executable.  Now it will run after the 05_debian_theme file and put the first entry at the top of the menu displayed.  Other linux OS entries can be added to the file as well, I believe, as long as you keep the format of each OS entry the same as that shown.

---

