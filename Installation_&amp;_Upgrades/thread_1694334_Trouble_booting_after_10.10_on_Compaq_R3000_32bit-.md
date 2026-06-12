---
title: "Trouble booting after 10.10 on Compaq R3000 32bit- dmesg attached"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by buddhaflow on 2011-02-24
Hi! I have been having a very frustrating problem.

It started when I tried to install Kubuntu 10.10. It booted OK from the CD, but after I installed it, it wouldn't boot. It would hang showing "floppy: no floppy found". I think the next part is either initializing swap or disks.

No matter what, I couldn't it to boot.

So, I installed with Xubuntu. it worked great, and booted fine a few times. Worked a couple days.

But just today, after updating to the new kernel, it won't boot at all. It gets stuck at the same place!

It does this even if I go back to the old kernel on the boot list.

When I boot into recovery mode, SOMETIMES it will boot. Actually, just once. All other times, it failed to boot even in recovery. I attached the dmesg from one of these boots.

I booted into a puppy partition, and fsck -f my other partitions. It reported no problems.

Could it be a hard drive problem? I don't hear anything from the drive, but it's getting old and I was planning on replacing it soon anyhow.

My computer is a Compaq R3000 AMD64, but I'm running the 32 bit OS.

Any help is much appreciated! I am in the middle of a major project, and I really, really need my computer to be working 

Thank you!

Sasha

---

### Post by Baji on 2011-02-24
I am having the exact same problem,

Presario R3000 AMD, ubuntu 10.10

It will boot 1 out of 4 times I try to start.

It just hangs after init.d/bottom or something like that. I  hard reset it,

grub loads, but the booting only finished 1 out of 3/4 times.

---

### Post by buddhaflow on 2011-02-28
Bump?

I hate the factthat I will never be able to upgrade Ubuntu again...I really like 10.04, but don't want to be stuck with it for the next several years, I was so excited by 11.04.

Does anyone have any advice to what I might check out? I am totally baffled, and the Compaq R3000 was a very popular line of laptops...

---

### Post by Baji on 2011-03-24
After some more trying around --- i installed ubuntu 11.04 --- same problem

Only solution is, going back to 10.04 ---- what a shame --- 

I still have 11.04 on a dual boot, if someone could give me a hint on how to debug this problem?

---

