---
title: "Upgrade mess-me up"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by photoman64 on 2008-08-04
Hello. I am new to Linux and installed in dualboot Ubuntu 8.4.
It installed fine and the sound was working fine.
After couple of hours I was able to make the wireless working.
I went to update from repository and my sound"bit the dust" and so my wireless.
I have Toshiba 215-5808.
I installed the KPPP so I can get on internet via my Sierra 595U.
That work fine.
Any help? Thanks:mad:

---

### Post by cespinal on 2008-08-04
Im sorry you got caugh in that "booby trap". I also experienced a lot of problem when doing major updates. One thing to do is to check out if you have two o more kernel versions which can be under conflict. You can check how many kernel version you have by simply booting into grub. it will show you which one you wat to load. If that is the case, I suggest you to go to synaptic and search and erase carefully, all the older kernel versions.

---

### Post by photoman64 on 2008-08-05
I found out that for some reason theGrub listing change and I was booting into wrong Ubuntu. Need to find out how to delete that listing. Booting in "generic" got me back my sound and wireless.
The other strange thing come up after update - the "restart" do no reboot to grub but restart Ubuntu. To get to windows ( I still have some programs that I can not replace in Linux - I have to shut down and then restart computer to see grub list.
Beside that two " glitchess" everything work fine. Even my Sierra 595U work fine.
I just found out that turning ter wireless switch off do not disconnect from Ubuntu. With switch in off position - Ubuntu still access my wireless (build-in).
Strange.
I am using Toshiba Satellite A315-5808.

---

