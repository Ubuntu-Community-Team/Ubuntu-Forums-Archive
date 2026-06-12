---
title: "Just installed ubuntu 7.10 but it won't boot !"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by FluxMaster on 2007-12-10
Hi guys,

I've just installed (and reinstalled) the ubuntu 7.10 on a Vista machine.
I have numerous disks with numerous partitions and for resons too complicated to go in to I had to install it on the 2nd partition of disk 3.
If I'm not mistaked thats the : (3,1) - counting from 0
I boot the machine and get the Vista OS selection, roughly as follows :

[B] 1. Vista 
 2. ubuntu, Gusty gibbon[/B]

And select ubuntu.
Then I get the grub screen and pick the first in the list (the 2nd being recovery)

Then I'm presented with a black screen (a bit like dos) with nothing but the following:

**root (3,1)**

and ... nothing. I can wait and wait and wait but i doesn't do anything.

I've read just about everything I could find on this and other forums, but haven't stumbled accross the solution as of yet.

Does anyone know where I screwwed up ?

---

### Post by PmDematagoda on 2007-12-10
Try booting into Ubuntu Recovery Mode, we should make sure it is a problem with GRUB not Ubuntu itself before trying to change GRUB.

---

### Post by petterth on 2007-12-10
Hi guys, ive had my troubles with setting up grub to, but i got it working,
correct me if i'm wrong but woulden't "2,1" be correct? if you count from "0". 
It's 0400 in the morning here so maybe my head is sleeping.

Cheers!

---

### Post by PmDematagoda on 2007-12-10
Of course, that is the most likely problem, and even though I just woke up now I did not see it:(.

Nice going petterth:lolflag:.

Now to fix it, when you reach the GRUB menu, press E, after that change the root to the following:-

(**2**,1)

After that press B to boot Ubuntu, then it should work.

---

### Post by petterth on 2007-12-10
Thanx
And of course edit your grub.conf so that the settings stays permanent or is that not neccesery?

---

### Post by PmDematagoda on 2007-12-10
Yes it is, but first we ensure that Ubuntu boots, then we get to the part of making it permanent.

---

### Post by FluxMaster on 2007-12-11
I installed ubunto on the 3rd HD in my config.
By third I mean 0, 1, 2, **3**
On the second partition : 0, **1**

In the Grub file it's noted as (hd3,1) ... did I make a mistake ?

I've just tried to boot into recovery mode -> nada 
I still have the :  **root  (hd3,1)**   prompt.

---

### Post by FluxMaster on 2007-12-11
I just tried :

> Now to fix it, when you reach the GRUB menu, press E, after that change the root to the following:-

(2,1)

After that press B to boot Ubuntu, then it should work.

... didn't work :(

---

