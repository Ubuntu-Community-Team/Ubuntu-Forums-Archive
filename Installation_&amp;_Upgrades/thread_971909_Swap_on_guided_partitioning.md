---
title: "Swap on guided partitioning"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by vtslimik on 2008-11-05
Hi

If i choose "Guided" partitioning, what is the swapsize going to be? Is  it any major disadvantages with using Guided? I know it is good to have a /home partition when installing or upgrading to new version of ubuntu. But what about the swap?

I have 140 GB free (1 disk only). Need to use somewhat ~80 to Windows XP and rest to Ubuntu. Any suggestions?

---

### Post by taurus on 2008-11-05
It depends on how much RAM you have.  Swap space of 1GB or 2GB would be plenty.

---

### Post by vtslimik on 2008-11-05
ok. But how large will the swap be if i choose "Guided" ? Have 4g ram

Or do I get a question about that?

---

### Post by tarps87 on 2008-11-05
You have to set up a partition manual, with 4GB you should not need a swap partition for 'normal' use but if you plan to hibernate you should set it to at least 1 1/2 times the size of your RAM, in your case 6GB. The swap partition is used for paging and when hibernating all the data/bytes in your RAM will be stored into the swap partition, this is why it needs to be bigger than your RAM.
You can resize the partition afterwards using the live cd if you want to so it doesn't have to be a permanent decision.

---

