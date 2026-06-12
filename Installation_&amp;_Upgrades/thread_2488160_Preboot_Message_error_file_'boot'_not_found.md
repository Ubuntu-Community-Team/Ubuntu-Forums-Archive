---
title: "Preboot Message: error: file '/boot/' not found"
date: 2023-06-25
forum: Installation &amp; Upgrades
---

### Post by darrylrowan on 2023-06-25
Hello,

When I boot Ubuntu Studio 22.04.2 from my bootable USB on my Dell OptiPlex 7050 SFF and 7060 SFF PCs, I get the error message: **error: file '/boot/' not found**  just before it enters the GNU Grub version 2.06 screen/menu. It happens  very quickly, but I am curious on what it is and why it occurs.  Everything seems to work well otherwise. I created the bootable USB  using Disks - Restore Disk Image tool from the verified ISO.

Any information would be helpful.

Regards,
Darryl&#8203;

---

### Post by Rubi1200 on 2023-07-02
Hi and welcome to the forums :-)

More than likely the system is looking for other boot files (Windows perhaps) and when it does not find them skips past to the next order of the day.

As long as you can boot normally and access Ubuntu, I wouldn't worry about it.

---

