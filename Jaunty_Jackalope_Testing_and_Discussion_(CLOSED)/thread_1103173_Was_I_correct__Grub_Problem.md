---
title: "Was I correct ? Grub Problem"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BGFG on 2009-03-22
Hi,
I installed the daily as of friday but on booting, got an 'Error 15' so I went through the install process again, this time pointing the install at my ext4 / partition and my ext3 /Home, opting not to format. 

On the final page in advanced options, i selected to install grub on sdc (the installation drive in question) and not on dev/sdc5 my '/' partition.

Now however, once i select Jaunty Development Kernel from the menu, the next dialogue says 'starting up' and there is about a 10+ sec interval before GDM appears.

Were my actions correct ?

---

### Post by cariboo on 2009-03-22
If it only takes 10 seconds before gdm shows up, I would say you did it right. My boot time has regressed to 34 seconds since kernel 2.6.28-10 came out. :(

Jim

---

### Post by BGFG on 2009-03-22
Thanks a lot for the response, i was concerned that i may have affected grub's performance. sorry to hear about the boot increase though. With intrepid, I used 'Start Up Manager' to set my kernel of choice and set the delay to zero.

Also, with what i think is the latest daily, I got the -11 kernel.

---

### Post by cariboo on 2009-03-22
My bug report was rejected, because the kernel dev decided that it is a BIOS problem, even though it didn't show up until 2.6.10. Previous to that I was geting boot times around 20 seconds.

Jim

---

