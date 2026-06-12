---
title: "windows 7  drives not coming"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by rahulvyas on 2011-07-23
big  problem .......frends i hav installed ubuntu with windows 7 dual mode  after shrink the memory for ubuntu ....then in installeation wizerd i  delete tht prt make logical nd also make new prt for swap ..and i  installed it in the logical prt  .......all is done thn i restrt the pc and try to strt windows7 in which  i hav data bt its not wrking ..then i try format the c drive of win 7  in which no drivers is coming ....dnt knw wht happed ...how do i get my  data .....shoud i re install the ubuntu ,coz it is wrking bt not windows  7 .plz help

---

### Post by Quackers on 2011-07-23
Welcome to UF.
In Ubuntu open a terminal and run ```
sudo update-grub
``` then watch the screen to see if the Windows Loader is recognised. If it is, reboot and you should now see a grub menu giving you the choice of which operating system to boot.

---

### Post by Mark Phelps on 2011-07-23
> **rahulvyas said:**
> big  problem .......frends i hav installed ubuntu with windows 7 dual mode  after shrink the memory for ubuntu 
You didn't shrink the "memory" -- you shrank the "disk space".  It helps to use the correct terms when you're asking for help.

>  then in installeation wizerd i  delete tht prt make logical nd also make new prt for swap ..and i  installed it in the logical prt  .......
So, I'm guessing Ubuntu worked OK after you restarted, right?

>  .. thn i restrt the pc and try to strt windows7 in which  i hav data bt its not wrking
This is a typical reaction if you used the Ubuntu installer or GParted to shrink the Win7 OS partition.  Did you do this?
>  ..then i try format the c drive of win 7  in which no drivers is coming ...
How did you try to "format" your "C" drive? And, what do you mean by "no drivers is coming"?  What do you see when you try to reboot Win7.  More details are needed in order to provide you detailed help.

> .how do i get my  data ...
If you really did "format" your C drive, all that data is essentially gone.  You could try using MS WIndows data recovery utilities to get it back.  And, if that is what you want, you need to tell us.
> ..shoud i re install the ubuntu ,coz it is wrking bt not windows  7 .plz help
If Ubuntu is working, there is no reason to reinstall it.  And, reinstalling Ubuntu will do NOTHING to get Win7 working.

We need more details.  And please, no more abbreviated speech -- it's hard enough to understand requests for help without having to guess at what the words mean.

---

### Post by Quackers on 2011-07-23
Can't argue with any of that :-)

---

