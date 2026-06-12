---
title: "installer not recognizing current os"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by compumasta on 2010-06-27
Ok before i get flammed for being a nOOb i must say that i have searched the forum and cannot find what im looking for(barring viewing all 3000 pages in this section of the forum of course.)

i have been using linux off and on since fedora 3(actually ive used fc3 fc6 and now f13) and fedora has always been my distro of choice mainly because back then, it was the first linux that i could find with a truly easy to use installer.

But alas, i am curious about trying ubuntu and have even downloaded the live cd. the only reason i have not installed it as of yet is because when i get to the partitioning section of the installer, it reads that i do not currently have any operating systems installed. I currently use fedora 13 and am using it now so im fairly certain its installed. but maybe its just me.

I dont want to affect my current files when i repartition my space to accomodate the dual boot. is it the installers fault or am i just an idiot?

any help would be greatly appreciated.

---

### Post by absic115 on 2010-06-28
No help I'm afraid just a similar issue when I just tried to install 10.4 on my system with Windows 7 Ultimate 64 bit. It sees the hard-drive OK but cannot see the OS.

Any help would be appreciated.

---

### Post by darkod on 2010-06-28
If you select the manual partitioning, does it show all existing partitions correctly?

You can try running the boot info script in my signature and post the results as explained. They should show more details.

For example, F13 might be installed in LVM setup, and I'm not sure ubuntu installer can "peek" into a LVM and see which OS is there.

---

