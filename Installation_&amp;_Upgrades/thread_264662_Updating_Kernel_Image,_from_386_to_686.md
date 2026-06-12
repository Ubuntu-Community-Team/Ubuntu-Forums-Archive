---
title: "Updating Kernel Image, from 386 to 686"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2006-09-25
I am currently running linux image 386 2.6.15.25 that states, This package will always depend on the latest kernel image available
for 386. and I have image 2.6.15-23.29, 2.6.15-26.47 and 2.6.15-27.48.
I have a P4, What procedures should be followed in order to have the linux image 686? Should I check and install the linux image that states,This package will always depend on the latest kernel image available
for 686. and apply? How many images should I be holding on to??? 2 others?

Thanks, I don't want to crash!?!?!?!?!

---

### Post by al_sharpe on 2006-09-25
Hello Chazall1:

Not sure on the correct answer, but I keep the original 386 kernel
from first Dapper install and the latest 386 and 686 kernel from 
repository and delete previous 386 and 686 after about 1 week.
I keep 386 for stability and use 686 when all is well.
Loading linux-image-686 will keep your restricted modules
updated so your nvidia or ati drivers will work after synaptic update

Cheers
Al

---

### Post by tseliot on 2006-09-25
Type:
```
sudo aptitude install linux-686
```

and reboot

that will install the restricted modules and the kernel image

---

### Post by Rhubarb on 2006-09-25
Thanks tseliot for posting the answer before I had a chance to!
Anyway, the 686 kernel also adds support for hyper threading / dual core systems.  Which for my Core Duo laptop, makes a huge performance leap.  Haven't found any stability problems with the 686 kernel.

---

### Post by Drezliok on 2006-10-30
I'm trying to use the aptitude command to upgrade to Kernel 686. But it won't install it.

I'm using Edgy.

---

### Post by sjrixon on 2006-10-31
I have just done a fresh Edgy install. apt-get install linux-686 installs fine.. But it looks like it doesn't bother setting it up. Still the generic kernel image is the only one available.

---

