---
title: "32 or 64 bit?"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by jefft113 on 2007-08-29
Hey, I have Feisty on my laptop, but I have no idea if it is 32 or 64 bit, how can I tell? I think its 32, but I need to know for sure before I buy some software.

---

### Post by viciouslime on 2007-08-29
To check if your feisty install is 64 bits go to a terminal and enter "uname -a"

You will get something like this:
Linux lime 2.6.22-10-generic #1 SMP Wed Aug 22 07:42:05 GMT 2007 [COLOR="Red"]x86_64[/COLOR] GNU/Linux

If you have x86_64 in the output you have a 64bit install, if it says i386 then you are running 32bit feisty.

If it is 32bit feisty, however, this does not mean that your computer is not 64bit capable. It is possible to install 32bit ubuntu on a 64bit machine, just not the other way around. So, if you post the type of processor you have, or, if you don't know this, the make/model of your machine, I will tell you if it is 64bit capable :D

---

### Post by Kxpress on 2007-08-29
I successfully installed 32-bit version of Ubuntu 7.04. 
My machine ThinkPad T61 has Intel Centrino Core 2 Duo T7300 2.0 GHz, it is a 64-bit machine right ? Is it easy to upgrade to 64-bit version ?

---

### Post by PurposeOfReason on 2007-08-29
> **Kxpress said:**
> I successfully installed 32-bit version of Ubuntu 7.04. 
My machine ThinkPad T61 has Intel Centrino Core 2 Duo T7300 2.0 GHz, it is a 64-bit machine right ? Is it easy to upgrade to 64-bit version ?
You'd have to do a whole new install. With the 64bit ISO.

---

### Post by Kxpress on 2007-08-29
If I used 64-bit ISO, my machine will be a triple-boot machine or it will overwrite/install over the existing 32-bit kernel ?
Thank.

---

### Post by PurposeOfReason on 2007-08-29
That's your call. You could remove the old installation if you wanted.

---

### Post by Mogurijin on 2007-08-29
Even if you have to reinstall Ubuntu, it's not like it takes forver. I mean, it isn't Windows :D. Also, aren't there a few issues with a 64bit install. I've heard some people spewing horror stories, but I've also seen many peole deny these stories. One such item is Flash. I'm running a 32bit machine so it doesn't matter to me but it might be nice before messing with an upgrade ;)

---

### Post by PurposeOfReason on 2007-08-29
Thanks to Kilz, for flash you download a file he made, run it in a terminal, and you're done. :) :

---

### Post by Kxpress on 2007-08-29
I am sorry for keep asking this type of silly questions. it seems you are familar with Fiesty, may I ask which version is more stable and have more popular apllications ?
I am planning to work on some simulation stuffs, perhaps I needed a more powerfull machine, but due to the financial constraint this is the one I can afford.

Thanks

---

### Post by Mogurijin on 2007-08-29
I like Feisty, albeit it is the only Ubuntu I've tried, and it even works on an old piece of junk I peiced together with scraps (1GHz Athlon, sis integrated graphics, some really slow 10gig hd from a  98 machine, etc). Well, I have tried Xubuntu for that machine, but it wouldn't install grub right, so I just used my Ubuntu disk :D

---

### Post by -SpaZ on 2007-08-29
In my experience 32-bit is a lot easier to deal with, but if you need that little performance boost that the 64-bit version gives you, then go for it.

---

### Post by jefft113 on 2007-08-29
I appreciate the help, I recognize the i386, I used to go grab packages with that number, but when I type in "uname -a", I dont get either of the listed options, I let it automatically upgrade from edgy to feisty and I get i686. I dont know if that still means it is 32-bit. I have a feeling that it would still be 32-bit, does anyone know if it would change from 32 to 64 on its own?

---

### Post by rsambuca on 2007-08-29
You still have a 32bit OS.

---

### Post by Mogurijin on 2007-08-30
> **rsambuca said:**
> You still have a 32bit OS.

He's right you know. What is your processor?

---

### Post by jefft113 on 2007-08-30
Intel(R) Pentium(R) M CPU, with 1.7 GHz.

---

### Post by rsambuca on 2007-08-30
That is a 32bit processor.

---

### Post by jefft113 on 2007-08-30
Yea, thats kinda what I figured, thanks for the help.

---

