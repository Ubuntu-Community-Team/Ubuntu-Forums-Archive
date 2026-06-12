---
title: "grub reinstalled but in shell mode, can't load ubuntu or windows"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by daudiam on 2010-05-20
I had Ubuntu **9.04**. But when I installed Windows also, the grub was overwritten. To reinstall the grub, I took a live cd of **9.10 **and typed the following
```
sudo mount /dev/sda8  /mnt 
sudo grub-install --root-directory=/mnt  /dev/sda

```
No error message came, but when I restarted my computer, it showed
```

GRUB 1.97~Beta4

sh:grub>
```

Perhaps its the command line mode of grub. I want a graphical mode so that I can easily boot either Windows or Ubuntu.

---

### Post by daudiam on 2010-05-23
Is there any way or should I just reinstall ?

---

### Post by wojox on 2010-05-23
What does this command tell us:

```
sudo fdisk -l
```

Try reinstalling it again like this:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

You may have left out a forward slash.

---

