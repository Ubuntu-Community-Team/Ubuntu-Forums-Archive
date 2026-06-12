---
title: "Installer Reads Partition Wrong"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by opticyclic on 2006-10-26
Look at the screenshot.
It shows the output of GParted and the output of fdisk -l

This causes me a problem of not being able to reformat sda3 and sda8 as ext3

Is my only option to boot to windows and format from there?

---

### Post by ribena on 2006-10-28
Hi,

Having similar problems: [http://ubuntuforums.org/showthread.php?p=1676755](http://ubuntuforums.org/showthread.php?p=1676755)

Looks like gparted isn't working properley... Not sure why?

Rob

---

### Post by opticyclic on 2006-10-28
When I ran GParted from the command line I got an error along the lines of:
"partitions cant overlap"
It was yesterday so I cant guarantee that was exatly it.
However, it might be thinking that the Extended partition (sda2 in my case) is overlapping all the subsequent ones. :-k

---

### Post by opticyclic on 2006-11-06
This was resolved by deleting the ext3 and swap partitions that I had created in Windows.
GParted could then see the rest of the partitions and I could recreate the ext3 and swap partitions in linux.

No idea why this worked, but it did.

It is worth remembering that you can only have 1 extended partition and that GParted will let you create NTFS and ext3 partitions within that extended partition.

---

