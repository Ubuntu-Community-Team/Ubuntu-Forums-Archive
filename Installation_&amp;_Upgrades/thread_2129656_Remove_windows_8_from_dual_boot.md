---
title: "Remove windows 8 from dual boot"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by mm320 on 2013-03-26
I've been using Windows 8 as my main OS but dual booted(with something called grub i think) ubuntu from time to time. I've been having issues with windows and i can't get it to boot correctly so i saw this as the perfect time to make the full switch to Ubuntu. How can I fully install Ubuntu and remove my Windows 8 partition? I've attached a picture of my list of partitions, maybe it'll help. Thanks for all the help!

---

### Post by darkod on 2013-03-27
The main issue is whether you have data to recover from windows or not?

If you do, you will have to boot your ubuntu and copy the data to some external disk.

Then simply boot the computer with the ubuntu cd, and in the install menu you can use the option saying something like Replace Windows, or Use Whole Disk ,etc. That option will delete all partitions, including your current ubuntu, and install ubuntu taking the whole disk with the standard root + swap setup.

If you want a specific setup, like having separate /home partition which is a good idea, you will have to use the manual install option (Something Else). That will allow you to create your partitions manually. That way you also have exact control on the partition sizes.

---

