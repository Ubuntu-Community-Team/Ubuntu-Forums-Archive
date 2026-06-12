---
title: "Must Format? Why?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by pinoytechie on 2007-05-01
I'm trying to install Feisty Fawn in my other machine. There's an existing install of Ubuntu in the target partition (ext3), and it's Edgy to be exact. I started LiveCD and started Install. After the destination partition is set, I left "Format" unchecked because there are data there that should not be deleted, i.e. documents, pictures, downloads, etc. But the installer is saying that it must be reformatted? Why? it's ext3 already!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=31412&d=1178004578[/IMG]

---

### Post by aysiu on 2007-05-01
It's because you selected the mount point as /

If you have data on there, mount it as /documents or /data instead of /

---

### Post by pinoytechie on 2007-05-01
but it's the partition where I will install Feisty, and the installer i must set it as root (/)

---

### Post by aysiu on 2007-05-01
The / partition has to be reformatted--otherwise, you're not really reinstalling.

As I said before, to preserve data, you should have a separate /home partition or /data partition or /documents partition.

[Create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome) and then mount the new /home as /home (not reformatted) and the other partition as / (formatted).

---

