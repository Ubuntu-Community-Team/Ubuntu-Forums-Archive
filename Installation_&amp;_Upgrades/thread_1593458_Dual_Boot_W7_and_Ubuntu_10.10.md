---
title: "Dual Boot W7 and Ubuntu 10.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by jammmie999 on 2010-10-11
Hey guys,

I have just installed Ubuntu 10.10 clean install and choose to install alongside other OS. Now when I boot I get about 5 Ubuntu options but no W7 option in my GRUB boot loader. I have ran the boot_info.sh script and got the following results

[http://pastebin.com/27SybPaC](http://pastebin.com/27SybPaC)

Please help me to dual boot Windows 7 and Ubuntu 10.10

Thanks

---

### Post by dino99 on 2010-10-11
a quick "search" about w7+maverick in this forum will give you the solution posted zillions times

---

### Post by jammmie999 on 2010-10-11
care to help enlighten me? I have tryed searching before posting this but cant find any results.

---

### Post by Mark Phelps on 2010-10-12
From your script, it looks like you have two physical drives, one containing Win7, the other Ubuntu -- right?

If that's true, do the following:
1) Go into your BIOS and set the boot option to use the Ubuntu drive
2) Boot into Ubuntu, open a terminal, and enter "sudo update-grub".

That will regenerate the GRUB menu and add an entry for Win7.

When you reboot, you should see that menu and be able to choose Ubuntu or Win7.

---

