---
title: "How do I know which partition to put Grub on?"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by wardrich on 2010-03-21
Let me start off with a screenshot here...

[[IMG]http://img144.imageshack.us/img144/2482/partitiontree.th.png[/IMG]](http://img144.imageshack.us/i/partitiontree.png/)

Here's the breakdown:
/dev/sda1: This is my main data drive.
---
/dev/sdb1: This is where I have XP installed
/dev/sdb5: Swap (obv)
/dev/sdb6: This is where I'd like to put Ubuntu.


Here's the questions:
1. How do I know where ntldr is already installed so I can replace it with grub?

2. Why does it jump from sdb1 to sdb5?  Is there a way to fix this indexing?  Is it an issue to be worried about?

Additional Details:
I've tried installing 9.1 a few times now, and I've tried putting grub on a few different partitions now (but I can't remember which...).



Thanks for the help guys, it's been a while since I've been in Linux and I'm really looking forward to trying out 9.1.  You guys have always been able to help me in the past, so I'm hoping the trend will continue.  lol.

Thanks again
-Richard


[update]
When I go to the list of places to put GRUB, sdb1 is listed as "WindowsNT/2000/XP (loader)".  I'm gonna take a chance and install it there.

---

### Post by gordintoronto on 2010-03-21
I've never worried about either of the questions you raised, and my dual-boot system works just fine.

However, there is something I have done which is not default: set up one partition for / and another for home. That way I can install (not upgrade) the next version without any change to my data.

I would also give / more space than you have reserved for it, at least 6 GB. If it fills up, it is a disaster, and all your programs and log files go there.

---

### Post by howefield on 2010-03-21
> **wardrich said:**
> How do I know where ntldr is already installed so I can replace it with grub?

Your install of Ubuntu will take care of where grub should be installed. I'd expect it to get it right.

> Why does it jump from sdb1 to sdb5?  Is there a way to fix this indexing?  Is it an issue to be worried about?

You can have only four primary partitions on your disk which would be numbered sdb1, sdb2, sdb3, and sdb4.

To create more than 4 partitions usually means that you would need to make an extended partition within which you would have logical partions, logical partitions would be numbered from sdb5 upwards.

Even if you had only one primary partition and one logical partion on your disk, the logical would still be numbered as sdb5.

Your sdb5 and sdb6 are logical partitions inside an extended partition.

Load up gparted from the live cd to get a graphical view of your disk, it may make sense when viewed like a "picture". 

Not sure if I have explained very well, but perhaps you get the idea. :)

---

### Post by wardrich on 2010-03-21
Thanks for the help guys, it took me a while to install b/c a few of my installs came up with copy errors... but I ended up putting grub on that "nt/2000/xp (loader)" partition and it works :D

---

