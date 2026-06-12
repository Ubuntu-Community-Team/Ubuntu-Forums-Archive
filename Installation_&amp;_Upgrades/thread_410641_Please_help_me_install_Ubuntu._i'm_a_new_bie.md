---
title: "Please help me install Ubuntu. i'm a new bie"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by mocqueanh on 2007-04-16
I've used computer for 3 months recently. And i'm a new bie of computer.
Im using Win XP.
Now i want to install Ubuntu and use as dual with XP.
I used Hiren Boot to make new partition with 20 GB of Ext3(partition E)
Partition C and D is FAT32.
I dont understand what does Primary, Logical partition mean.
How to instal Ubuntu on partition E ? I dont want to lost my XP.
Feel the installion of Ubuntu is difficult more than Windows .
My Ubuntu CD is version 6.1

---

### Post by renzokuken on 2007-04-16
i actually found ythe ubuntu installation easier and much quicker than windows.

the ubuntu cd should automatically detect all your partitions during the install and give you a list allowing you to choose which partition you want to use, in this case, the ext3 one.

the installation will automatically install and setup 'grub' allowing you to choose whether to boot up XP or ubuntu when you start your PC

---

### Post by Ti_Uhl on 2007-04-16
Just insert the ubuntu cd and follow the instructions in the wizard. Normally ubuntu will ask you to automaticly partion your hard drive, and it will find the windows partitions and setup grub to have a dual boot.

---

### Post by kvonb on 2007-04-16
>  I dont understand what does Primary, Logical partition mean.

Any hard disk can only have 4 partitions on it, this is a throwback hardware limitation and can't be changed.

However, a work around was created whereby if we use the last available partition as a "container" partition, we can create lots more partitions inside it.

Hence they called any partitions inside this container "logical partitions'.

That's why if you create a logical partition, under Linux it will skip a number, ie if you have 2 FAT32 partitions (hda1 and hda2) then create a new logical one, it will be called hda4 because hda3 is now a "logical container".

The other thing is that you will need 2 partitions minimum for a Linux installation as instead of using the main partition (as Windows does) for memory paging, we use a separate partition called swap for this purpose.

Remember you can only have a maximum of four primary partitions!

Your swap partition, on a modern Linux system would be about half to 1 gig depending on how much memory you have in your system.

---

### Post by mocqueanh on 2007-04-16
Yeah, now i understand what is primary and logical partition.
Previously, my PC only have partition C as primary, and D, E is both Logical Partitions.
I converted E from FAT32 to Ext3 (now E partition still is logical partition).
I install Ubuntu on this E, during the installion, when i'm in the step: partition, Ubuntu require i choose partition to install( i didnt remeber exactly), i choose E, but Ubuntu say: not find root file, meanwhile i check my CD is 100% correct.
So, i think that i must create new primary partition with Ext3 type and install Ubuntu on it ?

And finish, sorry for my bad English(my language is not Eng), what is swap partition ?

---

### Post by kvonb on 2007-04-17
What I would suggest you do is delete those extra partitions you created for Linux use, but keep the ones you are using for your Windows installation of course.

When you install Ubuntu, choose the option "Use all unallocated space", or words to that effect.

Ubuntu will automatically create all the necessary partitions for you.

---

### Post by mocqueanh on 2007-04-17
Thank, i'll try and post the result as soon.
:popcorn:

---

### Post by mocqueanh on 2007-04-17
Done.
Now i have dual OS in my PC.:)

---

