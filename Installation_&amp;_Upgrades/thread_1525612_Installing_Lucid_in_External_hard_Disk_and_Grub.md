---
title: "Installing Lucid in External hard Disk and Grub"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by kailsen on 2010-07-07
I had previously installed hardy in myoffice  Desktop internal hard disk. I bought a new Seagate Hard disk(500GB) so as to install Lucid and and can use in my home desktop that has Windows alone(80GB). Since at home there is know internet i want to install Lucid in External drive so i can update in office. I installed it in my external drive using my office machine. and but the Grub loader in the same external drive. when i restart the machine i have Grub menu.lst of the internal hard drive alone. how to change it to the external one. Lucid has grub2 while hardy has grub. Please help.

---

### Post by C.S.Cameron on 2010-07-07
When you get past partitioning when installing to the external drive there will be a tab named "Advanced". If you click this you can choose to install grub to the external drive.
Another option is to disable the internal drive when installing to the external one.
You can also use the Live CD to reinstall grub to the external drive.

---

