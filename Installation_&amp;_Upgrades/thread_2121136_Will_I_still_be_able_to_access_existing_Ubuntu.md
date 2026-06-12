---
title: "Will I still be able to access existing Ubuntu?"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by glad62 on 2013-03-01
my planned new system will have  new
120 gb SSD 1. Windows 7 64
    "     SSD 2. Flight sim Apps

from my old system I will install
HDD 1. with existing ubuntu working intallation (plus Win XP install)
HDD 2. for Data of both file formats

I want Windows 7 to be my most optimised config. for gaming (only) but continue to use Ubuntu for
day to day computer needs.

How should I physically install these drives to achieve dual boot?
Any thoughts would be appeciated.

---

### Post by stinkeye on 2013-03-01
I would think you just need to choose your old ubuntu/xp drive as the boot device in the BIOS
and then once logged in to Ubuntu, run 
```
sudo update-grub
```

To be safe I wouldn't even connect the ubuntu/xp drive until after the
SSD Windows7 install.

---

### Post by glad62 on 2013-03-01
Of Course.  Dummy me.
At times "one goes in to drain the creek and then finds oneself upto his a...e in crocodiles"
Thanks Stinkeye.

---

### Post by stinkeye on 2013-03-01
glad2 help glad62.

---

### Post by Mark Phelps on 2013-03-01
> **stinkeye said:**
> To be safe I wouldn't even connect the ubuntu/xp drive until after the
SSD Windows7 install.

+1 This is indeed the safest option when you're dual booting, as this prevents accidental installation of GRUB to the Windows drive.

---

