---
title: "Ubuntu with Fedora"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by jyoti9012 on 2011-11-29
I want to install ubuntu keeping my fedora partition intact. How can i do it. Does ubuntu supports dual boot with fedora??? Please help

---

### Post by Rex Bouwense on 2011-11-29
A quick Google check revealed some interesting information.  See here:
[http://ubuntuforums.org/showthread.php?p=10067632](http://ubuntuforums.org/showthread.php?p=10067632)

By the way, welcome to the forums.  Using search will sometimes give you the answer a lot quicker than waiting for someone to answer your question.

---

### Post by ratcheer on 2011-11-29
I have run Fedora 15 alongside Ubuntu, but I added Fedora to a system that already ran Ubuntu.

I don't see why there would be any problem. Just add a new partition to your disk and install Ubuntu to it. I even shared the same swap partition.

If Fedora is still using grub instead of grub2, you may need a little care to make sure it remains set up for booting the way you want. I let Ubuntu's grub2 handle the booting of both installations, but that may not be what you want.

Tim

---

### Post by ajgreeny on 2011-11-29
My only comments would be to:-

1.  Watch out for possible problems related to Fedora's use of LVM for partitioning, which may mean that Ubuntu has difficulty seeing them.  You may have installed Fedora with standard partitions, of course, which will have made things easier.

2.  Do not try to share the same **/home/<user>** folder, if that is in a separate partition from the root.

---

