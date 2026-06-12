---
title: "Installing on JFS with custom partitions"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by bLUEbYTE on 2006-10-10
Hi,
I will soon install Ubuntu to my computer. I am a JFS user for some time, and I want to stay pure JFS. There are freshly formatted JFS partitions ready for the Ubuntu install. I have:
/dev/hda1 swap
/dev/hda2 JFS
/dev/hda3 JFS

I want /dev/hda2 to be mounted as root (/) and /dev/hda3 as (/home).
From my past (limited) experience with Ubuntu and it's very simplistic installer, I doubt that it will give me the choice to do it like I want it. So, how can I tell it to do it like this when installing?

EDIT: Nevermind, installer was nice and all done. Didn't know that it offered custom partitioning.

---

### Post by x64Jimbo on 2006-10-10
Eww.. JFS partitions are not resizable. I used to use JFS until I found that out.

---

### Post by bLUEbYTE on 2006-10-10
I am not corcerned with them being resizable or not... I didn't mention such cuncern in my post either.

---

### Post by x64Jimbo on 2006-10-10
Boot a LiveCD like Knoppix and use a partition manager like QTParted to pre-partition the drive. You'll have to find out if it includes support for creating JFS partitions before you download and burn it though. Also, you would need to make sure that Ubuntu's installer can write to JFS partitions, which I am unsure of.

---

### Post by bLUEbYTE on 2006-10-11
For the record, yes it did install properly to the above mentioned preset JFS partitions.
I had the partitions formatted by the Gentoo LiveCD (before Ubuntu installer)

---

