---
title: "Partioner Problems"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Grantham on 2008-06-05
Hello there,

I recently FINALLY got Ubuntu to boot from Live CD, and now I'm at the Partitioner. I've set it to all the different filesystems, but all of them come up with the same error 'No root filesystem is defined' and I am extremely confused and would love to fix this very soon.

Grantham

---

### Post by iaculallad on 2008-06-05
> **Grantham said:**
> Hello there,

I recently FINALLY got Ubuntu to boot from Live CD, and now I'm at the Partitioner. I've set it to all the different filesystems, but all of them come up with the same error 'No root filesystem is defined' and I am extremely confused and would love to fix this very soon.

Grantham

If you're using the manual partitioning using the GParted, be sure to create a mountpoint named "/", this is your root filesystem, and select a filesystem under the "FileSystem" collumn.

Or

If you're drive is empty, you could use the automatic partitioning instead. Gparted will create/give all the mountpoints and filesystem for you.

---

### Post by Grantham on 2008-06-05
What filesystem should I use? I have it set to ext3 I think..

---

### Post by iaculallad on 2008-06-05
> **Grantham said:**
> What filesystem should I use? I have it set to ext3 I think..

Ext3 will be just fine.

---

### Post by talktoari on 2008-06-05
Do you have any other OS previously installed in ur machine?

In that case, use a partition manager and create an "unallocated space" by shrinking some volume or formatting and creating new partition.

After that while installing Ubuntu, you can choose an option which says "Choose Maximum contiguous space for install" and this should trigger ubuntu to choose the new unallocated partitioned space and create partitions automatically as it needs.

Hope this helps.

---

### Post by Grantham on 2008-06-05
I have Windows XP SP2 installed on a separate partition right now.

---

### Post by Pumalite on 2008-06-05
Delete

---

### Post by iaculallad on 2008-06-05
> **Grantham said:**
> I have Windows XP SP2 installed on a separate partition right now.

That would be good. Now, insert your Ubuntu LiveCD and continue your installation. Select manual partitioning on your Gparted so as not to mess your xp partition. Installation would automatically detect your xp os for you and add it to its GRUB menu for dual boot.

---

### Post by Grantham on 2008-06-06
Thanks guy (And girls) I got Ubuntu to install finally >:D

.. And it shut off during update. Great. Now I have to reinstall Ubuntu so I can update. Stupid errors *Kicks*.

---

