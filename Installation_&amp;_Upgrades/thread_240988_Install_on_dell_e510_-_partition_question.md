---
title: "Install on dell e510 - partition question"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by zshall on 2006-08-21
I am going to try and install the latest ubuntu version on my new dell e510. I downloaded the cd, started it in safe gfx mode (regular mode didn't work),  and got as far as the partition information on the installer until I noticed a problem. I want to keep my windows partition, but shrink it and install the swap and main ones in the shrinked space. The problem is I also want to keep all of the stupid partitions (dell system recovery, and dell diagnostic utility) that dell put in as well.

The only option there is 'delete all partitions' or 'custom'.
The custom thing looks scary. Can anyone tell me what to do if I want to keep all of my dell partitons and the windows partition, but shrink the windows partiton and install on that space?

---

### Post by Bobido on 2006-09-17
You can keep all yout patition, but you will lost the system recover function by pressing"F11"

Consider it!

This is because the Ubuntu 6.06 does not offer a choice to install Grub in other partition. It will install on the MBR, and this sucks!

---

