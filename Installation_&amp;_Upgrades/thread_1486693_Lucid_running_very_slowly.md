---
title: "Lucid running very slowly"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by andydch on 2010-05-18
After sucessfully install on my laptop, Lucid running very slowly, I have to wait until 5 seconds to open firefox or other applications.

Can anybody give me solution to solve this problem?

Thanks

---

### Post by chiwi on 2010-05-19
during those 5 seconds, is the CPU at 100% ? may be the problem is in your disk

---

### Post by andydch on 2010-05-19
> **chiwi said:**
> during those 5 seconds, is the CPU at 100% ? may be the problem is in your disk

what's problem? can u give me explanation?
during 5 seconds, CPU is in normal way, about 20%-30%...

---

### Post by chiwi on 2010-05-20
open a terminal, run 'top', and open firefox, which process is taking up your cpu?

---

### Post by efflandt on 2010-05-20
Two things you could try.

Try **nomodeset** kernel boot parameter to use regular video modules instead of the new kernel mode setting (KMS). [http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

Or you could try disabling Visual Effects under System > Preferences > Appearance.

The new KMS slowed up certain video actions of my desktop with legacy ATI X1300 video (and broke suspend/hibernate), and caused some boot video issues with similar Radeon Mobility X1300 on a laptop.  But with nomodeset, they work as well as 9.10.

---

