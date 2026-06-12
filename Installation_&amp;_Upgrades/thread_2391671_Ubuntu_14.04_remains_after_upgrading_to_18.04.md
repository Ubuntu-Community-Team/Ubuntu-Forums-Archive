---
title: "Ubuntu 14.04 remains after upgrading to 18.04"
date: 2018-05-12
forum: Installation &amp; Upgrades
---

### Post by belek on 2018-05-12
Hi!
Yesterday I upgraded my Ubuntu 14.04 to 16.04 and then after to 18.04.
But now in grub boot list I see Ubuntu (which is 18.04) and Ubuntu 14.04. Both of them working fine.
How can I delete 14.04 and have only 18.04?

---

### Post by dino99 on 2018-05-12
Please post 'sudo blkid' output

---

### Post by belek on 2018-05-13
/dev/sda1: UUID="3c2e2dae-27c0-432d-9535-d471c6c7a74b" TYPE="ext4" PARTUUID="000a25c6-01"
/dev/sdb1: LABEL="System" UUID="9246B18746B16C9B" TYPE="ntfs" PARTUUID="1f84d969-01"
/dev/sdb5: LABEL="Data" UUID="700C9417A74E6BB4" TYPE="ntfs" PARTUUID="1f84d969-05"
/dev/sdb6: UUID="131b7972-3d8b-40e8-9207-ee2398a129c4" TYPE="ext4" PARTUUID="1f84d969-06"
/dev/sdb7: UUID="784d9966-0384-4ed6-8888-120610beca24" TYPE="swap" PARTUUID="1f84d969-07"
/dev/sdb8: UUID="b49f12ca-626d-43c3-9087-399a0cd75a5e" TYPE="swap" PARTUUID="1f84d969-08"

---

