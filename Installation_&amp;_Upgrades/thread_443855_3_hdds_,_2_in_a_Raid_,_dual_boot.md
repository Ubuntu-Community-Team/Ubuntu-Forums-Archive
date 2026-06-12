---
title: "3 hdds , 2 in a Raid , dual boot"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by fenderog on 2007-05-14
Hello everyone , 
I tried to find an answer by searching but I coulnd't. I apologize if this is already answered.


I have 3 HDDs , 1 80gb , and 2 120GBs

I have a windows XP on the 80g

and I have a raid on the other 2 drives , that turns them into one drive of 240gb 

I want to install desktop ubuntu on my raid drive and have a dual boot with XP 

but when I run the live cd , ubuntu doesn't recognise my RAID

I'm using a silicon image PCI adapter , and its during boot time , I already have the raid setup.(i can boot from it , if I had an OS installed on it)

Can anyone give me some specifics on how can I install ubuntu on my raid drive while having a dual boot ? 

Thank you very much

---

### Post by zPacKRat on 2007-05-14
you need to install DMRAID via APT so that Ubuntu will see your SOFTWARE raid array. search for it on these boards and you should find some good howto's on how to edit your boot loader to boot to the array.

---

