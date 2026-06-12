---
title: "Unable to shrink windows partion during Ubuntu 12.04 dual boot installation"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by ohnoplus on 2013-08-12
Hello.  I am working with a PowerBook6455 B with a windows 7 (not the original) operating system installed.  I am trying to create a new partition with Ubuntu 12.04 from a live USB. When I go to install and click the "something else" option, I get the "Installation type" window.  It lists the following partions as existing
/dev/sda"
    Device: /dev/sda1, Type: ntfs, Mount Point: [blank], Size: 104MB, Used 35MB
    Device: /dev/sda2 Type: [Blank]:, Mount Point [blank], Size: 249952, Used [blank]

If I select the sda2 device and click change, I get the Edit a partion window.  This window does not give me an option to set a new size for that partion.
Can anyone suggest why I do not have that option, why it doesn't tell me how much space is used on sda2, and how I can work around this problem?

Thanks for any advice.
Best,
Jacob

---

### Post by ohnoplus on 2013-08-12
One more bit of information.  I tried going into gparted through the live USB.  /dev/sda2 is also listed as an unknown file system.  It has a little exclamation point.  If I click on it, it reads: 
Warining: Unable to detect file system! Possible reasons are:
-The file system is damaged
-The file system is unknown to GParted
-There is no file system available (unformatted)
-The device entry /dev/sda2 is missing.

Also the windows OS was installed as a sort of novell client operating system by my university, which may have some bearing on the situation.

---

### Post by grahammechanical on 2013-08-12
It is my understanding from reading posts on this forum that it is always best to use Windows tools to resize Windows partitions and then to make sure that Windows is booting correctly. I have read that you should defrag the disk first and to do it twice.

There is one more thing that you should consider. Is that disk a Microsoft Dynamic disk? If it is then Gparted will not be able to do much with it.

Regards.

---

