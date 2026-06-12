---
title: "Installation without deleting Partitons"
date: 2018-08-20
forum: Installation &amp; Upgrades
---

### Post by mdomer9911 on 2018-08-20
Hi

I am windows user for long time, now i have planned for  Migration to Linux so i am planning to delete windows and install Linux but i have a concern
1. My Partitions(D,E,F etc) has large amount of Data , i don`t want to delete these partitions  so is it possible to retain these and Install Linux without Dual boot Option.
2. As i am new to Linux, what all i need to keep in mind to work on Desktop Linux Versions.
3. Is Dual Boot Option good for me as i am planning to complete Migration.
please help me with Video links for proper understanding.
Hope for the Answers..

---

### Post by TheFu on 2018-08-20
When you are new, it is really easy to make a mistake and wipe everything.   Because of that, it is highly, highly, recommended that you backup to other media anything you can't afford to lose.

Many people run Linux inside a VM for a few months before jumping in all the way and deleting the prior OS. This is generally 100x safer than dual-booting or a semi-wipe install, so you can get used to doing things the Unix way.  It is also possible to try things out inside a VM with little risks thanks to snapshots.  This is especially useful when it comes to practice installations and/or trying new storage techniques out like LVM, ZFS, and non-trivial partitioning methods.

---

### Post by yancek on 2018-08-20
It would be necessary for you to post more detailed information to get more detailed advice.  Which release of windows are you using?  How many current partitions do you have with windows?  Do you have separate data partitions on windows?

---

### Post by oldfred on 2018-08-20
Do not delete Windows if you want to keep other NTFS partitions.
NTFS needs maintenance like chkdsk or defrag that you cannot do from Linux. Plan eventually to back up data and copy to a new ext4 partition before deleting Windows.

It took me several years before I could fully convert and delete XP entirely. There was just one application (paid for) I had used since DOS and the Linux somewhat equivalent version (free) was not quite as good. Eventually I decided not quite as good for one app was better than trying to keep XP.

---

### Post by slickymaster on 2018-08-20
Thread moved to **Installation & Upgrades** for a better fit

---

