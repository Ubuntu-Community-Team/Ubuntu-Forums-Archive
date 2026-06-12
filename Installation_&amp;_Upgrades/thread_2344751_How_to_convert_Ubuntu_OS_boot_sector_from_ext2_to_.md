---
title: "How to convert Ubuntu OS boot sector from ext2 to ext4 file system"
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by sekhar123 on 2016-11-28
Hi Experts,

We have system whose OS is installed with ext4 file system & boot sector is installed in ext2 file system.
We want to convert the boot sector file system type from ext2 to ext4.
Can you please say us how can we do this without re installing the OS.
My email id for communication is {email removed}

---

### Post by Dennis N on 2016-11-28
The correct terminology would be boot _partition_. You won't gain anything noticeable by making a change to ext4, especially since the partition is very small.

Here is a guide you might follow should you decide to proceed:

[http://www.ghacks.net/2010/08/11/convert-ext23-to-ext4/](http://www.ghacks.net/2010/08/11/convert-ext23-to-ext4/)

(found by google search - I have not done this myself.)

---

### Post by oldfred on 2016-11-28
Removed email, you would get spammed as forum is open and regularly searched.

Also we are a forum where users help users and then can search for solutions. Privately emailing a solution does not help others.

Ubuntu standard install of full drive encryption uses ext2. The advantage of ext4 is the journal which then allows fast fsck and repair. But with a small ext2 fsck is still pretty quick.

---

