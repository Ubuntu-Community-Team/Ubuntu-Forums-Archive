---
title: "[SOLVED] How do I make extended partition during installation?"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by alex72blue on 2008-10-17
Hello everyone, I am reasonably new to Linux and very new to Ubuntu.

I am struggling to partition my drive during installation.

I am installing 8.04.1 i386 Server on a bare system and would like to create an extended partition, however the only options I have are primary or logical.

I have been around in circles and tried all combinations and searched the forum for answers but failed.

I find a lot of posts mentioning that it is possible to create more partitions by making one of the four primary partitions extended but no info in the threads or the Ubuntu docs that tell me "how" to do this during installation.

I am willing to accept that it might not be possible during the installation process so if there is a way of sorting it out post installation then I am open to guidance on the best set up during install to ensure that I get the desired results later.

To that end this is the partition table I would like to end up with:

primary swap
primary /boot
primary /
extended
[INDENT]logical /usr/local
logical /var
logical /home[/INDENT]


Any help and guidance here would be greatly appreciated.

Cheers,

Alex

---

### Post by theduffman on 2008-10-17
logical can only exist in extended, therefore, create a logical partition and it`ll automatically make it in the extended...

---

### Post by alex72blue on 2008-10-17
Thanks theduffman, I kind of figured that might be it - since i posted I downloaded a copy of gparted live and created my partitions that way, but when I went back into the installation all my new partitions were suprisingly easy to configure.

D'Oh! It's all part of the learning curve I guess.

---

