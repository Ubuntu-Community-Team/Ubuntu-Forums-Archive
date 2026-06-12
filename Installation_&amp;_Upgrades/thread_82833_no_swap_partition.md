---
title: "no swap partition"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by Gedemins on 2005-10-27
hi.
I'd like to know what swap partition is used for. Well actually the question would be, what if there's no swap partition on my hdd? I know linux should be installed on ex3 system and the other must be swap, but I installed it without swap. should i notice any system unstabillity or sth? 

sorry for english.. will get better after a while ;)

---

### Post by John.Michael.Kane on 2005-10-27
How much memory do you have installed in the system, most here that do not use a swap have 1gig or more of memory. if you have enough memory there should be no system instabillity. however depending on what your using the system for you may want to add a small amount of swap say 512mb. with out knowing more about your system spec's. if you can please post your system spec's.

---

### Post by Gedemins on 2005-10-27
[QUOTE=SD-Plissken]How much memory do you have installed in the system, most here that do not use a swap have 1gig or more of memory. if you have enough memory there should be no system instabillity. however depending on what your using the system for you may want to add a small amount of swap say 512mb. with out knowing more about your system spec's. if you can please post your system spec's.[/QUOTE]


athlon 1Ghz
256mb of ram 
gf2 32mb
maxtor 40GB
:)
yeah, I guess i'd probably create a swap partition :)

1 more question
let's say i'll create it. does ubuntu recognize it and begins using it at once or will I need a reinstall?

---

### Post by az on 2005-10-27
[QUOTE=Gedemins]
let's say i'll create it. does ubuntu recognize it and begins using it at once or will I need a reinstall?[/QUOTE]
You just need to edit your /etc/fstab file and add a line for swap.

/dev/hd(whatever)  swap swap defaults 0 0

---

### Post by Gedemins on 2005-10-27
[QUOTE=azz]You just need to edit your /etc/fstab file and add a line for swap.

/dev/hd(whatever)  swap swap defaults 0 0[/QUOTE]


ok, i'll have that in mind.
thank's.
now i just need to figure out, why swap needs a separate partition in linux. (unlike windows) but maybe it's another topic..

---

### Post by az on 2005-10-27
[QUOTE=Gedemins]ok, i'll have that in mind.
thank's.
now i just need to figure out, why swap needs a separate partition in linux. (unlike windows) but maybe it's another topic..[/QUOTE]
Not that swapping is a high-performance thing, but a dedicated swap partition is much faster than using a swap file.

---

