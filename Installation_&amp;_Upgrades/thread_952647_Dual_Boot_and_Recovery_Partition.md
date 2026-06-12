---
title: "Dual Boot and Recovery Partition"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by JonE8 on 2008-10-19
Hi Everyone 

I'm thinking of dual booting Vista and Ubuntu again, last time I got rid of the PC Angel recovery partition on my laptop and put Ubuntu on there which I ended up regretting, but when my laptop went away for a graphics card replacement I got the recovery partition back. I don't want to lose it again so have got a few questions; 


1. Can I clone/copy the recovery partition onto a dvd so I could use the partition for my Ubuntu install?  

2. Does the Vista boot loader control booting into the PC Angel recovery partition? I ask because I will be using Grub as the boot loader and don't want to lose access to the recovery partition if I can't make a copy of it. 

Cheers 

Jon

---

### Post by crazyness003 on 2008-10-19
Even though you'll be using grub, all grub does is chainload the vista boot loader. So after you select vista from your grub list, you will be greeted with the vista bootloader list, hence allowing you to load your recovery partition. Of course this happens only if everything does smoothly.

As for backing you your partition, im gonna assume you can just make an image copy and burn to optical or HDD media, like with any other partition image. But someone else with further knowledge may interject at any time.

I personally found the "recovery" partitions to be a waste of disk space. As soon as I got my lappy, Wiped the entire drive clean, down to the last 00.

---

