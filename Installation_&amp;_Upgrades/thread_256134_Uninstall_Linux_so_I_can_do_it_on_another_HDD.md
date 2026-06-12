---
title: "Uninstall Linux so I can do it on another HDD"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Vehendi on 2006-09-12
Hi,

I'd like to uninstall Ubuntu from my current hard disk (dual boot with Windows XP), so I can install it on another HDD.

What do I need to do?

Delete all partitions? Reformat?

Thank you in advance,

Vehendi.

---

### Post by Irony on 2006-09-12
If you mean you want to install a second HDD on your machine and have XP on the first drive and Ubuntu on the other then the best thing to do is;

[PHP]sudo mkfs.ext3 /dev/hdb2
sudo mkdir /mnt/hda3_Ubuntu
sudo mkdir /mnt/hdb2_Ubuntu
sudo mount /dev/hda3 /mnt/hda3_Ubuntu
sudo mount /dev/hdb2 /mnt/hdb2_Ubuntu
sudo cp -ax /mnt/hda3_Ubuntu/. /mnt/hdb2_Ubuntu/.[/PHP]

And then alter you /etc/fstab file. In other words copy your current installation over to the second HDD.

You'd do this with the Live CD. You'd also have to reinstall Grub to point at the /boot/grub/menu.lst in hdb2 - note these partitions are just examples.

Once you've confirmed that it works, you can then simply delete the original partition (for example from XP).

---

### Post by confused57 on 2006-09-12
Here's an excellent guide to uninstalling Ubuntu:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

