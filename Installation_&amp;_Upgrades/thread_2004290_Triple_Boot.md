---
title: "Triple Boot"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by bheemamahesh on 2012-06-15
i want to install windows Xp, Server 2008 & ubuntu to my PC

i tried it before but it was not successful

can anyone please guide me

Thank "U"

---

### Post by Cavsfan on 2012-06-15
You will need to install xp and Server 2008 first.
Then install Ubuntu and select "something else" at the bottom when it comes to asking where to install it.
You can set Ubuntu up on 2 logical partitions. One about 2GB for swap and the rest of the space you have allocated for Ubuntu to / ext4.

---

### Post by bheemamahesh on 2012-06-15
thanX for the quick reply..

what abt /boot partition
where should i install grub loader

---

### Post by Cavsfan on 2012-06-15
> **bheemamahesh said:**
> thanX for the quick reply..

what abt /boot partition
where should i install grub loader

It should take care of itself if you install Ubuntu last.
Then after you get them all bootable take a look at the How to in my sig.
I am tri-booting Windows 7,  Lucid Lynx 10.04 and Precise Pangolin 12.04.
There is a picture of my current grub screen on the last post of the How to.

Edit: all you need is a swap and a / (file system). No need for /boot or anything else.

---

### Post by bheemamahesh on 2012-06-15
ok..but what to do if i delete one of my windows partition and add install another windows after successful triple boot

---

### Post by Cavsfan on 2012-06-15
> **bheemamahesh said:**
> ok..but what to do if i delete one of my windows partition and add install another windows after successful triple boot

You will be back on here asking for help. Installing windows after Ubuntu causes problems.
But, I am sure there is some knowledgeable enough person on here to sort it out.
Just not me.

---

### Post by bheemamahesh on 2012-06-15
sorry...i just want to know

is there any way that grub loader didn't corrupt if delete any Partition

any thnX for ur time :)

---

### Post by Cavsfan on 2012-06-15
> **bheemamahesh said:**
> sorry...i just want to know

is there any way that grub loader didn't corrupt if delete any Partition

any thnX for ur time :)

Not sure, you could check drs305's grub 2 basics thread and if you don't find an answer you could post a question there.
But, I would wait until something does happen instead of what if because that is basically impossible to answer.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by bheemamahesh on 2012-06-15
Thank "U"
i'll reply here after successful triple Boot

---

