---
title: "Can't find inittab file"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Doojek9 on 2007-05-01
Hi all. 

Installed Feisty recently and for some strange reason I don't have the /etc/inittab file. 

Does something change in this version?

Thanks.

---

### Post by phiphedog on 2007-05-01
init has been replaced by upstart.

if you wish to change you runlevel upstart still looks for the inittab file for a user set runlevel. Just create the inittab file and put the following line in it to boot to runlevel 2

[COLOR="Red"]id:2:initdefault:[/COLOR]

---

### Post by Doojek9 on 2007-05-01
Thank you.

---

