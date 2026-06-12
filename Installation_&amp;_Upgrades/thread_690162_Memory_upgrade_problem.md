---
title: "Memory upgrade problem"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by b4rt on 2008-02-07
Hi all!

I am not new to linux, but I am quite new to ubuntu. I love it.
I dual boot with ubuntu 7.10 and windows XP

I upgraded my memory from 2 GB (2 x 1GB) to 4 GB (4 x 1 GB now)
When I boot ubuntu, boot time is normal, but once login screen starts, things get VERY slow...
booting into the graphical user interface (GNOME) takes over 5 minutes to load entirely. When my computer only had 2 GB of memory, it booted in less than 40 seconds...
I removed one of the memory bars (so now I have 3 GB of memory) and ubuntu is running fine...

What am I doing wrong? Any help would be greatly appreciated...

Kind regards,

Bart Goyens, Belgium

---

### Post by peterbrewer on 2008-02-07
What processor and such do you have.  It is possible your mother board is having difficulty handling 4GB of RAM.

---

### Post by b4rt on 2008-02-07
I have an Intel Celeron 3.2 GHz and an MSI Neo2 motherboard, which should be capable of handeling 4 GB of memory.

Also, when I boot with 4 GB of memory, /var/log/Xorg.0.log shows a lot of memory related errors (not right now, because now I only use 3 GB of memory)

Thanks for the quick reply,

Kind regards...

---

### Post by Partyboi2 on 2008-02-07
have you tried doing a memory test?

---

### Post by b4rt on 2008-02-07
yes, I have tried a memory test, it gives no errors, the memory itself is fine...

---

### Post by Carl H on 2008-02-07
I had problems getting 7.10  to run properly with 4Gb of RAM installed.

Check that you have the right combination of memory. Are you trying to run it as single channel or dual channel?

---

### Post by b4rt on 2008-02-07
what is the difference?

now I have 3 sticks of 1 GB installed, and it works fine, but I would like to install the 4th also. I tried several combinations, but they do not work...

Thanks for replying...

---

### Post by Sidewinder1 on 2008-02-07
Perhaps the 'forth' stick is bad. Have you tried swapping it with one of the other three?

---

### Post by Carl H on 2008-02-07
> **b4rt said:**
> what is the difference?

now I have 3 sticks of 1 GB installed, and it works fine, but I would like to install the 4th also. I tried several combinations, but they do not work...

Thanks for replying...

4 x 1Gb of RAM in "dual channel" mode actually gives you 2Gb of RAM. Each pair of 1Gb DIMMS acts as though it is one 1 Gb DIMM, but twice as fast as usual. 

You need matched pairs of DIMMs to use dual channel, so with three installed you can only run it single channel.

---

### Post by b4rt on 2008-02-07
Thank you all for your replies.

The pairs match. The 4th stick isn't bad, I went to the store to change it, and they did. I can also swap them all. They are all fine.

Aren't there any kernel parameters that I am forgetting?

Kind regards...

---

### Post by b4rt on 2008-02-07
Please help me with this...

---

