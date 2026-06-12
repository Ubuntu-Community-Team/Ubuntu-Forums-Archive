---
title: "Planning Win7/Ubuntu 10.10 dual boot, SSD &amp; HDD"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by gstilma on 2011-01-20
Hello:

I'm currently dual booting XP and 10.04 on an old build. I'm planning & collecting parts for a new build using a 60gb SSD as boot drive and a 500gb HDD for documents and anything /home. I want to dual boot Win7 and 10.10 and, after some research here and elsewhere on the interwebs, have the following steps/partitions in mind:

1. Install Win7 on a 40gb partition of the SSD and tweak it (move paging file to 100gb NTFS partition on HDD, no hibernation, etc.)

2. Install Ubuntu root on remaining 20gb of SSD, /home on remaining 400gb ext4 partition of HDD.

Of course, Win7 gets installed first to get GRUB to work correctly. I don't planning on using Win7 much (just Netflix & a few other things), so I figured 40gb was enough of the boot drive.

Can anyone tell me if there are any apparent problems with this plan? What about swap -- some say that double the system memory isn't really necessary. I'll have 4gb DDR3, so maybe I could have just, say, 2gb swap on the SSD?

Really, I'd just love to read any comments/suggestions. Thanks.

---

### Post by gstilma on 2011-01-26
Anything? Anyone?

---

### Post by psusi on 2011-01-26
With 4 gb of ram, you need 4 gb of swap in order to hibernate.  If you don't care about hiberation, you probably don't need any swap with 4gb of ram.

---

### Post by Logiwonk on 2011-01-26
Sounds like a solid install plan to me...although 20 gb for Ubuntu root sounds like way more than necessary if you're putting home on the other HDD, depending on how much in terms gb of programs you're planning on installing to Ubuntu.

---

### Post by gstilma on 2011-01-26
Thanks, psusi -- something to consider. I don't care about hibernation, so I'll probably leave off swap altogether.

Logiwonk, so would 10 or 15gb do it for root?

---

### Post by Logiwonk on 2011-01-26
I've been using Mint (flavor of Ubuntu) for a few months so don't take my reply as gospel.  From what I understand root is where your program files normally hang out (in /usr I think) whereas the home usually has most of your documents, music, downloads, etc.  How much you allot for the root of linux would then depend on how much space you need for programs.   The only reason I mention it is that in a windows system 40 gb can go fast even if you're really paying attention to C: usage.  Of course, I find it much easier to run programs off of my second hard drive in windows compared to linux because I'm more familiar with windows.

Question for experienced users - if you have root on one drive and /home on the other can you setup a program to live on the /home drive and run in linux?

---

