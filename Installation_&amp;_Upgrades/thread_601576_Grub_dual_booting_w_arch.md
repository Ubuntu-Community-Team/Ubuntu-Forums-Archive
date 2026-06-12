---
title: "Grub dual booting w/ arch"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by fatalfurry on 2007-11-03
I just installed ubuntu 7.10 and grub didnt find my arch install on a different hdd. Right now i moved the arch kernel and the vmlinuz files to the ubuntu /boot partition. I have added the arch  menu.list entry like so

> 

# (0) Arch Linux
title  Arch Linux
root   (hd2,1)
kernel /vmlinuz26 root=/dev/sda1 ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd2,1)
kernel /vmlinuz26 root=/dev/sda1 ro
initrd /kernel26-fallback.img



it starts to boot into arch but gives a kernel panic.
How do I dual boot these 2 distros?

---

### Post by meierfra on 2007-11-03
Grub starts counting at zero. So (hd2,1) refers to the second partition on your third hard drive. root (hdx,y) needs to  be the location of  /vmlinuz26

---

### Post by zvacet on 2007-11-03
[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

---

