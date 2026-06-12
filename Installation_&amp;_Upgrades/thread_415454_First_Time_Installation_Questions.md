---
title: "First Time Installation Questions"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by HogWild on 2007-04-20
I'm trying to make the switch from windows to linux and was recommended Ubuntu as a place to get started. Because of recent problems with windows I decided to reformat my HD and reinstall it along with installing Ubuntu and thus creating a dual booting system. WIN XP has been installed and my HD reformatted to create two partitions, one of which will belong to windows and the other to Ubuntu. Baby steps, right? I want to install Ubuntu on my second partition, but I'm getting lost when trying to perform the initial set up when it's asking me how I want to partition my HD. I'm unclear if I select "GUIDED" will it attempt to install over my windows xp installation or will it automatically select the empty partition and install there? Also, what will I need to be able to choose between the two OS's upon boot? I'm trying to make this as user friendly for not just myself, but for my family as well.

Thank you in advance.

HogWild

---

### Post by cogadh on 2007-04-20
If you choose guided, it should give you the option to use the largest available free space, which should be the second partition. The partitioner does not actually make any changes to your drive until you finish the install wizard, so you can always click "Back" or "Cancel" before comitting your changes.

The install process will automatically install the GRUB boot loader for you which will allow you to choose between the two OSes. You won't get a prompt to install it, it just does it for you.

---

### Post by HogWild on 2007-04-20
Many thanks for the quick response!

---

### Post by HogWild on 2007-04-20
Well, I ran the Guided-Largest Free Space utility and it keeps telling me that my HD is too small to partition. I have an 80GB HD with 40GB dedicated to win xp and the other 40GB to be dedicated to Ubuntu. I know that I'm not at all on the cutting edge, but this is what I have. So, I'm stuck at this point and am unclear as to how to properly partition my HD. As stated above, my HD is already partitioned to two separate HD's C & D and I'm trying to get Ubuntu to install on D. Do I need to install win xp, reformat and create only one partition and allow Ubuntu to create it's own when installing? Please advise.

Thanks in advance.

HogWild

---

### Post by cogadh on 2007-04-20
If you already formatted the second partition (i.e. Windows already sees is as another drive) then boot into Windows, go into Disk Manager (Start -> Run -> type "diskmgmt.msc" -> hit enter), right-click on the second partition and select "Delete Partition...". Then you can reboot to the Ubuntu CD and it will see that as free space it can install to.

If your second partition is within a logical drive, you will also have to delete the logical drive after you delete the partition in order to be sure the area is totally free space.

---

