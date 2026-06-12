---
title: "Can't install neither ubuntu nor xubuntu"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by lentia on 2014-06-15
Hello. I have problem with installing ubuntu 14.04 along with windows 7.  Look at picture. 
[IMG]http://i59.tinypic.com/a424nn.jpg[/IMG]
On installing xubuntu 14.04 I have different problem. An installer does not see my disks correctly. 
sdd  its hitachi 320GB: 1-41GB windows C: ntfs, 2-43GB ext2, 3-4GB ext2. Partitions 2 and 3 prepared for linux.
[IMG]http://i62.tinypic.com/v5fsr5.jpg[/IMG]

---

### Post by Adam_GUI on 2014-06-15
Did you setup Windows with Extended or Logical partitions?
The Parted Library of the installer should only be showing primary partitions.
Industry standard has always only allowed a maximum of four primary partitions per drive.
That should be why all seven of your desktop locations don't show up in your installer.

---

### Post by lentia on 2014-06-15
Oh! Thank you for answer. But is it possible to install linux (or ubuntu) in my situation? along with windows without reinstalling it.
I think I get it. AOMEI Partition Assistant utility allows to choose between primary and logic partition type.
I will try xubuntu with primary option.

P.S. About standards. They limit the possibilities.

---

### Post by lentia on 2014-06-15
Well. I did install xubuntu. Made an upgrade, 
and learned that using fglrx leads to a black screen of death.

---

