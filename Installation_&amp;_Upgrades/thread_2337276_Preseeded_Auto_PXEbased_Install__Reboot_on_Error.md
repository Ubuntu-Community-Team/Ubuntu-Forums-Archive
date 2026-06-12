---
title: "Preseeded Auto PXEbased Install / Reboot on Error"
date: 2016-09-16
forum: Installation &amp; Upgrades
---

### Post by brownjl99 on 2016-09-16
Hello,

I am supporting a student undergrad lab of 60 machines which we are moving from windows to Ubuntu. I have set up a PXE server and have the installation of Ubuntu automated via a preseed file. I have built the lab numerous times for testing and I am seeing random errors which is a halting the installation process on random machines - usually about one or two machines in every install.  

The installer is having problems finding the ssd and errors out later in the processes when it then can't find the root partition. If I restart the machine it sorts it self out. I am not quite sure what the cause of this is but as it only happens on one or two machines and a reboot solves its not that critical. 

 Is there a way of forcing the Ubuntu installer to just automatically reboot if it hits fatal error during the install process?

Thanks

James

---

### Post by ian-weisser on 2016-09-18
Is it the same couple machines each time?
Or are the one-or-two machines randomly distributed each time?

Failure to locate the main storage device isn't exactly a minor error.

---

