---
title: "Help me configure system for new RAM"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by j2fraser on 2008-03-09
I have just upgraded my Dell Dimension 9150 from 1GB 533Mhz to 4GB of 667Mhz RAM... What configuration tunings, if any, should I make? Will Ubuntu/Linux read the new memory install automatically, and start using it appropriately, or do I need to manually change any settings? I had previously setup a 3Gb swap partition -- should I keep it or change it? I'm running 7.10 AMD64. Thanks!

---

### Post by munkyeetr on 2008-03-09
The OS should just work with the new RAM installed (provided there are no issues with the memory itself). One issue you may have is if you are running the 32-bit version of Ubuntu, you will only see between 3-3.5 GB of that 4GB you installed.

That is a limitation with 32-bit operating systems, and the only thing you can do about it is switch to the 64-bit version of Ubuntu. (Yes, I noticed in your post you said you are running 7.10 AMD64, but I'm not sure if you are just saying what processor you are using)

As far as the swap file, I am running with 2GB of RAM and a 1.5GB Swap, and I haven't seen my swap file accessed at all yet. I would probably lower your swap size if you wanted to reclaim some disk space, but otherwise, it can't hurt.

---

### Post by j2fraser on 2008-03-09
Thanks! I am glad to know there's nothing I have to do. BTW, I am running the 64-bit version of Ubuntu, but I still only see ~3.5GB of RAM in Linux. BIOS reports 4GB installed. I think that this is due to the fact that my system uses the RAM for on-motherboard video/sound...? The manual says: 
> 
Your computer supports a maximum of 4 GB of memory when you use four 1-GB DIMMs. Current operating systems, such as [*the OS that shall not be named*], can only use a maximum of 4 GB of address space; however, the amount of memory available to the operating system is less than 4 GB. Certain components within the computer require address space in the 4-GB range. Any address space reserved for these components cannot be used by computer memory.

Funny though... I don't remember missing chunks of RAM when I had 1GB installed... Oh well.

---

