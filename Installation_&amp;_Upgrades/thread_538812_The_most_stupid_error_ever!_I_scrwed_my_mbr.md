---
title: "The most stupid error ever! I scrwed my mbr"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Lucidio on 2007-08-30
Help please!!!!

I`m an ubuntu user since a pair of years and i have to say that i love it. What i like most is the posibility to tweak it the way i like it (i even had the 3d aceleration, 3d desktop and vary eye candies on my own).

By mistake my sister deleted the ubuntu partition from windows and now i cant use my computer because grub doesnt work. in top of that my cdrom is not working properly, so, i cant reinstall ubuntu properly (sometimes i can run the ubuntu live cd, but i cant finish the instalation). I dont have the windows instaler cd either.

What can i do? I need desperately my pc! :confused: :(

---

### Post by rsambuca on 2007-08-30
You will need to somehow run the ubuntu live cd so that you can restore grub from there (you don't have to re-install the entire ubuntu OS, just grub.

---

### Post by Lucidio on 2007-08-30
How i can do that?

---

### Post by rsambuca on 2007-08-30
Did you get the liveCD to boot?

---

### Post by LaRoza on 2007-08-30
> **Lucidio said:**
> Help please!!!!

I`m an ubuntu user since a pair of years and i have to say that i love it. What i like most is the posibility to tweak it the way i like it (i even had the 3d aceleration, 3d desktop and vary eye candies on my own).

By mistake my sister deleted the ubuntu partition from windows and now i cant use my computer because grub doesnt work. in top of that my cdrom is not working properly, so, i cant reinstall ubuntu properly (sometimes i can run the ubuntu live cd, but i cant finish the instalation). I dont have the windows instaler cd either.

What can i do? I need desperately my pc! :confused: :(

Use the Super Grub Disk to restore the Windows MBR, link in my sig.

---

### Post by Wim Sturkenboom on 2007-08-30
The Ubuntu partition is deleted so chances are very small that one can fix Grub or rescue the system. Best chance to get the machine up is to boot from a Windows install CD (just find one somewhere, borrow from friend or whatever), goto recovery and run fixmbr. At least you will have windows back and can use the system again.
Next you can try to figure out (step 1) how to get data back if necessary and (step 2) how to reinstall Ubuntu.

---

### Post by LaRoza on 2007-08-30
> **Wim Sturkenboom said:**
> The Ubuntu partition is deleted so chances are very small that one can fix Grub or rescue the system. Best chance to get the machine up is to boot from a Windows install CD (just find one somewhere, borrow from friend or whatever), goto recovery and run fixmbr. At least you will have windows back and can use the system again.
Next you can try to figure out (step 1) how to get data back if necessary and (step 2) how to reinstall Ubuntu.

The SGD is much handier to have around, than frantically looking for an install disk.

---

### Post by rsambuca on 2007-08-30
Yeah, I had a brain cloud there!  You definitely need to restore the mbr from either the XP install disk or Super Grub disk.

---

### Post by Lucidio on 2007-08-30
Super grub disK? i think i can obtain that.

Thanks a lot guys! I`ll post my resut here later...

---

