---
title: "reinstall but keeping documents on separate hard disk help"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by snobby500 on 2008-06-10
Im going to install ubuntu as my main OS and get rid of xp for good, but I would like to keep some of my current documents (music, work etc.) from both os's. As i have two hard drives, what i have done is move everything onto ubuntu and then i am going to wipe xp off the other hard drive, reformat to put documents on there, reinstall ubuntu, then bring files back to ubuntu hard drive and ill be sorted :) Then i will take out win xp hard drive for my brother to use :D

My question is, how to i reformat the xp hard drive, i got gparted but cant igure out how delete xp off it :/

thanks in advance

---

### Post by nunki on 2008-06-10
While in ubuntu, make sure the xp harddrive is unmounted, open up gparted, select the drive, and then choose the type of the new partition and size. After you have done that click "apply". That should do it.

If grub is installed on the xp mbr, then  you may have some extra work to do when you reboot. See  [this]("http://ubuntuforums.org/showthread.php?t=224351") thread.

---

### Post by snobby500 on 2008-06-10
Thanks, i did this, but it didnt show up under computer, but i found out how to do this, you have to right click on the hard drive once you have reformatted it and go to flags, and then click boot, then ubuntu will recognise it, hopefulyy this helps someone else with thte same problem :D

Thanks for your help nunki

---

