---
title: "partition 40gig hard drive"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by John.Michael.Kane on 2005-08-25
I have a 40gig drive ubuntu will be the only os used . i have 512mb of ram how wouldone set up the partition for this drive, and howsmall or  large would the swap file have to be.

---

### Post by jasmuz on 2005-08-25
Greetings:

For a root partition you will need as a minimum 1.6 Gb (Ubuntu Full install) to 10-15gb of storage,
for your /home partition, scrunge up everything you can (depending on how heavily you use the pc)
As for swap it can go from 10% of your RAM to 2x your RAM, you could make by with 300megs or so.

---

### Post by John.Michael.Kane on 2005-08-25
Thanks

---

### Post by az on 2005-08-25
Just use the default (use entire drive) partitioning scheme the installer will give you.  It should be fine.  Also, you need to have more than your ram (at least 25 percent more?) so that you can use the hibernate function.

The installer will calculate and create your root and swap partitoins for you automagically.

---

### Post by John.Michael.Kane on 2005-08-25
the swap file thing i can understand .. allocating all that space for just the os i dont understand ..

---

### Post by Zhukov on 2005-08-25
It isnt weird. I have 1,5 Gb for swap, and my pc never stall, or slowed down or anything like that, and that is well worth the space, even more if you have to spend a lot of time working at the computer.
It only works until a certain amount of space, but a big swap partition can greatly increase you pc experience, now you have to see what you are going to do with the machine and how do you want the machine to behave.

---

### Post by John.Michael.Kane on 2005-08-25
no real heavy graphicswork i will be running a progam called eagle and some word doc work andnet surfing

---

### Post by az on 2005-08-26
[QUOTE=SD-Plissken]the swap file thing i can understand .. allocating all that space for just the os i dont understand ..[/QUOTE]


I do not know what you mean by this.

If Ubuntu is going to be the only os on the box, why not allocate all the space to it?

If you want to add other operating systems, you can always partition the drive afterwards.

---

### Post by hashimoto on 2005-08-26
In the expert mode installation there is a selection where you can ask the install program to partition the HD for desktop use or something. It will then check the HD size and mem size and suggest a partitioning sheme: /, swap and home.

---

### Post by az on 2005-08-26
[QUOTE=hashimoto]In the expert mode installation there is a selection where you can ask the install program to partition the HD for desktop use or something. It will then check the HD size and mem size and suggest a partitioning sheme: /, swap and home.[/QUOTE]
You do not need to be in expert mode to do that.  Just pick "manual edit partition table"

You can even manually edit to shrink a partition to create free space, and then go back to guided partitioning to let the installer create the root and swap partitions for you.

Breezy will have this option as default - that is, unless there is already free space, it will suggest shrinking the largest partition for you and installing on the free space it creates.

Expert mode is probably more accurately called debug mode.  There is nothing you cannot do from the regular mode that you can do from expert mode.

---

