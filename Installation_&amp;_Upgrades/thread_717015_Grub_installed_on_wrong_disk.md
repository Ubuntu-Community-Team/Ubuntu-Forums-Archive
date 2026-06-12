---
title: "Grub installed on wrong disk"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2008-03-06
A friend (yes, really) installed Ubuntu 7.10 into one of three disks in his computer. 
It was installed on sda. However, sdb is the default boot device in BIOS.

The result was that sdb still boots as before and grub isn't there.

If we boot from the live CD and select "Start from first harddrive" then grub starts!

So, the live CD menu and the Ubuntu installer obviously has the same (but wrong) idea of what the first hard drive is... (I guess)

What is the best way to clear up this mess and get a proper  dual booting system?

Should we reinstall the MBR part of grub onto sdb?

Or could we change the boot order to boot from sda?

---

### Post by Pumalite on 2008-03-06
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

