---
title: "Unable to use existing partitions"
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by lduperval on 2005-10-31
Hello,

I am trying to install BB, but when I get to the partition table, I'm having problems. Specifically, I already have a disk with logical partitions on it. However, when the installer displays the disk information, it shows no partitions for my primary disk (hda). The only option I have seems to be to erase all information from the partition table and start froms scratch.

I tried to use the guided partitioning but it brings me back to the original screen.

My current installation is a Mandrake 9.1 installatyion, I believe.

L

---

### Post by Kyral on 2005-10-31
Are the logicals LVM by anychance?

---

### Post by lduperval on 2005-10-31
Uhm, it's possible. I'll have to check.

If I remember correctly, though, I tried using LVM and it also only gave me the option to erase everything. But, I may be wrong.

L

---

### Post by lduperval on 2005-11-01
I tried it and in the end I had to delete everything on the disk. I had a number of issues:

- Formatter complaining of disk already in use
- Refusal to format the drive if it was a reiserfs partition
- Other stuff

In the end I gave up, trashed the existing drive and tried to install over the entire disk. However, I'm seeing the stalled installation problems that others have reported. I'm using an old Creative CD ROM. 

L

---

