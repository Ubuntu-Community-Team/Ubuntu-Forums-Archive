---
title: "Umbuntu does not read secondary ide's?"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by ulao on 2011-01-25
I have the flowing

Primary 
IDE 1: WD 
IDE 2: quantum
secondary:  
IDE 1: maxstore 
IDE 2: maxstore

So its either maxstore drives or the second IDE it wont see. When I get to the partitionier it has the option to take over the entire drive with a drop down of two choices. These two are my primary IDE drives.  

Why would linux not see my other two?

---

### Post by Mark Phelps on 2011-01-27
As far as I recall, you can only have one Primary and one Secondary connected to the same IDE cable/motherboard jack.

So, do you have two jacks on your motherboard? Or is the second set of drivers connected to an add-in controller card?

If it's the second, my guess would be that the Ubuntu installer doesn't have the driver needed to see the add-in card.

If it's the first, sorry, don't have a solution as I've not encountered that problem.

---

### Post by nogoodnamesleft on 2011-01-27
check drive jumpers

1 master, 1 slave on each cable

this used to happen to me a lot in the dark days of IDE


basically you have 2 plugs, 1 cable on each and 2 drives on each cable - thats fien if the jumpers are correct - not every autodetect works, manually set master and slave




> **ulao said:**
> I have the flowing

Primary 
IDE 1: WD 
IDE 2: quantum
secondary:  
IDE 1: maxstore 
IDE 2: maxstore

So its either maxstore drives or the second IDE it wont see. When I get to the partitionier it has the option to take over the entire drive with a drop down of two choices. These two are my primary IDE drives.  

Why would linux not see my other two?

---

### Post by ulao on 2011-01-28
Yeah its a jumper issue. Those maxtors are weird with jumper. I guess windows does not ge effected by crappy hardware like linux does. The Maxtors only have a j50 Mater on, slave off. And yeah one is master one is slave.

I ended up rearranging the drives and installing the grub to the partition. That worked.

Mark Phelps, I think you're just young.  Most boards to day don't give you both ports but all IBM/clone atx MB's have the ability to use two IDE ports. Pre 2000 just about all had both.

---

### Post by Mark Phelps on 2011-01-28
> **ulao said:**
> Mark Phelps, I think you're just young. 
Thanks for the compliment.

>  Most boards to day don't give you both ports but all IBM/clone atx MB's have the ability to use two IDE ports. Pre 2000 just about all had both.

I know that nearly all recent boards include only ONE IDE connector -- which is WHY I made the comment about an add-in controller card.

---

### Post by nogoodnamesleft on 2011-01-28
> **ulao said:**
> Mark Phelps, I think you're just young.  Most boards to day don't give you both ports but all IBM/clone atx MB's have the ability to use two IDE ports. Pre 2000 just about all had both.

EDIT - I was going to have a go at him here as the first PCs had no hard drives at all, then I noticed he said ATX.

BTW - In my opinion, a secondary controller would the other cable on an old machine. That's why I knew it was jumpers. "Secondary IDE" was what it was called in the BIOS in those days, and the BIOS would not see a plug-in (unless it was onboard, in which case it would be called something else, like a Host RAID).

---

