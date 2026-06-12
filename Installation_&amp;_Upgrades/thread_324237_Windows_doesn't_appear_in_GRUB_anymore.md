---
title: "Windows doesn't appear in GRUB anymore"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Bosonator on 2006-12-23
I recently installed 64-bit Kubuntu (Edgy) on my laptop, leaving room for a Windows installation as well. After installing Windows, I had to boot from the Live CD and reinstall grub. My Kubuntu is on hda2 and my Windows is on hda1, so I entered the following:
```

sudo grub
grub> root (hd0,1)
grub> setup (hd0)

```
Which, as I understand it, should install GRUB to the master boot record (MBR). Unfortunately, when GRUB runs now, Ubuntu is the only OS it sees. Can anyone tell me how to alert Grub that Windows is still there? Thankx!

---

### Post by gbesso on 2006-12-23
Note: You might want to backup menu.lst first :)
Run ```
kdesu kate /boot/grub/menu.lst
```
and add this at the bottom: 
```

title        Windows
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

