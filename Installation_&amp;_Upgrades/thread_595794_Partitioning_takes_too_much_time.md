---
title: "Partitioning takes too much time"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by AgrawalAshishS on 2007-10-29
Hi, I downloaded Ubuntu 7.10 DVD yesterday. I have rebooted my machine using it.
My initial thought about system was COOL. But then I see animation option for appearance is off by default it made me :(. I tried to have basic options selected but it asked me to reboot. So I believe I can't see effects in live CD :(. I had used Sabayon Linux and I really enjoyed those effects directly from live CD.

After live CD started I d'click on Install option (just to see how install process looks).
It completed first 3 steps in less than 30 seconds. Then comes the partition stuff, and it looks like
its going to take forever to get see partition options.

Let me give you my system info - 

I have HP dv6000 series laptop with WinXP MC installed.
CPU : Intel centrino duo
Ram : 2 GB
Display card: nVidia Geforce 7400
HDD: 80 GB SATA

Currently entire HDD is assigned to WinXP only.

After 45+ mins waiting for install wizard to show partition options - I found what took so much time!
It was due to my entire HDD is occupied with WinXP and Install process is looking to resize it. So it was reading my ENTIRE HDD and looking how much resize is possible.

Just for check I clicked on Manual option available in screen, and after 50% of progress same again waiting for partition to show up. This was frustrating, I remember in old Linux I can do partition stuff in 5 min at max and here it took me more then 2+ hours just to see my existing partition stuff.

As result - I Quit install and continue with WinXP.

I seriously think there is some really big mistake has been made by devs in this case. I see the cases where current partition thing is required, but I believe it should not be default - as its going to read entire HDD and take so much time.

---

