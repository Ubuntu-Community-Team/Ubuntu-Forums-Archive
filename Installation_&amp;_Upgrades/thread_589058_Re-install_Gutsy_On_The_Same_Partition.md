---
title: "Re-install Gutsy On The Same Partition"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by gimmy_bond on 2007-10-23
After updating from 7.04 to 7.10. All seem to worlk fine until today. Due to few boot up and network issues I like to re-install a whole new 7.10 on the same petition from the CD, while preserve the HOME directory located on another partition. 
Please note, I don't wish to update through live update. just reinstall a whole new system on the same location as the previous one.

Any suggestion would be appreciated

---

### Post by Pumalite on 2007-10-23
You are fine.Just install over the other one in the same partition. Use your /home partition for the new install. Just don't format it.

---

### Post by jimrz on 2007-10-23
> **gimmy_bond said:**
> After updating from 7.04 to 7.10. All seem to worlk fine until today. Due to few boot up and network issues I like to re-install a whole new 7.10 on the same petition from the CD, while preserve the HOME directory located on another partition. 
Please note, I don't wish to update through live update. just reinstall a whole new system on the same location as the previous one.

Any suggestion would be appreciated

This assumes that you have a separate /home partition:

Just pop in the live cd, run the install and when you get to the partitioner select "manual" and proceed as follows:

1- mark your current "/" partition to be formatted. them click "edit partition" and select "/" as it's  mount point.

2- select your current "/home" partition but do NOT select the format box, rather just click "edit partition" and then select "/home" as it's mount point.

3- click "Next" which will take you onyour way through the rest of the installation.

This will re-format your "/" and "swap" partitions, giving you a fresh install, while leaving your current "/home" partition intact and still correctly mounted.

---

### Post by gimmy_bond on 2007-10-23
Jim
Thanks for the quick reply. I will follow your suggestion.

---

