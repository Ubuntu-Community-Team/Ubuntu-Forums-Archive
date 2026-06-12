---
title: "How does upgrading to Intrepid affect kernel modules?"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fundae on 2008-10-21
Hi,

I'm running Hardy on a Dell Vostro 1510. The builtin network card driver that ships with Hardy doesn't work with the Realtek card on the 1510, and I had to install the r8169 driver based on instructions I saw [here]("http://www.martinhenze.de/2008/05/24/ubuntu-linux-on-dell-vostro-1510/"). 

My question is: if I upgrade to Intrepid, will have to redo this process? 

Thanks,
Pramod

---

### Post by overdrank on 2008-10-21
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by philinux on 2008-10-21
Download and burn the latest livecd.
[Ubuntu 8.10 (Intrepid Ibex) Daily Build]("http://cdimage.ubuntu.com/daily-live/") 

Give it a whirl. There's only 9 days to go till the final release. I'd hold off upgrading till then especially if this is your main machine. I prefer clean installs myself. I've /home on it's own partition so it's really easy.

---

### Post by dinxter on 2008-10-21
i believe the driver had problems with the 2.6.24 kernel and, in theory, the r8169 driver included with the intrepid 2.6.27 kernel should work... in theory :) trying out the livecd is the safe way to find out though

---

