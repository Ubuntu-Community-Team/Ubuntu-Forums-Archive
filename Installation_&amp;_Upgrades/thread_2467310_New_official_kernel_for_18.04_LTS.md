---
title: "New official kernel for 18.04 LTS?"
date: 2021-09-22
forum: Installation &amp; Upgrades
---

### Post by pmaff on 2021-09-22
With the 4.15.0-151 kernel I had the file system and other problems described here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1938013](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1938013)

I went back to  4.15.0-147 .
But somehow it looks as if I switched off kernel updates.
What is the newest official kernel for 4.15.0-147-generic ?
How can I tell the system to check for a newer kernel (if it is not 4.15.0-151 still) and do the update?

lsb_release -a says:
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.6 LTS
Release:    18.04
Codename:    bionic


Thanks in advance.
Pete

---

### Post by MAFoElffen on 2021-09-22
If you run the system-info script in my signature line, it has a section that wull tell you, and if it safe to intsall the HWE on your system (along with information about your hardware and your system settings...

But just to figure out that one question, run
```

dpkg -s linux-generic-hwe-$(lsb_release -sr)

```

---

### Post by deadflowr on 2021-09-23
Latest GA kernel available for 18.04 is 4.15.0-158.
Presumably the implied Fix for the bug was built into it.
Disabling kernel updates would mean you removed or set as held the linux-generic, or subsequent linux-image and linux-headers-generic packages.
So if you had not apt-mark held the package simply reinstall the linux-generic package.
After that do a regular update.

---

