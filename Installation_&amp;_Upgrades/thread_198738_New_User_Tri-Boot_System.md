---
title: "New User Tri-Boot System"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by Stryker30 on 2006-06-17
Im not new to Linux, but it has been awhile since my last Linux Experience. I am trying to install 3 different OS's on one machine with 3 seperate Hard Drives. I have 2 IDE Drives and 1  SATA Drive. The SATA Drive has my Windows XP on it, The IDE Channel 0 has Windows Vista on it, and the IDE Channel 1 is where I installed Ubuntu Linux. I can get Windows XP or VIsta to boot just by changing the boot Priority in the bios no problem. However I cant get Linux to boot, First I was getting the L 99 99 Etc. Error, so I pulled out and old 98 SE CD and booted into dos and FDISK /MBR the boot record to clean it out. Then I reinstalled Linux and now I get no OS on that drive when I try to boot. I know I have a lot to learn when it comes to Linux. The LiveCD boots Fine and runs everything. I am going to check and see if it placed a Boot Manager on my IDE Channel 0 HD now and see if I can boot, otherwise any suggestions would be helpful. In the past I have DUal Booted Linux's with Windows on Seperate Hard Drives without changing the boot Priority in the Bios. Also the installs have come along way since I have used Linux, they were still command line installs then.

---

### Post by Stryker30 on 2006-06-17
Ok, my theory was correct, it did install grub on my IDE Channel 0 HD and now I get an Error 17 and neither Windows VISTA nor Linux will boot. Ill research some more while I wait for replies. Thanks

---

### Post by Stryker30 on 2006-06-17
Well one more reboot and Error 17 Went away on its own and I am up and running on my own Ubuntu install now. now to just make some modifications to my preferences and get going. Luckily I was able to figure this one out on my own!

---

### Post by catlett on 2006-06-17
problem solved while I was posting a reply, no need for it now

---

