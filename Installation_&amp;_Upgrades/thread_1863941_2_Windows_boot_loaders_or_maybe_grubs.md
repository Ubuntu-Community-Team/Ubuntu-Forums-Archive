---
title: "2 Windows boot loaders or maybe grubs?"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by fallen1011 on 2011-10-18
when i put in the ubuntu cd, i press install and somehow i can see that i have 2 windows loaders, which has been causing problems considering your only supposed to have only 1, ive already been having problems with ubuntu install all week as is...but i see that this loader has been causing the problem, or at least one of them, saying "this system has multipule operating systems" how can i find and get rid of this extra loader, ive formated the drive at least 5 times and no luck, i checked disk managment and it doesnt show up, what else can i do here? how did i even end up with 2 windows boot loaders in the first place?


64 bit windows 7 ultimate, 600-1365q hp touchsmart 23' pc 8gb ram
i7 1.73ghz

---

### Post by Quackers on 2011-10-18
Welcome to UF :-)
It's likely that one of the Windows Loaders boots a recovery partition and the other boots your Windows installation. 
Both partitions have a set of boot files, so grub picks them up as different OSes.

---

### Post by fallen1011 on 2011-10-18
> **Quackers said:**
> Welcome to UF :-)
It's likely that one of the Windows Loaders boots a recovery partition and the other boots your Windows installation. 
Both partitions have a set of boot files, so grub picks them up as different OSes.

i got more info, when i went to install ubuntu, it shows this "select any account you want to import, and its the secound windows loader the sda2 thats no supposed to excist...how can i get rid of this sda 2 it never did this the actual first time i installed ubuntu but ive had problems and now this is like the 5th time...

---

### Post by Quackers on 2011-10-18
That's just for importing settings during installation. I wouldn't recommend importing any Windows settings ;)
Once installed see what grub shows. It is possible to delete the Windows Loader for the recovery partition but it is no small job.
I have left mine alone. I just remember not to boot that one :-)

---

