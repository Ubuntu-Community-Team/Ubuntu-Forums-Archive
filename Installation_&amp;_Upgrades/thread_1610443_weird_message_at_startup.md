---
title: "weird message at startup"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by Rul on 2010-10-31
I just installed ubuntu 10.10. Everything is fine so far except that after the kernel boots I receive the following message:

The disk drive for /media/drv0 is not ready yet or not present
Continue to wait; press S to skip mounting or M for manual recovery

After I press S everything goes normally. How can I get ride of this message?

---

### Post by darkdragn on 2010-10-31
Usually that means there's an entry in fstab that it can't mount. Just edit /etc/fstab, and remove the entry referencing /media/drv0

---

### Post by nbala.iyer on 2010-10-31
the tick for mounting all removable devices may be enabled , you can try unticking that options in the 'Advanced User Setting'

---

### Post by Rul on 2010-11-01
Thanks darkdragn I removed the entry and now everything works perfect

---

