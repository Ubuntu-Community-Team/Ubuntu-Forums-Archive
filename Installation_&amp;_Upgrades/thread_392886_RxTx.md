---
title: "RxTx"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by peterl_j on 2007-03-25
Hi

I am trying to get my serial port working.  I have downloaded Suns Java from the repositories, it works fine.  I downloaded the RxTx stuff, again from the repositories and well so what!  

The application does not see the serial port!

Can anyone please give me a pointer on where to look next!

Thanks

Peter

---

### Post by Mlepicki on 2007-04-05
Is your device located at /dev/ttyS*? I've had to create symlink "ln -s /dev/rfcomm0 /dev/ttyS4".

---

### Post by peterl_j on 2007-04-09
Hi, Thanks for the advice, I will give it a try when I have downloaded my new OS.

Thanks again.

Peter

---

