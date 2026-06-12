---
title: "Serious problem about Grub"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by shewenhao on 2008-05-29
I am using IBM T43(is there any special group in this forum to talk about IBM things?)

This laptop has a hidden recovery partition which is pre-organized by IBM. I installed the Ubuntu 7.04 and updated the Ubuntu to 8.04 few days ago. Today I got lot of update files downloaded and installed again. it is ok. But now I could not boot in to windows... Before today update, I could select the system I want to enter. There is ubuntu with diferent kernel version and other two options: Windows Home edition xp and Win NT/XP?2000. Before I just need to select the windows home edition then got windows but today when I selected this one, I entered the recovery partition of the IBM. People using IBM knows that Lenovo allow use to enter this mode by pressing the Access IBM button. But I did not do any thing.....before, ubuntu works perfect to set the grub automatically but today..


Any one has good idea to tell me how to configure the Grub thing?? I checked under Ubuntu that all my windows files systems are still there, nothing has been deleted.


Thank you in advance!:KS

---

### Post by shewenhao on 2008-05-29
I am using IBM T43(is there any special group in this forum to talk about IBM things?)

This laptop has a hidden recovery partition which is pre-organized by IBM. I installed the Ubuntu 7.04 and updated the Ubuntu to 8.04 few days ago. Today I got lot of update files downloaded and installed again. it is ok. But now I could not boot in to windows... Before today update, I could select the system I want to enter. There is ubuntu with diferent kernel version and other two options: Windows Home edition xp and Win NT/XP?2000. Before I just need to select the windows home edition then got windows but today when I selected this one, I entered the recovery partition of the IBM. People using IBM knows that Lenovo allow use to enter this mode by pressing the Access IBM button. But I did not do any thing.....before, ubuntu works perfect to set the grub automatically but today..


Any one has good idea to tell me how to configure the Grub thing?? I checked under Ubuntu that all my windows files systems are still there, nothing has been deleted.


Thank you in advance!

---

### Post by shewenhao on 2008-05-29
I am using IBM T43(is there any special group in this forum to talk about IBM things?)

This laptop has a hidden recovery partition which is pre-organized by IBM. I installed the Ubuntu 7.04 and updated the Ubuntu to 8.04 few days ago. Today I got lot of update files downloaded and installed again. it is ok. But now I could not boot in to windows... Before today update, I could select the system I want to enter. There is ubuntu with diferent kernel version and other two options: Windows Home edition xp and Win NT/XP?2000. Before I just need to select the windows home edition then got windows but today when I selected this one, I entered the recovery partition of the IBM. People using IBM knows that Lenovo allow use to enter this mode by pressing the Access IBM button. But I did not do any thing.....before, ubuntu works perfect to set the grub automatically but today..


Any one has good idea to tell me how to configure the Grub thing?? I checked under Ubuntu that all my windows files systems are still there, nothing has been deleted.


Thank you in advance!

---

### Post by Rallg on 2008-05-29
Try this: When you get to the Grub menu, select the choice for Windows, then edit it within Grub (the on-screen messages tell you how). Change the partition number that attempts to boot Windows. For example, if it shows (hd0,0) then edit it to (hd0,1) and see if that works. If not, try (hd0,2) or whatever.

Doing this will not hurt your system. If it fails, then you simply won't boot to Windows.

If it works, then the next time you are in Ubuntu, manually edit the Grub menu.lst to reflect the proper partition number for Windows. Editing within Grub, at boot, is only temporary for that one boot instance. To edit menu.lst:

gksudo gedit /boot/grub/menu.lst

There are other possible things that could be wrong, but try the above first.

---

### Post by louieb on 2008-05-29
T30 here. Two good places for Linux on a ThinkPad
[ThinkPad Forum ]("http://forum.thinkpads.com/")
[ThinkWiki - Linux on ThinkPad]("http://thinkwiki.org/wiki/ThinkWiki")

---

### Post by Mark_in_Hollywood on 2008-05-29
One place to look:

SuperGrub
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

which makes available, a LiveCD of GRUB, and has lots of help and a forum for specific questions about boot loaders.

Stay tuned to this forum, too, somebody here has probably had the same or similar problem.

---

### Post by tubbygweilo on 2008-05-29
Lots of [ThinkPad]("http://forum.thinkpads.com/") forum and [wiki]("http://www.thinkwiki.org/wiki/ThinkWiki") type information  and plus the [ThinkPad Owners]("http://ubuntuforums.org/showthread.php?t=645208&highlight=lenovo+thinkpad") thread. 

Can't help much with the Grub problem but you never know some of the links above may hold the answer.

---

### Post by Oldsoldier2003 on 2008-05-29
> **shewenhao said:**
> I am using IBM T43(is there any special group in this forum to talk about IBM things?)

This laptop has a hidden recovery partition which is pre-organized by IBM. I installed the Ubuntu 7.04 and updated the Ubuntu to 8.04 few days ago. Today I got lot of update files downloaded and installed again. it is ok. But now I could not boot in to windows... Before today update, I could select the system I want to enter. There is ubuntu with diferent kernel version and other two options: Windows Home edition xp and Win NT/XP?2000. Before I just need to select the windows home edition then got windows but today when I selected this one, I entered the recovery partition of the IBM. People using IBM knows that Lenovo allow use to enter this mode by pressing the Access IBM button. But I did not do any thing.....before, ubuntu works perfect to set the grub automatically but today..


Any one has good idea to tell me how to configure the Grub thing?? I checked under Ubuntu that all my windows files systems are still there, nothing has been deleted.


Thank you in advance!:KS

if you can boot with a live cd and post the output of ```
sudo fdisk -l
``` we can help you get grub up and running for you fairly easily. if you comment and show us which partition is the recovery partition it will make things go a bit faster

---

### Post by abdulahad100 on 2008-05-29
try posting the text of ur /boot/grub/menu.lst file here.

maybe the update changed ur grub config file and it could be easily fixed.

---

### Post by didac on 2008-05-30
post the results of:

```
sudo cat /boot/grub/menu.lst
sudo fdisk -l
sudo /etc/fstab
```

---

