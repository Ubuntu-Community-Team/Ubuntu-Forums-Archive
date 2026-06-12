---
title: "Fitting 2nd OS on the same hard as Ubuntu system"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by amelie on 2008-07-28
Hello everybody!
I want to run two OS on my hard - I already have Ubuntu, but have also some programs that Wine cannot emule, so I need to put there a tiny windows as well. Can somebody give me some quick guide, because I don't want to use mu cute, comfortable Ubuntu system...
Thanks a lot in advance

---

### Post by Potatoj316 on 2008-07-28
your going to have to partition some space for your XP/Vista install. (20GB should be good but 30 better) I would do this using gparted from your ubuntu install CD.  (system->administration).  Resize the ext3 partition and leave the empty space there (your xp/vista disk will format it) then boot with your xp/vista disk and install.  Tell it not to use the entire HD and instead us the unallocated space.  

When you finish this you will have to reinstall GRUB.  Do a quick search in either google or these forums to find out how.  (its really easy though) then add windows to your menu.lst file (/boot/grub/menu.lst) and you will be set.  

You might realize that your windows system is using the f drive instead of the c drive. this is normal and it is due to the fact that you have other partitions on your drive.  (windows labels them even though it cant see them) I have heard that you can change the drive label but I dont know how or care to.  (even though my default drive is the f drive)

---

### Post by ajgreeny on 2008-07-28
I think you may also find that the work on the ubuntu root partiton has changed its UUID and there may be a problem with booting into ubuntu as a result of the new UUID and that in /etc/fstab being non-matching.

If I'm right just boot to the live Ubuntu CD again, run sudo fdisk -l inthe terminal and make a note of the UUID for the ubuntu partition.  Now mount the ubuntu partition and then edit the fstab UUID entry for the partition to be the same as that using ```
sudo gedit /etc/fstab
```From memory, I don't think a password is needed, in spite of using sudo in this command as you are using the live CD, but without the sudo, I don't think you can edit the fstab file.

If I'm wrong and you can boot straight into ubuntu after using gparted, my appologies for perhaps putting the frighteners on you, but forewarned is forearmed.  Good luck!

---

### Post by amelie on 2008-07-29
Thank you guys so much! I'm going to try it now :) :lolflag: Thank you Thank you thank you!!!

---

