---
title: "Slow boot time of kernel 2.6.17-11-generic (vs. 2.6.15-23-686)"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by anchois on 2007-04-05
Hi all,

I've a problem on my Edgy laptop (Sony VAIO FS-315E).
I've recently upgraded the old Dapper kernel (2.6.15-23-686) to the new Edgy generic kernel (2.6.17-11-generic) for a better madwifi support.

On the 2.6.15, I had a boot time of 50 seconds but with the new one, it takes
2min15 (which is not "taking ages", but not really an improvement).

I don't have a clue of what is taking so long.
I read many post and the removal of "quiet" in /boot/grub/menu.lst help a little.

Looking at the bootchart graphics, my conclusion is that udev script is THE problem
but I'm not sure.

Could you help me on that problem ?

Thx

ps: I put the link to the two relevant bootcharts:

first one is the 2.6.15 kernel (png of 187 ko)
[link: edgy-20070326-5_2.6.15.png]("http://anchois.free.fr/bootchart/edgy-20070326-5_2.6.15.png")

the other is the 2.6.17 (png of 239 ko)
[link: edgy-20070405-3_2.6.17.png]("http://anchois.free.fr/bootchart/edgy-20070405-3_2.6.17.png")

pps: I have change nothing else except the kernel.

---

### Post by anchois on 2007-04-18
Answering to myself

the add of "noapic nolapic" on the grub/kernel line did the trick:
no more latency on boot.

Now, my boot time is 45s

(still to see what's not working ;)

---

