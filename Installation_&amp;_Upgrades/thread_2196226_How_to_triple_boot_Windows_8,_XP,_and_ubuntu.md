---
title: "How to triple boot Windows 8, XP, and ubuntu?"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by americandollar22 on 2013-12-28
Before anyone asks, I've already searched the forums and I've researched this issue elsewhere, so I would appreciate it if everyone could simply answer my questions and help me figure this all out instead of simply telling me to use the search function or question my motives for or the necessity of creating a triple-boot drive, but I guess I'll go ahead and do it anyway just to keep it from happening.

I've finally got some extra money to dole out for a 1 TB external hard drive, and I'd like to be able to triple boot from it. Ideally, I'd like to have Windows 8 take up the partition with the greatest amount of space, as it will be used for manually backing up the docs and files I have on my windows 7 laptop. I might play around with having a fourth partition with the majority of the space (750 gb to be exact) to be used as a spot to store an identically sized image of my laptop's hard drive. I'd like to have ubuntu as a failsafe OS since it can manage all sorts of drives and partitions. Windows 7 came preloaded onto my current laptop so I didn't want to mess around with partitions to install ubuntu at the time, especially since I currently have nothing large enough to backup my entire installation and since I don't have an install disc for 7. I need XP to be able to run some older software, and I prefer to test with it.

Ideal partition order: XP (20 GB), Windows 8 (950 GB), Ubuntu (30 GB). I'm not sure if this particular order works or not, and I'm also not sure if I can swap the order.

Like I said, I've done my research, so here's what I know (or at least what others have said), and if anyone can give me a confirm/deny on each of these that would be great:

1. It's possible to multi-boot these 3 OSes in the first place.

2. You can multi-boot from a USB 2.0 hard drive, although read/write speeds might not be as good as an internal.

3. I've read some stuff about the order of installation affecting the master boot record for windows. These are the conclusions I've come to in this area:

a. You have to install Windows XP first and on the first partition because it requires a primary partition, otherwise its MBR will prioritize itself over the other bootloaders and cause serious problems.

b. Vista, 7, and 8 are all programmed to incorporate XP's bootloader so that you can multiboot several versions of windows from the same drive.

There are some things I don't know. I'm just getting started with using Linux, this is part of the reason why I'm posting it on the ubuntu forum, and I don't fully understand how Linux interacts with previously installed versions of Windows. I know that it runs on its own bootloader, but I'm not sure what the consequences of that are on startup.

Finally, I don't know how all of this will show up on my laptop or any other computer that I would use to start this triple-booting hard drive on. I know my PC can boot from USB, but will my BIOS be able to detect the three options I would have on the different partitions, and would there be any way I could label the options in the BIOS so that I know which OS I'm booting from? I'm also confused about whether or not my BIOS will only show the hard drive itself and then once that starts I'll see a separate bootloader that lists the 3 partitions.

If any of this is confusing to anyone I'd be happy to break it down. Thanks in advance for the help.

---

### Post by Mark Phelps on 2013-12-28
You won't be able to boot either XP or Win8 from an external drive.

The order of install I recommend are:
1) WinXP
2) Win8
3) Ubuntu

Yes you CAN multiboot all three -- but with a single hard drive, you will get a GRUB menu that only lists Windows and Ubuntu.  When you select Windows, you will get a second menu that allows you to select from Win8 or Older version of Windows.  That's because the GRUB entry only points to the Windows boot loader -- and its menu is where you choose the Windows version.

---

### Post by americandollar22 on 2013-12-28
> **Mark Phelps said:**
> You won't be able to boot either XP or Win8 from an external drive.

The order of install I recommend are:
1) WinXP
2) Win8
3) Ubuntu

Yes you CAN multiboot all three -- but with a single hard drive, you  will get a GRUB menu that only lists Windows and Ubuntu.  When you  select Windows, you will get a second menu that allows you to select  from Win8 or Older version of Windows.  That's because the GRUB entry  only points to the Windows boot loader -- and its menu is where you  choose the Windows version.

Why wouldn't I be able to boot them from an external drive? Would I be able to run Windows To Go from the external drive, or is a flash drive absolutely necessary? Also, doesn't BartPE make it possible for windows xp to do this?

---

