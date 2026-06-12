---
title: "Raid Problem"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by shadow-uk on 2006-07-26
'lo everyone,

I'm trying to install Dapper on Asus machine configured in Raid1 Sata. I setup the BIOS to RAID1. Install Dapper. When I try to bootup, machine complains there's no bootable devices. Now if I unplug the second disk, machine boots up and works perfectly. But I need that second HD to be working. Any ideas on what I can do to get it working??

Thanks

---

### Post by csimone on 2006-07-26
what is your motherboard model? ASUS A8V-MX?

---

### Post by shadow-uk on 2006-07-27
No, it's a A8N32-SLI Deluxe.

---

### Post by csimone on 2006-07-28
there seems to be a problem with the SATA controller on some ASUS mobo, it will be fixed in kernel 2.6.18 due out in about a month...I hope.

---

