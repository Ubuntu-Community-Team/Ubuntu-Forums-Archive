---
title: "Installation of Ubuntu 18.04 LTS on a 32-bit computer with 1.5 GB RAM"
date: 2019-04-07
forum: Installation &amp; Upgrades
---

### Post by Kaminar on 2019-04-07
Hi,

I need to reinstall a 32-bit computer which now runs on Ubuntu 14.04 LTS. It is not my computer, therefore I can not experiment to see if there are any problems with Ubuntu 18.04 on this computer. That's why I turn to this forum asking you about experiences with Ubuntu 18.04 on a 32-bit computer that has 1.5 GB of RAM.

I would like to ask how good 32bit support is and if all 64bit versions packages will be available and supported for the 32bit version in the future. I am most interested in MidnightCommander, SeaMonkey, LibreOffice, GIMP and gnome-session-flashback.

I would also like to ask if you have any experience with Ubuntu 18.04 on a computer that has only 1.5 GB of RAM. Ubuntu 14.04 on 1.5 GB of RAM runs smoothly, but I'm a bit worried that Ubuntu 18.04 and the above-mentioned apps has become too resource-hungry, and 1.5GB of RAM would not be enough for them. Under VirtualBox it runs, but VirtualBox is not real HW.

---

### Post by kc1di on 2019-04-07
though I have not experiment with the 32 bit version, I do believe that for the modern gnome desktop used by 18.04 that 1.5 GB ram will not suffice.  And the machine would run very slowly.  I can't speak to the other issues you raise.  I would think that xubuntu or ubuntu mate may be a better fit for that machine. Good luck in your search.

---

### Post by CatKiller on 2019-04-07
> **Kaminar said:**
> 
I would like to ask how good 32bit support is and if all 64bit versions packages will be available and supported for the 32bit version in the future.  
No, they won't. Ubuntu has already stopped providing 32-bit desktop install images. Even the lighter flavours have dropped it. Chrome is not available as a 32-bit version. It's only a matter of time before all support for 32-bit architectures is stopped. 

> I would also like to ask if you have any experience with Ubuntu 18.04 on a computer that has only 1.5 GB of RAM. Ubuntu 14.04 on 1.5 GB of RAM runs smoothly, but I'm a bit worried that Ubuntu 18.04 and the above-mentioned apps has become too resource-hungry, and 1.5GB of RAM would not be enough for them.
It's not the system itself that's the issue, it's really websites that push up the requirements. Sure, the computer can run with that little RAM, but you still need to be able to do other things.

That machine's remaining useful life is limited.

---

### Post by Rubi1200 on 2019-04-07
I just recently discovered another alternative: [https://www.neverware.com/#introtext-3](https://www.neverware.com/#introtext-3)

The software CloudReady is based on Chromium OS and they have a 32bit install option.

Might be worth looking into it.

---

### Post by oldfred on 2019-04-07
I have a laptop from 2006 with 1.5GB of RAM.
I installed 64bit Ubuntu 16.04 and used fallback or gnome panel.
It runs well if I only use one larger app like Firefox or LibreOffice, but not both at same time. 
I normally opened Firefox, terminal & text file like Zim, but if I accidentally clicked on something that opened another large app, it would go to swap and turn gray for several seconds.

What hardware is it?
Brand model system, cpu & video?
Some very old hardware is not supported, as drivers were not secure and no one wanted to attempt to update them.

---

### Post by Impavidus on 2019-04-07
Ubuntu no longer has a 32 bit live disk iso, but lubuntu and xubuntu still have one. I didn't check the other flavours. It's not known how long this will remain so, but for the moment the official Ubuntu software is still available in both 32 and 64 bit. Some other suppliers (like Google) have dropped support for 32 bit, so Chrome is no longer available in 32 bit.

---

### Post by CatKiller on 2019-04-07
> **Impavidus said:**
> Ubuntu no longer has a 32 bit live disk iso, but lubuntu and xubuntu still have one.

[https://lubuntu.me/sunsetting-i386/](https://lubuntu.me/sunsetting-i386/)
> With i386-only machines becoming an artifact of the past, it has become  increasingly clear to the Lubuntu Team that we need to evaluate its  removal from the architectures we support. After careful consideration,  we regret to inform our users that Lubuntu 19.04 and future versions will not see a release for the i386 architecture.

[https://lists.ubuntu.com/archives/ubuntu-release/2018-December/004647.html](https://lists.ubuntu.com/archives/ubuntu-release/2018-December/004647.html)

> This is an announcement that Xubuntu will no longer be shipping a 32-bit installation medium starting with Xubuntu 19.04.

---

### Post by Kaminar on 2019-04-13
Thanks everyone for your answers, especially to oldfred.
The CPU is Intel Dual Core. The video is integrated on the motherboard.

I decide to upgrade the computer to 64bit. I guess it will be better choice than try to struggling with 32bit Ubuntu with ending support.

---

