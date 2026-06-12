---
title: "Upgrade from a 32-bit installation to 64-bit on 10.10"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by slakur on 2010-11-18
Is is possible to upgrade a 32-bit install of 10.10 to 64-bit over the network? Basically, I want to avoid downloading the installation media and doing a fresh install. I have seen people talking about this back in [2005]("http://ubuntuforums.org/showthread.php?t=41865"), where the conversation concludes that you should just do a fresh installation. It seems like it should be pretty easy to just upgrade the kernel and userland of a 32-bit installation to 64-bit packages, perhaps I am naive?

---

### Post by dino99 on 2010-11-18
the main question is : why you want 64 bits instead of generic-pae kernel that give the same advantages without all the 64 bits troubles ?

---

### Post by slakur on 2010-11-18
The reason for me making the switch is that I want to run native 64-bit programs, more specifically to run 64-bit oracle database and weblogic. If I could do that with my 32-bit system I would be happy, I don't know that I need a 64-bit kernel otherwise.

---

### Post by Mark Phelps on 2010-11-18
To answer your original question, NO, it is not possible to "upgrade" an existing 32-bit installation to 64-bit.  You have to do a complete reinstallation.

---

### Post by TBABill on 2010-11-18
And just to correct a percpeption some people show about 64 bit Ubuntu, the issues used to be a lack of software for 64 bit, 32 bit flash running in 64 bit, etc. Those are non issues these days and I have no problems running 64 bit Ubuntu on multiple machines with various configurations of sound, wireless, video, etc.

---

### Post by sikander3786 on 2010-11-18
> Those are non issues these days and I have no problems running 64 bit Ubuntu on multiple machines with various configurations of sound, wireless, video, etc.

+1 to that.

ubuntu-restricted-extras nicely sets up everything for me even on 64-bit. Never had any issues with flash ever.

To the OP: You can install pae-kernel as suggested already to take advantage of RAM > 3 GB.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

But you cannot upgrade from 32-bit to 64-bit as Mark Phelps already mentioned. Clean install is the only option.

---

