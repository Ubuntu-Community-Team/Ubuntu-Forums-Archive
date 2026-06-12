---
title: "Dual Boot Vista/Ubuntu Partitions"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by JimmyK377 on 2007-10-22
Apologies if this has been asked before but I haven't found anything exactly solving my problem.

I bought an Acer Aspire 5920g with Vista HP already installed, I don't have a full vista installation disk, only one that will take it back to it's original state.

After finding the 64-bit ubuntu wasn't working properly with my hardware, I used the 32-bit version and all seemed well. However, after much head scratching over the issue of why the partition space I'd freed up was unusable, regardless of whether or not it was done with the Vista editor or whilst setting up the ubuntu installation, I finally used the partition editor to be found in the Ubuntu applications menu, where it finally explained to me that you cannot have more than 4 primary partitions. As i'd already seen Vista uses 4 (one called ACER, with most of the data, one called DATA with barely anything on, that I had originally shrunk to get the unallocated space, one labelled PQSERVICE, and one it said was hidden).

Any ideas where to go from here?

---

### Post by ldesilva on 2007-10-22
The partition that is labelled as PQSERVICE is used when you want to restore the OS. If I am not mistaken, you should be able to make a backup copy on DVD.

FYI, I am using a Acer Laptop.

---

### Post by JimmyK377 on 2007-10-23
That still leaves Vista with 3 partitions though, is there a way of doing Ubuntu with only one primary partition or should I look at splitting the DATA partition and moving half to C: and half to a new partition?

---

### Post by JimmyK377 on 2007-10-25
PQSERVICE -> DVD, is it safe to remove the content of that partition from the HDD after that then?

---

### Post by meierfra on 2007-10-25
> That still leaves Vista with 3 partitions though, is there a way of doing Ubuntu with only one primary partition ? 

Just create an extended partition. Then inside the extended partition you can create logical partitions for Ubuntu, swap and whatever else you want.

---

### Post by JimmyK377 on 2007-10-27
I've been looking for solutions to the PQSERVICE partition issue and opinion seems split about whether or not it's safe to remove. I'm fairly sure (currently at uni having left some stuff behind) my laptop came with a vista recovery disk. Do you know if that renders the partition unnecessary?

EDIT: and yes I am exceptionally new to all this

---

### Post by meierfra on 2007-10-27
I   know nothing  about PQSERVICE. But another option is to  back up your files on the  Data partition, delete that Data partition,  create an extended partition and then recreate your Data partition inside the extended partition.

---

### Post by Zoolie on 2007-10-27
hello.

i'am here with an other problem,but i think it's fit to this topic,so i dont create a new one.

i have 2 hdd's.

on the 'a' i have vista and on 'b' i want gutsy.

now,if o set the 'b' one to be the first boot device and it got higher priority than the 'a' and i boot gutsy livecd and want install it dont give me grub menu with vista? or it give's? couse i want to change the system i want to boot in my bios with this hard disk boot priority option.

is this possible?

i hope you can understand

---

### Post by confused57 on 2007-10-27
> **Zoolie said:**
> hello.

i'am here with an other problem,but i think it's fit to this topic,so i dont create a new one.

i have 2 hdd's.

on the 'a' i have vista and on 'b' i want gutsy.

now,if o set the 'b' one to be the first boot device and it got higher priority than the 'a' and i boot gutsy livecd and want install it dont give me grub menu with vista? or it give's? couse i want to change the system i want to boot in my bios with this hard disk boot priority option.

is this possible?

i hope you can understand
What you are proposing to do "should" work.  If this is your only pc, I would recommend that you download & burn a copy of the Super Grub Disk, before installing Gutsy:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD should be able to repair your system, if anything goes wrong.

---

