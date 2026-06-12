---
title: "Pros and cons on laptop amd64 ati 3100"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by thonuz on 2008-09-18
On my laptop -- a Toshiba M305D AMD64 x2 R70 and ati 3100, atheros I have a couple of problems that have forced me to go back to Hardy for now and am wondering if I need to file separate bugs.

On Ibex: Wireless and wired works, no battery indication is possible -- ACPI?? and I get lock ups on boot at powernow unless I boot rescue. Also no compiz or drivers for ATI 3100;

On Hardy neither wired or wireless work, very painful at first but there is a way to get the unknown Marvell device working by doing some fixes to sky2.ko in kernel modules. Wireless is also possible by compiling madwifi. 
battery function and compiz also work.

So as is now Hardy is more functional even though the kernel sees some improvements. I know the catalyst driver is coming, but the ACPI or battery issue is a show stopper.

---

