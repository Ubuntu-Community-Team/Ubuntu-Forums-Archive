---
title: "Ub install not happening"
date: 2019-01-01
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2019-01-01
I tried 4 times today to do an 18.04 minimal install, and quit after 30 minutes at "something else" stage watching that little icon circling.
Maybe next time....

---

### Post by oldfred on 2019-01-01
That typically means you have a partition issue.
Most often Windows 10 fast start up is on. All the install instructions will tell you that you must have that off.
But a variety of other partitions issues, from RAID in UEFI for drive (should be AHCI) to partition corruption.
If you use gparted to partition in advance it may tell you more, if it shows yellow warning or red icons on a partition.

What brand/model system?
What video card/chip?

---

### Post by ra7411 on 2019-01-01
> **oldfred said:**
> That typically means you have a partition issue.
Most often Windows 10 fast start up is on. All the install instructions will tell you that you must have that off.
But a variety of other partitions issues, from RAID in UEFI for drive (should be AHCI) to partition corruption.
If you use gparted to partition in advance it may tell you more, if it shows yellow warning or red icons on a partition.

What brand/model system?
What video card/chip?

No Win on the machine.
Before the last try I used Gpart to del the part. and create a new one - no warnings.
The partition has been a Ub os for over a year prior to this.
No RAID on the machine.
vid card= msi 210 has worked fine for 2 yrs on this machine.

---

### Post by yancek on 2019-01-01
You will need to post more information to get help, starting first with do you have another OS installed and if so, what is it?  If you have the current windows10 OS, the link below explains dual booting it and Ubuntu.  If that's not the case, you need to post more details.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

