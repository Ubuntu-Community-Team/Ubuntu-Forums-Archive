---
title: "Merging partitions.....sort of..."
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by CS.Scorpion on 2005-08-06
Ok, I did a silly thing, but without knowing it. When I installed Ububnu, I made a partition called 'set' for setup files (20Gb), but of course I can't save stuff there, so I want to merge that partition with the /home partition. How would I do this, and what tools will I need. I have a liveCd as well as the install cd.

Thanks for any and all help.

Scorp.

---

### Post by amohanty on 2005-08-06
>> man parted

AM

---

### Post by CS.Scorpion on 2005-08-07
[QUOTE=amohanty]>> man parted

AM[/QUOTE]


Okay then........all that did was give me a flashing cursor in terminal  ](*,) 

I assume there is some way of doing what I need as the 'command' above implies, but what does it do, and how do I run it?

Any help greatfully recieved, but please remember I'm a newbie.

Scorp.

---

### Post by sooqing on 2005-08-07
use Bootit NG  to resize all partitions..

---

### Post by GTvulse on 2005-08-07
[QUOTE=CS.Scorpion]Okay then........all that did was give me a flashing cursor in terminal  ](*,) 

I assume there is some way of doing what I need as the 'command' above implies, but what does it do, and how do I run it?

Any help greatfully recieved, but please remember I'm a newbie.

Scorp.[/QUOTE]

Hi Scorp.

It is easier to accomplish what you want using a graphical partitioner. I suggest that you install gparted (if using Ubuntu) or qtparted (if using Kubuntu); in fact gparted is easier to use, in my opinion. Now, there are some caveats you must be aware of to be successful:
[list=1]
[*]Partitions must be adjacent.
[*]Partitions can grow to the end of the disk. You can't move a partition to the beginning of the disk.
[*]Partitions cannot be merged, rather the first partition can be expanded to occupy the space of the second partition if you **delete** the second partition first.
[/list]

---

### Post by CS.Scorpion on 2005-08-07
> **dradul]Hi Scorp.

It is easier to accomplish what you want using a graphical partitioner. I suggest that you install gparted (if using Ubuntu) or qtparted (if using Kubuntu) said:**
> 
[*]Partitions must be adjacent.
[/list]


Thanks Dradul....

I would have gone that way, with gparted, but....as per part 1 of your quote above....the ones I wanted to merge were not adjacent (just my luck), so I did the easiest thing. As this was a new install anyway, I just reinstalled Ubuntu, and set the partitions correctly this time!!  :grin:  :grin: 

Thanks anyway. For future reference, I know what to do now.

Scorp.

---

### Post by amohanty on 2005-08-08
In this:

>> man parted
 

'>>' was meant to be the cursor.

AM

---

