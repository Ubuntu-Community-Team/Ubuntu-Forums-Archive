---
title: "how to edit the os selector countdown"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Ubuntered on 2010-12-14
I installed Ubuntu 10.4 using wubi from XP. For some reason wubi didnt increase the countdown time on the windows os selector. My P.C. came with a recovery partition, so the os selector has always poped up on startup, but the timer was set to 5sec.(probably to avoid annoyance). Is there a way to edit this so I can have more time to select my option? This is the windows os selector and Ubuntu is on a separate(second) hard drive.Thank you.

Ubuntu version:  10.04 LTS- the Lucid Lynx
Windows version: Xp servicepack 2

Machine: Hp Pavilion a1677c

---

### Post by spcwingo on 2010-12-14
There should be file named boot.ini on the root of your XP partition.  In that text file you should be able to edit the timeout.

---

### Post by bcbc on 2010-12-14
Right click My computer, Properties, Advanced tab, Startup and Recovery, change timeout there. You can also edit boot.ini but you have to take off the read only flag first and if you mess it up... it won't boot.

---

### Post by Ubuntered on 2011-01-19
Thanks for the help, its very appreciated. I got sidetracked and forgot about joining this forum, but I'm back and glad I remembered :). I have not tried either of these fixes yet, but I will soon, and will be back to post the results. Sorry for not checking back sooner, thanks.

---

### Post by Ubuntered on 2011-01-28
> **bcbc said:**
> Right click My computer, Properties, Advanced tab, Startup and Recovery, change timeout there. You can also edit boot.ini but you have to take off the read only flag first and if you mess it up... it won't boot.

Worked perfectly, thanks again.:P

---

