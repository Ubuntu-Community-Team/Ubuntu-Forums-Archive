---
title: "dual-boot XP and kubuntu 9.10 with Lenovo's RnR"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by drixomanbeta on 2009-11-17
Hi
 
I'm trying to dual-boot windows XP and kubuntu 9.10 and I think it makes sense to separate the so called boot and system partition in windows' term (i.e. having \Windows on one partition and the boot.ini, ntldr stuff on another)... But I can't figure out how to separate them...
 
Since I'm dual-boot I am aware XP should be installed first...what I did was installed it onto the second partition while at the partition screen in the XP install and left a smaller NTFS partition as the first one on the list.  Not sure if that would cause the boot and the system to separate...(it seem so since the boot-related file is on C:\  while the Windows directory is on D:\)
 
However I install Rescue and Recovery on this Windows and tried to boot into the RnR workspace through the Think button but it notes NTLDR is missing...Windows still boot normally on startup (to me the workspace was probably not installed to the right place perhaps? ; shouldn't it be in like a new service partition called S:\ or something? maybe it got installed into C:\)   I read somewhere that RnR workspace has it's own bootloader and write into the MBR or something...
 
since I'll also be installing kubuntu the bootloader will surely get messed up again by Grub...so that might completely screw up everything on Windows side...
 
I have no idea what to do to make kubuntu, windows, and RnR all exist in peace....
 
I'm not very familiar with booting and disk management but any help would be appreciated; I'll try to follow step if they are very specific...

Thanks

---

### Post by drixomanbeta on 2009-11-17
geez...i can't get any response...
bump...

---

### Post by drixomanbeta on 2009-11-18
bump..come on people...

---

### Post by drixomanbeta on 2009-11-20
bump...

---

### Post by darkod on 2009-11-20
What is RnR? Restore & Recovery? You want to keep some type of recovery partition, and making sure it doesn't get deleted?

I don't understand what you want to achieve, otherwise I could give you some advice. :)

---

### Post by drixomanbeta on 2009-11-20
sorry I wasn't explicit about that..it was in the tags...

I am using Thinkpads so "Rescue and Recovery" (RnR) is one of Lenovo's ThinkVantage software stuff...

I don't expect RnR to cooperate with ubuntu but basically this is about how to get the RnR to works with XP, and hopefully ubuntu's boot loader won't screw that up...

right now i'm having trouble figuring out why does RnR don't work with my particular partition scheme...

---

