---
title: "Help with partition and instalation..."
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Joe_Swaza on 2009-12-09
Ok, currently I have windows vista installed...what I'd like to do is wipe everything off my hard drive, and install ubuntu on half of my hard drive, and windows 7 on the other half.  I'm faily new to partitioning, and completely new to any form of linux.  So, please post detailed instructions.

---

### Post by phillw on 2009-12-09
> **Joe_Swaza said:**
> Ok, currently I have windows vista installed...what I'd like to do is wipe everything off my hard drive, and install ubuntu on half of my hard drive, and windows 7 on the other half.  I'm faily new to partitioning, and completely new to any form of linux.  So, please post detailed instructions.

Hi & welcome.

1) Put Win7 on - use your entire disk to do it. (As per a Normal Win7 installation)
2) Use the disk management utility in Win7 to 'shrink' it [http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)
3) Make sure Win7 boots happily (it may complain - if so, allow it to 'repair itself until it boots happily)
4) Boot the LiveCD and it will ask to use the 'free area' - Let it do so.

It will ask for the size of swap , as a rule of thumb... 1GB or the same as whatever RAM you have - whichever is greater.

That should have you up & running. 

Regards,

Phill.

---

### Post by audiomick on 2009-12-09
+1 phil. He knows what he is talking about.
You might consider making a seperate partition for / amd /home.
About 10 GB for /
Swap = RAM as Phil said.
The rest for /home

To do this, you have to chose the manual partitioning option in the ubuntu install.

---

