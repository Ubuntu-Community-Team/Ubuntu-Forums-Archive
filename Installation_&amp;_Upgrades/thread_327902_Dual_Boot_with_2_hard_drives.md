---
title: "Dual Boot with 2 hard drives"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by FreakTech on 2006-12-29
I just installed Ubuntu on my laptop.  I have a HP dv8235nr with dual 100 g drives.  I removed my primary drive that already had windows installed and installed Ubuntu on my secondary drive and then swapped the two, putting Ubuntu on my primary drive.  Ubuntu boots fine but Win XP doesn't show up in the Grub menu.  I am new to Linux and any help will be greatly appriciated.

---

### Post by pissedoffdude on 2006-12-30
> **FreakTech said:**
> I just installed Ubuntu on my laptop.  I have a HP dv8235nr with dual 100 g drives.  I removed my primary drive that already had windows installed and installed Ubuntu on my secondary drive and then swapped the two, putting Ubuntu on my primary drive.  Ubuntu boots fine but Win XP doesn't show up in the Grub menu.  I am new to Linux and any help will be greatly appriciated.

your gonna need to edit ur grub.conf file try ```
sudo gedit /boot/grub/grub.conf
``` and try adding these lines ```
title Windows XP 
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
```

---

### Post by pissedoffdude on 2006-12-30
did this work for you

---

### Post by FreakTech on 2006-12-30
yeah that worked great.  Thanks.  I think one of the best things about Ubuntu is the comunity.  You know exactly where to go to find help and people will actually help you.  Thanks again:p

---

