---
title: "installation- no root system defined"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by shady2 on 2014-01-25
looked at the guide before I went to install Ubuntu 12.04. Well I chose other, the last of the options because i did not want to install alongside windows. Want to have in its own partition. What am I missing or doing wrong when it says no root file system defined ??

---

### Post by grahammechanical on 2014-01-25
We chose the Something Else option and when we get to the partitioning section we select the partition we intend to install Ubuntu in and we click Change. At the next dialog we go to the panel Use As and select Ext4. We then tick the box to format. Then we set a mount point. That is the step that you missed. There is a panel called Mount Point, select / and then click OK. That will take you back to the partitioning screen. Double check that everything is as you want it to be and click Install.

Selecting a mount point of / will define the root file system.

Regards.

---

### Post by ali12 on 2014-01-27
> **grahammechanical said:**
> We chose the Something Else option and when we get to the partitioning section we select the partition we intend to install Ubuntu in and we click Change. At the next dialog we go to the panel Use As and select Ext4. We then tick the box to format. Then we set a mount point. That is the step that you missed. There is a panel called Mount Point, select / and then click OK. That will take you back to the partitioning screen. Double check that everything is as you want it to be and click Install.

Selecting a mount point of / will define the root file system.

Regards.


Ive done that same exact way and it takes me into a minimalist grub menu with bash commands. any insight on this?

---

