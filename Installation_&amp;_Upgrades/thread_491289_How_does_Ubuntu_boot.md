---
title: "How does Ubuntu boot"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by mehdi_m62 on 2007-07-03
Dear all 

   I have installed ubuntu and after sometimes I dellet it through windows Xp and I delet the partition. But know windows Xp does not working anymore(it can not boot). can I repair the windows or I should install again :-??


regards.

---

### Post by raja on 2007-07-03
That is because you must have installed grub in the MBR. Now you dont have the original MBR to boot into windows. 
You can insert you windows install cd (if you have one) and do a 'fixmbr', I think that is all that will be required. 

Look [here]("http://www.users.bigpond.net.au/hermanzone/p18.htm") for more info if you dont have the cd.

---

### Post by LaRoza on 2007-07-03
The Super Grub Disk will restore it also. Check my sig.

---

