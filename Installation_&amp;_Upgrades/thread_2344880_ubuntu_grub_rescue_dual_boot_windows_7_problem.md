---
title: "ubuntu grub rescue dual boot windows 7 problem"
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by chirazou23 on 2016-11-28
Good evening
I have a problem that I could not solve.
 I tried all the tutorials that exist on the internet without results ..
So I have the famous grub problem, why? Since I formatted by fault the disk of windows 7 on ubuntu ... on ubuntu I formatted 
the disk of windows 7 so I could not start with windows (it asked me to put the cd of windows ..ect ) Anyway what I did is try 
to recover the data I lost while formatting .. i did it with testdisk..but when i did the reboot --->grub mood.
I tried the solutions set root set prefix.. on the good partitions (I did ls to know) but i had the unknown file problem when tipping insmod normal
And I also boot ubuntu on usb to try solutions on terminal like boot repair..but always the grub

I want to go back to the dual boot that I had 
or even if I lose ubuntu I have no problem as long as I can recover all the data on windows because
 I can reinstall ubuntu after after all there is no important data on it.. but data on windows are sooo important ...help please

---

### Post by yancek on 2016-11-28
If you formatted the entire disk on which you had windows then it is gone.  If you can't get it back with testdisk I'm not sure what else you could try.  If you had data you wanted on windows I'm not sure why you would have formatted that partition?

Who/what asked you to put the CD of windows in?

You mention boot repair.  It has an option to Create BootInfo Summary and running it again and posting a link to that output would be your first step in trying to get help here.

---

### Post by oldfred on 2016-11-29
As Yancek suggests run the Summary report from Boot-Repair.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you have overwritten the NTFS partition, you want to STOP using system on hard drive. Every use overwrites more data. While you cannot recover all data, you may be able to get some back.

But lets see what partitions are still on drive first.

---

