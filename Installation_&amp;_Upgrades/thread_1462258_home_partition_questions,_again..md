---
title: "/home partition questions, again."
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by BrockStrongo on 2010-04-25
Okay,
    So I am going to setup a /home partition when I install Lucid. 
Questions are :
How Big should my home partition be?
       I have a 320gb hardrive, should most of this be /home and only ,say, 20 gb for root?
 
Is it better to create /home partition and copy all data to it before I install Lucid, or should I just install lucid, create home partition and restore data from external backup?  
  
I understand these questions are mainly preference, I am jsut looking for some input before I make my decisions.
    ( I am killing time at work)

---

### Post by wirespot on 2010-04-25
> **BrockStrongo said:**
> How Big should my home partition be?
       I have a 320gb hardrive, should most of this be /home and only ,say, 20 gb for root?

20 gb for root partition sounds about right. Mine is 15 gb and it only has about 9 gb occupied, with almost 2000 packages installed.

The only thing that may fill it up is the apt package cache, which you can clean from time to time with `sudo apt-get autoclean` (to get rid of uninstalled or obsolete packages) or `sudo apt-get clean` (to get rid of all the cache). But normally you should have no need to.

---

### Post by wirespot on 2010-04-25
dupe

---

### Post by dwarfolo on 2010-04-25
> **BrockStrongo said:**
> Okay,
    So I am going to setup a /home partition when I install Lucid. 
Questions are :
How Big should my home partition be?
       I have a 320gb hardrive, should most of this be /home and only ,say, 20 gb for root?
 
Is it better to create /home partition and copy all data to it before I install Lucid, or should I just install lucid, create home partition and restore data from external backup?  
  
I understand these questions are mainly preference, I am jsut looking for some input before I make my decisions.
    ( I am killing time at work)
It really depends on what you're going to use your computer for. If you plan to do some video editing for example, 20 Gb could be much less than optimal.

---

### Post by avl555 on 2010-04-25
I think it's best to create the parititon, then install Lucid and after that set fstab so it'll be automounted, and copy all the data after the upgrade.
You don't know what will be happening with the data when you copy the backup before the upgrade (I guess you do a fresh reinstall?).

---

