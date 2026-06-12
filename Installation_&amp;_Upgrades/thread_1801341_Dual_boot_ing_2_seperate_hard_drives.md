---
title: "Dual boot ing 2 seperate hard drives"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by saintek1 on 2011-07-10
Hi everyone,  
 
I am finding it hard to get 2 seperate hard drives to work each having different OS..... windows XP and Ubuntu 10.10.
Making Ubuntu the master, it can recognise the drive but cannot boot from it.  If XP is the master it does not recognise the Ubuntu drive at all.

---

### Post by dabl on 2011-07-10
> **saintek1 said:**
>   
 
Making Ubuntu the master ...

???

What is this "master" capability -- are these IDE drives or what?

Some BIOSs need to see the "boot" flag set on the partition to be booted -- you can do that with GParted.  Then it's good to have that drive also be the first (and/or only) hard drive in the BIOS boot sequence list.

---

### Post by oldfred on 2011-07-10
Is this an older system that only has IDE/PATA drives? Old BIOS that supported IDE drives could only boot from the drive with the jumpers set as primary master or slightly newer with the cable select jumper and a 80 wire cable that location on cable set primary master.

Newer systems that support SATA drives have the logic in BIOS to set the "master" (mine still calls it that).

---

### Post by Bucky Ball on 2011-07-10
Welcome. Can you be more specific about the exact errors you are encountering when you attempt to boot Ubuntu? Are you getting a menu list when you boot so you can select Windows or a Ubuntu kernel?

---

