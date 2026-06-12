---
title: "UEFI Turned Off... 64 Bit Still Necessary?"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by nnjrob2 on 2013-11-05
Hello, I recently purchased a laptop with Windows 8 installed. I know Ubuntu requires a 64 bit install for use on a UEFI windows dual boot. If I have UEFI turned off, can I use a 32 bit?
I have a game I'm addicted to, that STILL won't work with 64 bit linux.

---

### Post by mastablasta on 2013-11-05
what game? why won't it it work in 64 bit? with 64bit you just install the 32 bit libraries and 32 bit stuff usually works then...

---

### Post by Bucky Ball on 2013-11-05
> **mastablasta said:**
> with 64bit you just install the 32 bit libraries and 32 bit stuff usually works then...

+1. Are you sure it works in 32bit? Could be a wild goose chase as maybe it just doesn't work or there is a problems that has nothing to do with **bit.

---

### Post by oldfred on 2013-11-05
The only way you could use 32bit would be to totally turn off UEFI and turn on CSM/BIOS/Legacy boot mode. 

Then to boot a 32 bit Ubuntu you would have to go into UEFI and turn on the CSM and UEFI off. Then to boot Windows or a 64 bit UEFI install turn off CSM and turn UEFI on. Not the easiest way to dual boot but possible.

 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

---

### Post by nnjrob2 on 2013-11-07
> **mastablasta said:**
> what game? why won't it it work in 64 bit? with 64bit you just install the 32 bit libraries and 32 bit stuff usually works then...

You're right. I found a list of additional stuff that wasn't added by default(on the site for the game). Added it, and all works well, with a 64 bit install. One more hurdle, for a different thread. Thanks All, marking this one solved

---

