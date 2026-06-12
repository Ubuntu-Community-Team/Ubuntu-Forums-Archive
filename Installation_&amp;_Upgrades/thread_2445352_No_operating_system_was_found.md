---
title: "No operating system was found"
date: 2020-06-12
forum: Installation &amp; Upgrades
---

### Post by philosofool on 2020-06-12
I installed Ubuntu from a USB onto an old computer. The HDD I used also contained some personal data that I didn't want to use, so I created a new partition while installing and added Ubuntu to that partition. The installition proceeded smoothly and I restarted when prompted. After the restart, I got the error message that no operating system was found.

There are no other OSes on the drive. I suspect this is connected to the partitioning. The data on the drive is important and I don't have any other drives for that data, so eliminating the partition is not an option. 

[LIST=1]
[*]Is there a way to fix this so that the computer will detect Ubuntu without having to reinstall?
[*]If not, was there some setting that I should have set differently (likely with the partition) so that I can re-install and have a bootable installation?
[/LIST]

Thanks.

---

### Post by oldfred on 2020-06-12
Cannot emphase how important having some backup of your data is.
And wrong select, drive failure, lightning strike, and many other reasons may damage or destroy your one copy of data.

Where did you install boot loader, it default to first drive?

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

### Post by philosofool on 2020-06-12
I fixed it.

I booted to Ubuntu from my USB drive. Using disk, I unchecked bootable for the data partition and check bootable for the Ubuntu install. It booted from the HDD.

---

