---
title: "Windows disappear from GRUB after updating to Ubuntu 11.10"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by yellowkylin on 2011-11-24
Hi folks! My laptop has ubuntu and windows. I just updated my ubuntu from 11.04 to 11.10. I used the updater from ubuntu 11.04. However, after updating Windows XP disappeared from the GRUB list. What should I do to recover the windows option?

---

### Post by gordintoronto on 2011-11-24
Open gnome-terminal and enter this command:
sudo update-grub

---

### Post by darkod on 2011-11-24
For more details what is where, follow the link in my signature to run the boot info script and post the results here as explained there. It will show more details.

---

### Post by yellowkylin on 2011-11-28
I just fixed the problem. I ran bootcfg /rebuild under windows recovery console and then ran update-grub in ubuntu. Then I can see windows option in grub.

Thanks, gordintoronto and darkod!

---

