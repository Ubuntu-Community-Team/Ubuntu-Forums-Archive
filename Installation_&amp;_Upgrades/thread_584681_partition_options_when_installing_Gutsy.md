---
title: "partition options when installing Gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by darden68 on 2007-10-21
Hello,

I'm trying to install Gutsy from the CD in a partition that I've left unused.
When I get to the partition options, I get :
- resize sda5 (which I don't want, that's my data partition)
- use whole disk (which I don't want either)
- manual partitioning

I go with manual partition, even if I would have prefered something I used to have with previous versiosn, "use a free partition (and make a /, a /home, a swap)"

in manual partition, I delete my unused partition, recreate a smaller one as / , then I want to create the swap but it's not possible because what's remaining of space (900MB) is caled "unused" and I have no option with it....

has it really gotten that bad, or am I not seeing something ??

Thanks in advance for your help..
Chris

---

### Post by Sef on 2007-10-21
1) If you already have a swap partition, you do not need a second one.

2) How much ram do you have?  If you have a gb or more of ram you really do not need a swap partition except under certain circumstances.

---

### Post by darden68 on 2007-10-21
Hi,

I don't have a swap partition, for now only Windows on my computer, I'm trying to change this.
I have 2GB ram but anyway, the installer won't let me go further if I don't create a swap (or at least i get a big warning message)
 
chris

---

### Post by logos34 on 2007-10-21
maybe you've reached the limit on primary partitions (4) after you create the /, and it won't let you make swap.  Or are you making partitions inside your extended?

Run fdisk in a terminal and post it:

**sudo fdisk -l**

---

