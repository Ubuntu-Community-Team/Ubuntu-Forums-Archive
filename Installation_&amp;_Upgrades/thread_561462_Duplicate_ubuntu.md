---
title: "Duplicate ubuntu?"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by Onay on 2007-09-27
I want to duplicate my ubuntu install onto another partition. I mainly want to try and mess with some different themes and software that I don't want to mess with my current install.

Is there anyway I can take an image of the partition, resize the partition and make a new partition using the same swap and install the image onto that partition?

---

### Post by logos34 on 2007-09-27
Use partimage, clonezilla, or dd command.

What does

**sudo fdisk -l** (lowercase L)

and 

**df -h**

show?

---

