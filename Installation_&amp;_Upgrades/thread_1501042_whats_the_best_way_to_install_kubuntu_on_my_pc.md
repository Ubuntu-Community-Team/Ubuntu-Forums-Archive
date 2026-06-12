---
title: "whats the best way to install kubuntu on my pc"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by skakid177 on 2010-06-03
im running xp and id like to run kubuntu on the same machine. should i  use that virtual pc software? if possible i want to install it entirely  on its own hard drive

---

### Post by wilee-nilee on 2010-06-03
> **skakid177 said:**
> im running xp and id like to run kubuntu on the same machine. should i  use that virtual pc software? if possible i want to install it entirely  on its own hard drive

So you might share what you mean by on it's own hard drive, how many HD's do you have and do you want to due a true dual boot which would mean Kubuntu in it's own partitions, installed with a booted live cd or thumb, or a install inside of XP with wubi.

---

### Post by skakid177 on 2010-06-03
i have two hard drives already and another that i wanted to erase to put linux on. i have no idea what wubi is so i guess a dual boot with the entire hard drive its own partition

---

### Post by wilee-nilee on 2010-06-03
> **skakid177 said:**
> i have two hard drives already and another that i wanted to erase to put linux on. i have no idea what wubi is so i guess a dual boot with the entire hard drive its own partition

So just use the booted install cd to install to that drive, but make sure you put grub in the master boot record of that HD. You do this by checking the advanced button in the last install gui and checking that that grub is pointed at sdb if that is the drives actual name, don't install grub to the XP HD or to a partition. Some suggest unplugging the HD with XP, but as long as grub is installed correctly there should be no problem. Grub is the Linux bootloader. Go slowly look at the whole set up 1st from gparted on the live cd so you understand which is the second HD.

You also may want to make sure the disc has been checked at boot for errors by hitting the shift key to bring up the old choice of options which has a cd check option, also make sure your computer is going to run okay with Kubuntu, personally I don't like Kubuntu, but others do. A standard Ubuntu install may be easier to understand if this is new to you.

---

