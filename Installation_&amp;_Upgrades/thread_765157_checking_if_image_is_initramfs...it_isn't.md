---
title: "checking if image is initramfs...it isn't"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by oliver341 on 2008-04-24
When I upgraded my Ubuntu server from Gutsy to Hardy using do-release-upgrade all seemed fine. However, the boot procedure now hangs after these two lines:

[   28.190344] checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
[   28.216154] Freeing initrd memory: 8194k freed

I have reverted back to using the vmlinuz and initrd.img from Gutsy, which still works. However obviously I'd like to get the Hardy kernel working!

Any ideas please?

---

### Post by vja on 2008-07-15
See [https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/221664]("https://bugs.launchpad.net/ubuntu/+source/lilo/+bug/221664")

Summary: initramfs grew too big, you have to include a line with "large-memory" in /etc/lilo.conf and rerun lilo.

Vincent.

---

### Post by oliver341 on 2008-07-16
Thanks for the update. I managed to install Grub in the end and get the serial console operational, but it's handy to know it wasn't something I was doing wrong!

---

