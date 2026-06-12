---
title: "installation says: &quot;the disk has no OS on it&quot;"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by shaon3343 on 2009-12-11
[SIZE=2]**hi , In my friends pc which was infected with virus and for this we have to reinstall windows. the windows installation went well but after that we wanted to install ubuntu on it. but unfortunately the ubuntu installation showed that "the disk has no operating system on it"!!! (i've included the screenshot.)then we cheked with gparted on that live cd but it also cant recognize the windows on that hard-disk we tried with kubuntu live cd but the result was same.then we boot up with windows and through computer management we deleted a disk and keep it unallocated. and then again tried with ubuntu 9.10 live cd but still the same "no operating system":(. so how can i fix this problem? please help me.**[/SIZE]

---

### Post by darkod on 2009-12-11
You should not have deleted windows.
If you want to dual boot with windows, install windows again but not on the whole drive. Create only partition for windows with the size you want to dedicate for it. Leave the rest of the hdd unallocated for ubuntu.
This "problem" with not seeing the drive correctly usually happens if there is a raid settings remains on the hdd. If you are not running raid, boot with the ubuntu cd, Try Ubuntu option, and in terminal execute:
sudo apt-get remove dmraid

That should make the problem go away and the disk to be visible to ubuntu.
After that boot with the cd again, select Install Ubuntu and use the Use Largest Continuous Space option and ubuntu will be installed in the unallocated space planned for it.

---

### Post by shaon3343 on 2009-12-13
**sorry for late :( . thanks for your reply, the problem was on my friends pc and before I inform him your solution  he unallocated two of his primary drive ( except the drive containing windows) and then reboot with ubuntu9.10 live cd and this time ubuntu found the partition and also detected the windows on that disk. Now my friend is enjoying ubuntu 9.10** . :D

---

### Post by macmaster on 2009-12-13
Maybe this was incorrectly burned, to burn safely burn it with a free program called "Imgburn" for windows, burn it at 4X or lower. And you don't have to repartition your hard drive, ubuntu 9.10 install does this for you. Repartition is only needed for older versions of ubuntu.

Reply if this didn't work or if you need more help.

---

