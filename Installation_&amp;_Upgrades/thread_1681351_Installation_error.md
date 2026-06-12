---
title: "Installation error"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by abhishek_turbo911 on 2011-02-04
I have a 160GB harddrive and Windows 7 is already loaded in it. I want to install 10.04 on another partition but im getting an error.
Here are the screenshots:
[IMG]http://i56.tinypic.com/w1d93q.jpg[/IMG]


[IMG]http://i53.tinypic.com/af93c4.jpg[/IMG]

-e-
I tried with the partition deleting the required partition and creating the same one on FAT32(as ntfs was unavailable) but the same error is shown

---

### Post by Quackers on 2011-02-04
A couple of points.
Firstly, the "no root file system defined" is usually caused by no mount point being selected for that partition where you are trying to install Ubuntu. The mount point should be selected as " / " in the edit partition stage.
Secondly, you are installing to /dev/sda3, which is marked as a fat32 partition. The default file system for Ubuntu is now ext4. This should be selected in the same screen as the " / " mount point above.
Presumably you are aware that whatever was in sda3 previously, will be over-written, and therefore lost?
Thirdly sda4 is shown as unknown. Is there anything in sda4? If not, you can delete that partition.
Alternatively you could create an extended partition in the space now occupied by sda3. Then inside this extended partition you can create as many logical partitions as you like (Ubuntu may need a swap space as well).

---

