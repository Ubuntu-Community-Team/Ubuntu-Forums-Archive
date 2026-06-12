---
title: "Live CD boot fault"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by MasterKosty on 2006-06-28
Hi,

I am a Windows XP user (32bit) , and i loved to test ubuntu.
I downloaded and burned the ubuntu Live CD ISO to a CD-R and booted on it
When i reach the "boot" menu (start/install ubuntu etc.) it's still ok , but then when i choose Start/install ubuntu (the first choise) it starts ....
First , it says mounting image etc. it continues , then it stops at configuring some drivers. it stays a while like that (5min+). then i get only a non-functional commandscreen....

Sorry for the poor English and poor descripting , but i am new to Linux

Please help me , Because Windows is getting kinda bored (after a good 10Year, what would you say)

PS.:
My PC Specs :

It's an HP pavillion 3035.be
Processor :AMD Athlon64 3200+
RAM: 512RAM
VideoCard: ATI Radeon X300se @ 256mb

---

### Post by m23 on 2006-06-28
Do you have an external CD or hard drive? For whatever reason I had to unplug my USB CD and harddisk to get it to work,

---

### Post by MasterKosty on 2006-06-28
Uhm , no , The HDD is internal , and the DVD Drive too (i have 2 of them , both internal , can only boot from one)

---

### Post by m23 on 2006-06-28
Try booting with "noapic acpi=off" .

When you get to the screen where you press enter to install Ubuntu, press escape instead, and type: live noapic acpi=off

---

### Post by Yochai on 2006-06-28
I just downloaded the image from differnet location after encountered this problem (seems like some of the location have spoiled image). Be sure that it is 697MB and that you burn it on 700MB CD (and not 650MB).

Good luck,
Yochai.

---

### Post by MasterKosty on 2006-06-28
Thx , but i downloaded the iso at ubuntu.com,
Sure it would be spoiled ? it was the 697mb

---

