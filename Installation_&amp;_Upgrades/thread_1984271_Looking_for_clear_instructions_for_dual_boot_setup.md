---
title: "Looking for clear instructions for dual boot setup with windows in 12.04"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by david.karr on 2012-05-21
I have a desktop with Win7 installed.  I'd like to keep that there and dual boot with Ubuntu 12.04.  I've tried to go through the documentation and various tip articles, but I can't find any really clear instructions about how to set this up for dual boot, with 12.04.  I found somewhat vague instructions in the "official" instructions, and I found various "tip" articles that are several years old, for older releases.

I'd really like to make sure I don't mess this up, if I only have  unclear instructions to go on.

Can someone point me to something I've missed that goes through this in detail?

---

### Post by mrpot on 2012-05-21
> **david.karr said:**
> I have a desktop with Win7 installed.  I'd like to keep that there and dual boot with Ubuntu 12.04.  I've tried to go through the documentation and various tip articles, but I can't find any really clear instructions about how to set this up for dual boot, with 12.04.  I found somewhat vague instructions in the "official" instructions, and I found various "tip" articles that are several years old, for older releases.

I'd really like to make sure I don't mess this up, if I only have  unclear instructions to go on.

Can someone point me to something I've missed that goes through this in detail?
Hi david, in the past i have installed many times ubuntu distro's with windows,
now is very simply, i think there are two possibilities,
one:
download iso of pangolin, write it correctly inside an usb pen
start your machine with the "boot usb "option at the bios,
the ubuntu 12.04 start some window dialog, you can try distro or you can install,
if you select install, other window dialog show the precedent operating system fonunded on your hard drive, you can choose "install near wondows 7" that's all.

but in any case you can choose the second method, 
the wubi installer,
but please look at this page :
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

i hope this is useful for you, and don't forget to listen many voice about your question,
i'm not using windows after vista,
don't discard ubuntu ):P

sorry for my english..

---

### Post by darkod on 2012-05-21
Few important things to do first:
1. Branded machines these days often ship with all 4 primary partitions used. Open windows Disk Management and confirm how many primary partitions you have. If it's 4 you will have to delete at least one so the ubuntu partitions can be created.
2. Even by deleting one partition, you might still need to shrink the C: partition if it's taking almost all of the hdd because there will be no space for ubuntu. If you are doing this, do it in Disk Management too. NEVER do it during the ubuntu installer using the "slider" to split the disk between windows and ubuntu. Bad idea.

Windows likes to be restarted few times after the shrink and that's why it's best to do it separately.

Once that is taken care of, you can install either using one of the auto methods or the manual which I recommend. It gives you most control, and you can install with a separate /home partition which is better.

Also, I don't recommend wubi since it's like a virtual install inside windows, go for the proper dual boot.

Check the partitions number first, and make unallocated space for ubuntu (not belonging to any partition), and then if you need more detailed help about ubuntu just ask. I have no detailed instructions at hand, maybe this.
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by vasa1 on 2012-05-21
> **darkod said:**
> Few important things to do first:
1. Branded machines these days often ship with all 4 primary partitions used. Open windows Disk Management and confirm how many primary partitions you have. If it's 4 you will have to delete at least one so the ubuntu partitions can be created.
2. Even by deleting one partition, you might still need to shrink the C: partition if it's taking almost all of the hdd because there will be no space for ubuntu. If you are doing this, do it in Disk Management too. NEVER do it during the ubuntu installer using the "slider" to split the disk between windows and ubuntu. Bad idea.

^^^^
**This is very, very important**. I heard that HP PCs are famous for stuffing all available partitions. Then of course, some of us like to "organize" things into separate partitions, keeping **C** for original programs, **D** for other data, and **E** for stuff like music not knowing that the boot sector (?) is counted as a partition.

I sincerely wish that Ubiquity warns users to check this aspect first. Instead, Ubiquity just drops the "install alongside" option.

> **darkod said:**
> 
Windows likes to be restarted few times after the shrink and that's why it's best to do it separately.

It may not be a total waste to defrag the whole disk after wiping off extra partitions and shrinking **C** to make free (aka unallocated) space available.

> **darkod said:**
> 
Once that is taken care of, you can install either using one of the auto methods or the manual which I recommend. It gives you most control, and you can install with a separate /home partition which is better.

I'm not sure that a newbie should take the manual route. A more confident user sure, but a newbie would do just fine with the auto method.

> **darkod said:**
> 
Also, I don't recommend wubi since it's like a virtual install inside windows, go for the proper dual boot.

Absolutely.

---

### Post by darkod on 2012-05-21
> I'm not sure that a newbie should take the manual route. A more  confident user sure, but a newbie would do just fine with the auto  method.

And how would a user get more confidence if they never try partitioning and planning of their disk layout.

The windows way of taking the whole hdd in one partition definitely doesn't help.

Planning to install an OS is the right moment to get informed about partitioning your disk in the best way.

---

### Post by vasa1 on 2012-05-21
> **darkod said:**
> And how would a user get more confidence if they never try partitioning and planning of their disk layout.

The windows way of taking the whole hdd in one partition definitely doesn't help.

Planning to install an OS is the right moment to get informed about partitioning your disk in the best way.
The way I see it is that it is a big step to just start using Ubuntu and getting comfortable with it.

**I'm not sure that I implied in any manner whatsoever** that "they **never** try partitioning and planning of their disk layout."

---

### Post by wilee-nilee on 2012-05-21
> **darkod said:**
> Few important things to do first:
1. Branded machines these days often ship with all 4 primary partitions used. Open windows Disk Management and confirm how many primary partitions you have. If it's 4 you will have to delete at least one so the ubuntu partitions can be created.
2. Even by deleting one partition, you might still need to shrink the C: partition if it's taking almost all of the hdd because there will be no space for ubuntu. If you are doing this, do it in Disk Management too. NEVER do it during the ubuntu installer using the "slider" to split the disk between windows and ubuntu. Bad idea.

Windows likes to be restarted few times after the shrink and that's why it's best to do it separately.

Once that is taken care of, you can install either using one of the auto methods or the manual which I recommend. It gives you most control, and you can install with a separate /home partition which is better.

Also, I don't recommend wubi since it's like a virtual install inside windows, go for the proper dual boot.

Check the partitions number first, and make unallocated space for ubuntu (not belonging to any partition), and then if you need more detailed help about ubuntu just ask. I have no detailed instructions at hand, maybe this.
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

+1
Excellent advice from one of the best helpers on the forum in these areas. ;)

---

