---
title: "Aptitude question"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2010-01-10
Aptitude is doing something that I think is weird. Could someone provide an explanation of what is going on and how I should deal with it?

A few days ago, I ran "sudo aptitude update" and was given a list of packages to upgrade. Several of them related to the 2.6.31.17 kernel upgrade. I ran "sudo aptitude safe-upgrade" and they were installed, successfully. "uname -r" confirms this.

Yesterday, I ran "sudo aptitude update" again and was informed that there were 30 New packages available. So, I ran "sudo aptitude" and looked at the new packages it had found. Many of them were related to the 2.6.31.17 kernel upgrade!

Why, after I upgraded, is it offering them again as "new"? Should I "forget-new" or handle this in some other way?

Thanks,
Tim

---

### Post by keithweddell on 2010-01-10
If you ran "sudo aptitude safe-upgrade", you won't have got all the kernel updates.  You need to run "sudo aptitude full-upgrade".  See man aptitude.

Keith

---

### Post by ratcheer on 2010-01-10
Thank you, Keith.

Tim

---

