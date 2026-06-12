---
title: "Ubuntu/Windows sharing datastore with LVM/RAID"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Plecebo on 2006-10-14
I have a problem that I could use some advice on, first some background. 

My machine has Windows currently installed on a RAID 0 array (nforce4 software raid array that will not really work in linux very well) that spans 2x250gb sata hard drives. This works well, but i'm currently "linuxless" which is becoming more blasphemous in my mind. 

What I would like to do? 

I want to move to primarily linux, but because of work needs just can not give up windows 100%. Ideally I would want something like 50GB each for my windows partiiton and my linux volume, and the remaining 400GB (spanning 2 hd's) as a shared media store partition that both windows and linux can access. 

The problem I am running into is getting windows to read and write to the LVM, i cant seem to find any good solutions to this at all. There are applications that allow access, but they are standalone apps and not "incorperated" into the OS so for example you can not use windows explorer to view the drive. 

I would like something like ext2IFS that works with LVM. 

my other last resort option is to pick up one of the 3ware hardware sata raid cards and use that instead, but i'm still not sure that the hardware raid solution will solve my problem. 

Can anyone give me some pointers?

---

