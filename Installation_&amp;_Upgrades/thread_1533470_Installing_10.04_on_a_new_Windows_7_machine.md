---
title: "Installing 10.04 on a new Windows 7 machine?"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by rlwpub on 2010-07-18
I'm getting ready to install 32 bit Ubuntu 10.04 on a new 64 bit Windows 7 machine. I want to install it so it will dual boot.

Do I need to re partition the hard drive before installing or will the Ubuntu install CD handle the re partitioning for me?

---

### Post by Old_Grey_Wolf on 2010-07-18
Here is a link to the Ubuntu documentation for installing a dual boot after Windows 7 is installed:  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Bluesan on 2010-07-18
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

Edit:

Oops, similar info as the post above ^, just a different link.

---

### Post by ST3ALTHPSYCH0 on 2010-07-18
Dunno if the above links mention it, but, when you resize your windows partition, make sure that the "round to cylinders" box is **unchecked**.

---

### Post by rlwpub on 2010-07-20
Thanks for the info. So what I am getting out of this is I can do it before installing Ubuntu or just let the install cd do it for me. Correct?

---

### Post by Old_Grey_Wolf on 2010-07-20
Just out of cautiousness, I always let Windows shrink Windows. I did have a problem using Gparted once to shrink Windows one time; however, I may have done something wrong like not defragging first.

---

### Post by ST3ALTHPSYCH0 on 2010-07-20
Yeah, Windows built in drive tool isn't too awful. However, it'll create dynamic partitions if you're not paying attention to what you're doing, and Linux doesn't understand those.

---

### Post by Mark Phelps on 2010-07-21
> **rlwpub said:**
> Thanks for the info. So what I am getting out of this is I can do it before installing Ubuntu or just let the install cd do it for me. Correct?

NO!  Letting the Ubuntu installer shrink Win7 partitions is asking for trouble.

You would do better using the Win7 Disk Management utility to shrink the Win7 OS partition and then installing Ubuntu to the "largest free space".

---

### Post by corona79 on 2010-07-21
unanswered - so moving to new thread[SIZE=4][/SIZE]

---

