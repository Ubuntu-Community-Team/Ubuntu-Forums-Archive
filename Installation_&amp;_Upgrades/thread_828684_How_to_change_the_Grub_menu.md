---
title: "How to change the Grub menu?"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by -Outcast- on 2008-06-14
Hey folks

I have dual boot with Vista and Hardy. How can I change the text of Grub when it appears?

I want to rename Windows Vista to Say 'Other'

---

### Post by iaculallad on 2008-06-14
> **-Outcast- said:**
> Hey folks

I have dual boot with Vista and Hardy. How can I change the text of Grub when it appears?

I want to rename Windows Vista to Say 'Other'

Create a backup of your menu.lst file first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original 
```

Open the file for editing:

```
gksudo gedit /boot/grub/menu.lst
```

When your menu.lst file opens, edit your "Title" windoze name and rename it with "Others". Save it and do reboot to see the output.

---

