---
title: "Fresh install on top of existing distro possible?"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by Ken Kaniff on 2008-06-12
Hi all,

I wonder if the following is possible:

I'm running Debian Etch. Unfortunately my install is pretty crashy and I'm tired of the system freezing on me. Is it possible to install another distro into my "root" partition and leave the "swap" and "home" untouched? If yes, it would save all my user files, documents etc.

To clarify, I currently have three partitions: root, swap and home.

Any comments or links you can suggest are welcome.

Thanks.

---

### Post by mikewhatever on 2008-06-12
Yes, in fact, I think you can install any distro. You are not required to modify partitions, other then formatting /root. You'd have to mount all three partitions properly, which is quite easily done during the installation.

---

### Post by Ken Kaniff on 2008-06-12
> **mikewhatever said:**
> Yes, in fact, I think you can install any distro. You are not required to modify partitions, other then formatting /root. You'd have to mount all three partitions properly, which is quite easily done during the installation.
Mike, can you explain what you mean by saying I'd have to mount all three partitions properly? 

I thought I'd need to skip "swap" and "home" installation and proceed with installing "root" only.

---

### Post by mikewhatever on 2008-06-12
At the partitioning stage of the installation go with Manual, select appropriate mount points for root, home and swap as /, /home and swap, and then proceed. If you do not mount, say, home during installation, the installer would think it a data partition and create another home within root. You'll be required to format root, but make sure you do not format home.
[Installation Guide]("http://psychocats.net/ubuntu/installing")

---

### Post by Ken Kaniff on 2008-06-13
This makes perfect sense. Thank you.

---

