---
title: "Why does swap space need it's own partition?"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Norman IV on 2011-08-09
I am using a Dell Inspiron 580 that I recently recieved as a gift. I wouldn't normally purchase a Dell, but I have no money and it my old computer was WAY past it's prime. After going through a miniature nightmare I now wonder how to create swap space for my ubuntu installation. I am running 10.04, 64 bit. I am having no problems, but I have no swap space. My computer is a new  -Intel i3- with 6GB of ram; so I assumed I could worry about getting it installed, then set a swap file later. As I said, it runs well, but i don't feel comfortable with ZERO swap space. 

When I installed Ubuntu I already had a problem because Dell had included 2 special partitions that are diagnostic and recovery. This didn't surprise me, but I want to make my system backup less than 100GB, so I shrank the "c:" partition to 100Gb and made the free space "storage":NTFS partition. After backing everything up (before messing with the partitions), I installed Ubuntu. Since I had created the backup that Dell asked me to (the very first time I turned the PC on) as well as my own system image I wasn't concerned.

Using GParted Boot disk I deleted the Dell "Recovery" partition and marked the "C:" drive (C:(OS)) as active. I used a Windows 7 install disk to "repair" the bootmgr problem. Had to run "repair" twice, but it worked. 

My question now is: why didn't Ubuntu installation say anything about a swap partition until I had already set up my partitions? I could easily give up a gig or two for swap space but I cannot make a swap partition unless I delete the Dell diagnostic partition (NOT the "recovery" partition; the other hidden one). I don't mind deleting the "recovery" partition because it is backed up, but I would prefer not to delete the "diagnostic/utility" partition, just in case. The 40MB is crap anyway.

It hadn't occurred to me that I would have trouble making swap space. I am used to windows (I am dual booting with GRUB BTW, if that matters) and the swap FILE doesn't need it's own partition. I understand why a separate partition would be better, but unless I can somehow create a logical/extended partition for swap, I need to know what else I can do.

 I believe Ubuntu is a better system for many reasons, but little things like this do puzzle me. I am no engineer, or software designer, but I don't understand why I wasn't given an option, such as: You cannot make another primary partition; would you like to use a virtual disk/file as your swap space?"...

Better than nothing, at the very least...

---

### Post by ajgreeny on 2011-08-09
Have a read through [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) which gives you all you need to know, and if you scroll down far enoughg, even tells you how to make a swapfile instead of a partition, useful if you already have four partitions on the disk.

---

### Post by YesWeCan on 2011-08-09
> **Norman IV said:**
>  I believe Ubuntu is a better system for many reasons, but little things like this do puzzle me. I am no engineer, or software designer, but I don't understand why I wasn't given an option, such as: You cannot make another primary partition; would you like to use a virtual disk/file as your swap space?"...
What you/it could have done was to make your remaining primary partition an extended partition to contain any number of logical partitions. Then you could go to town creating root, swap, home, etc...
It seems to me it always makes sense to contain all linux partitions inside an extended partition when dual booting with Windows. Ubuntu doesn't always take care of things nicely or explain your options to you.

---

