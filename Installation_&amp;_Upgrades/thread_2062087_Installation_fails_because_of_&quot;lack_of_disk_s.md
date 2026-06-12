---
title: "Installation fails because of &quot;lack of disk space&quot;"
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by paul9 on 2012-09-24
Hello,

i am repeatedly experiencing errors while trying to install packets with apt-get. It always says that there would be no memory left on the device. But df says that there should be enough memory. The last time i tried to install, the packet needed less than one MB while df said that there was at leasts 1/2 GB on each partition of the system. I am clueless. Does anyone knows what the intention of Ubuntu is here?

I am using Ubuntu 10.04 (Lucid Lynx)

Paul

---

### Post by Bucky Ball on 2012-09-24
Welcome.

Yea, you probably need to make a little more headroom than that. Once you start getting below a Gb things can get strange so doesn't matter what size your app is, probably still get the problem. 

And remember, the app, once installed, might take up x amount of space on disk but *installation may require more than x *as data is loaded to disk for the install then removed when it's no longer required.

---

### Post by paul9 on 2012-09-24
> **Bucky Ball said:**
> 
 ... a little more headroom than that ... 

Thanks a lot for your answer, Bucky Ball. Can you say on which directory that headroom is needed?---So i could try to provide some additional space there.

Paul

---

### Post by Bucky Ball on 2012-09-24
The partition you are trying to install to rather than any specific directory I'd say. At a guess /, your root partition.

---

### Post by paul9 on 2012-09-25
My idea was, knowing the directory which Ubuntu uses to do the package installing, that i could mount another partition there. So there would be the required space. On the other hand i do not see how to provide additional space directly with /, since it is now fixed in my system. Anyway, now i have a clue what is happening.

Thanks for answering, Bucky Ball.
Paul

---

### Post by Bucky Ball on 2012-09-25
> **paul9 said:**
> ... i do not see how to provide additional space directly with /, since it is now fixed in my system. 

It is reasonably straight forward. As the partition you want to resize is / boot from the LiveCD>Get to the desktop>Launch Gparted>Right Click the Partition>Unmount + Resize.

If you make a plan, like shrinking the partition next to /, you might be able to come up with something. But make a plan.

You can unmount and resize partitions *other* than / from the hard drive install but easier and safer IMHO this way. 

;)

---

