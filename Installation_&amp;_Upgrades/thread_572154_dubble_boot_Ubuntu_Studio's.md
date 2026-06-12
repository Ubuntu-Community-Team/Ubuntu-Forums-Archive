---
title: "dubble boot Ubuntu Studio's"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by almancora on 2007-10-10
my distro: Feisty

As I started Rosegarden, I got A notice, the kernel timer is set to low. 
I found some info on Ubuntustudio's, and so I was wondering how I could dubble boot this with feisty. I m a complete nobody on partitions, dubble boot. I even don't now If I my disk is divided in partions at the moment. 

Can anyone give my some information (or a good site) on how partitions work in linux, how dubble boot works, what it does? Ok, you can just give me a name of a dubbleboot program, but I want to know how all of that works, so in the end after more experience maybe  I'll be able to anwser my on problems.

I also heard of DeMuDi. What are the avantages, disadvantages against Ubuntu studio's?

---

### Post by Herman on 2007-10-10
Here's a good site about dual booting [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php"), by aysiu.
You should find all kinds of pages in that site about how to use the Ubuntu Live CD to install with and information on what partitions you'll need.

I personally recommend not making too many partitions, all you need is one partition for each Ubuntu and one swap area, Most people will tell you you should consider making extra partitions so you can have a separate /home partition for Linux. Most dual boot sites assume you're dual booting between Windows and Linux, but if you're dual or multi booting more than one Linux I think you'll find it too messy and confusing to make separate /home partitions. Just keep it simple, simplicity is beauty.

Another site is in my signature links (at the bottom of this post).

Probably if you already have Ubuntu Feisty installed your disk would be divided up into one big partition for Ubuntu and a small swap area of less than 1 GB.
You will just need to resize your big partition to a smaller size (if there isn't too much data in it), to make room for a new partition for installing another Ubuntu it, probably 5 GB would be necessary or 10 or more would be better.

Your new install of Ubuntu will offer to install GRUB boot loader to MBR for you before the installation finishes, and it should tell you that it has detected your existing Ubuntu install, so it will add that to your boot menu automatically, there will be no need for you do worry about doing it manually.

Basically that's about all there is to it, you'll find it quite simple once you try it. 

Sorry, I haven't tried DeMuDi or Ubuntu Studio, maybe someone else can provide an answer to that question.

Regards, Herman :)

---

