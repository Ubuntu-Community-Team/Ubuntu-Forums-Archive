---
title: "windows 8.1 dual boot"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by nhyrum on 2015-03-24
I have a windows 8.1 hp pavilion touchsmart laptop that i want to dual boot with ubuntu 14.04. whe i load the ubuntu DVD i get to the instalation step and there is no option to install alongside windows like there has always been(ive installed various versions of ubuntu) I even installed it on my windows 7 desktop with no issues(same DVD even). been reading and seems like its something about this UEFI thing? I also read that i need to disable fast startup as windows doesnt properly shut down on fast start up. When did it get so complicated to dual boot??

what do i need to do to get it to install alongside windows?

---

### Post by Bucky Ball on 2015-03-24
Disable fast start, as you've read. With it on, Windows is 'hibernating', it's not actually off, so the partition/drive is not unmounted. Consequently, your Ubuntu installer won't see it. 

Not au fait with Win8, but I believe you need to boot into Windows and switch it off in the software somewhere. Hopefully someone a bit more familiar with where it is might be able to jump in and help. Try this in the [meantime]("http://mywindows8.org/fast-start-up-in-windows-8/") ...

---

### Post by nhyrum on 2015-03-24
I have alreaddy disabled fast start up and still nothing. still cant install ubuntu as dual boot.

If I remember right it says something about secure boot

---

### Post by Bucky Ball on 2015-03-24
Boot into the BIOS and check it is not set there. Also, if Win is installed using UEFI, don't change that. Ubuntu should also be installed in UEFI, not legacy.

---

### Post by oldfred on 2015-03-24
Best to only use Something Else.
This bug is still in most live installers. Also new installs were Windows not seen.
 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Best to have full backups of Windows, efi partition and have made both the Windows repair CD or flash drive and the image copy that vendor's partition is on hard drive. If system get erased all that is gone, but if you use Something Else you should be ok, but have backups. 
Even if you do not install Ubuntu you should have those backups anyway as hard drives do fail, virus' erase damage system and users make errors.

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

