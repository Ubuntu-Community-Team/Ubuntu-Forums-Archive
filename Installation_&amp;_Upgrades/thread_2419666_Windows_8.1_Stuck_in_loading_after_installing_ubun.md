---
title: "Windows 8.1 Stuck in loading after installing ubuntu"
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by ghost-am on 2019-05-24
Hey!
I installed ubuntu 18.04 next to windows 8.1 (i mean that i don't erase windows or install that in vmware or virtualbox) but after installation i can't get access to windows i can see windows 8.1 option in first grub menu but when i enter that the windows stuck in loading 

please help me!

---

### Post by yancek on 2019-05-24
I would suggest you read the Ubuntu documentation at the link below which explains dual booting Ubuntu with windows uefi which is likely what windows 8 is.  Compare the expalanation to what you did.  If that doesn't help and you can boot Ubuntu, go to the second link below and download and run boot repair according to the instructions on the page.  Use the 2nd option described on the page to download using the ppa and when you run boot repair, select the Create BootInfo Summary option and do not try to make any repairs.  You will get a link when it finishes which you can post here and someone should be able to help.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2019-05-25
You didn't mention HOW you created the partitioned space to install Win8x, but if you used the Linux installer and let it shrink the existing Windows filesystem partition, that is almost certainly the source of the problem, as that has a nasty habit of corrupting Windows filesystems in the process.

If you have access to a working Windows PC, you can download and install the FREE version of Macrium Reflect -- and then use that to create a Boot Disk (or USB stick).  You can then boot your PC from that and use the option to repair the boot loader files.  That might get Windows booting again.

Good Luck

---

### Post by ghost-am on 2019-05-30
Thank's For your replay but,am i going to lose my data after using boot-repair?

---

### Post by Rubi1200 on 2019-05-30
Generally speaking, no it should not affect any data but as with any type of manipulation of system files there is always some risk.

I suggest you do the following:

boot the computer with a liveUSB and in test mode run the boot info summary (see first link in my signature).

Note, do not attempt to repair just use the option to create a report which you can post here.

Once we see that and have a much clearer view of the setup we can advise on the best steps to resolve the problem.

Thanks.

Edit: and oops I just saw that yancek already advised this in his previous post (therefore, please follow it)

---

### Post by yancek on 2019-05-30
We don't know what happened during your install of Ubuntu.  The purpose of running boot repair is to gather information which is why when you download and run it, be sure to NOT try any repairs and ONLY select the Create BootInfo Option.  You will get a link to post here and members will be able to view information on your system and hopefully help.  One common situation is that you mixed UEFI with Legacy installs and that will show in the bootinfo report.  There are a number of other possible problems which is why we need the info.

---

