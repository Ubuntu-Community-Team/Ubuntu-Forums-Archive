---
title: "Another dual boot question"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by goldshirt9 on 2013-07-13
I happily run Ubuntu LTS on a laptop, but unfortunately some time's I do need to use Windows 7  (even steam as yet doesn't run certain games in Linux).
I have dual booted before and have had no serious problems, but I normally only run LTS releases.
ATM I am running 12.04 and when the next LTS is released I want to install over this without effecting booting in to Windows 7 ?

Can this be done without too much pain.?

Any help is appreciated Thanks

---

### Post by claracc on 2013-07-13
There is not any problem. I have a hp compaq 6720s laptop dualboot win vista/ubuntu 12.04, I have been upgrading the ubuntu part since ubuntu 9.04 without any problem. The windows part remain untouched since the OS's are installed in different partitions.

---

### Post by goldshirt9 on 2013-07-13
do you upgrade lts to lts or every release ?

---

### Post by claracc on 2013-07-13
Yes for the last one, from 10.04 to 12.04. Everything was OK

For the previous ones, it was step by step (9.04 to 9.10, and after one year or more to 10.04)

---

### Post by Mark Phelps on 2013-07-13
> **goldshirt9 said:**
> ... Can this be done without too much pain.? 

When you do a version upgrade, it will overwrite the GRUB config file. So, after that, you will need to open a terminal and enter "sudo update-grub" -- to regenerate the GRUB config file with an entry for Win7.

---

### Post by goldshirt9 on 2013-07-13
will look into cheers

---

