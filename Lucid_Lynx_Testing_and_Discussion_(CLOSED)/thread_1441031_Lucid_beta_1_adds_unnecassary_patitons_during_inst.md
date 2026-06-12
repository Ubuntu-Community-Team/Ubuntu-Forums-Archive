---
title: "Lucid beta 1 adds unnecassary patitons during installation."
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kgarbutt on 2010-03-28
Lucid 10.04 beta 1 adds unnecessary small 'unformatted partitions during the installation process. It will add them whether you automatically have Lucid partition your drive or if you manually set-up the partitions during installation. In both cases it adds 'unnecessary partitions.'

Because of this bug I went back to Karmic 9.10. Karmic doesn't have this bug. Has anyone else experienced this? Any thoughts on it?

I have a ASUS EeePC 701 (4G SSD) with 2GB ram.

---

### Post by snkiz on 2010-03-28
while I can't say for sure my guess would be Ubuntu is lining up to the block size witch is changing with the new eco drives. Maybe Lucid is already prepared for that change.

---

### Post by Sef on 2010-03-28
Moved to Lucid.

---

### Post by kgarbutt on 2010-03-30
Hey SN,

Good point but this is not going to happen until 10.10. See here:

[http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release](http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release)

Thanks man I really appreciate your response.

---

### Post by gillmt on 2010-03-30
Yes - I have two small unallocated sections of HD on both the PCs running Lucid - both were fresh install and I selected "Use entire HD"

---

### Post by bdrung on 2010-04-04
That's a bug in ubiquity. Please check if it is still present before reporting.

---

### Post by whoop on 2010-04-04
Is this bug reported already? If so, what is the bug id?

---

### Post by bdrung on 2010-04-04
I didn't checked that. You can search through the ubiquity bugs: [https://launchpad.net/ubuntu/+source/ubiquity/+bugs](https://launchpad.net/ubuntu/+source/ubiquity/+bugs) (currently         1257 open bugs).

---

