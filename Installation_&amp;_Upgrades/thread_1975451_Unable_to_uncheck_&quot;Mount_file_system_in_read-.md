---
title: ": Unable to uncheck &quot;Mount file system in read-only mode&quot;"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by Hvide on 2012-05-07
Hi everyone:
I have just install ubuntu 12.04.
After installed,  for mount my data partition (sda3, NTFS) at the startup, I installed Storage Device Manager

[ATTACH]217467[/ATTACH]

Since then i can access the partition in read-only mode, i can't write it!

I tried to uncheck the box "Mount file system in read-only mode" in Storage Device Manager and perss applay, but as soon as i clic on "assistan" the box is tick again.

[ATTACH]217469[/ATTACH]

Can anyone help me to be able to read and write to the partition

Tks in advance

---

### Post by Hvide on 2012-05-19
After try different solution I reinstall with "synaptic packet manager" the packet "ntfs-3g" and smoe how now i'm able to modify my file on the NTFS partition...

I don't know way but it work!

---

### Post by Rulius on 2012-09-03
> **Hvide said:**
> After try different solution I reinstall with "synaptic packet manager" the packet "ntfs-3g" and smoe how now i'm able to modify my file on the NTFS partition...

I don't know way but it work!

Reinstalling ntfs-3g didn't work for me.
The solution came from installing and using "NTFS configuration tool"

---

