---
title: "Grub2 confused by duplicate Ubuntu installations"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by Jar Jar Binks on 2010-09-25
I have two identical Ubuntu installations.  When I boot up and choose the same menu item in GRUB2, sometimes it boots one Ubuntu installation, sometimes the other.  Is it possible to eliminate this ambiguity?

My partitions and drives:
sda1 = Windows XP
sda2 = reserved
sda3 = Ubuntu
sda5, sda6, sda7, sda8  = data
sdb1 = Windows XP cloned from sda1
sdb2 = reserved
sdb3 = Ubuntu cloned from sda3
sdb5, sdb6 = more data
sda = 1.5TB drive
sdb = 2.0TB drive

For example, if I select the same "Windows XP (on /dev/sda1)" in GRUB2 menu, it boots sda1 every time.  But if I select the same "Ubuntu" entry, even though it contains the line "set root='(hd0,3)'", some days it boots sda3 while other days it boots sdb3.

---

### Post by drs305 on 2010-09-25
Unless you have a specific reason to retain them, do yourself a favor and make sure the cloned partitions don't have the same UUID as the originals.

You can easily change the UUID with the following command:
```
sudo tune2fs -U random /dev/sd**[COLOR="DarkRed"]XY[/COLOR]**
```

Check the new UUID with:
```
sudo blkid -c /dev/null
```

If you have the UUID feature disabled in /etc/default/grub, enable it again and update grub and your /etc/fstab file if it contains UUID entries.
```
gksudo gedit /etc/default/grub /etc/fstab
sudo update-grub

```

---

