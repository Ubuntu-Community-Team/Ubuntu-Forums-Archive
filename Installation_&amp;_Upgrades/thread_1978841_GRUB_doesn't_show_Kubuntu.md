---
title: "GRUB doesn't show Kubuntu"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by Shishimaru on 2012-05-12
Hello!
I installed Kubuntu 12.04 on my "testing" partition with btrfs and external /boot on ext2. Then, I decided to use GRUB with my main system, which is Ubuntu 12.04 and I run "sudo grub-install /dev/sda". Now GRUB doesn't show Kubuntu anymore, what can I do. Is it because of Btrfs? It's strange because GRUB, from Kubuntu, shows everything.
Of course update-grub doesn't solve.

---

### Post by darkod on 2012-05-12
It might be because of btrfs but I was under the impression that it will pick up the separate /boot and should recognize Kubuntu.

---

### Post by Shishimaru on 2012-05-12
Exactly!

---

