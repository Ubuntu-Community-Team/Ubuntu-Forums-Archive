---
title: "New ubuntu user, 2 video cards issue"
date: 2015-07-25
forum: Installation &amp; Upgrades
---

### Post by florin11 on 2015-07-25
Ok!

I tried some time ago to install ubuntu with a friend that has some experience with ubuntu and practicaly he installed it and tried to manage my 2 video cards issue. Well, i have this laptop [http://www.toshiba.com.ro/contents/ro_RO/PRODUCT_DESC/files/1161625.pdf](http://www.toshiba.com.ro/contents/ro_RO/PRODUCT_DESC/files/1161625.pdf) and i want to install and use the Nvidia video card, on windows i needed to install first the intel driver and after that the nvidia and from the nvidia driver select to use the high performance video card. Simply i want to play dota and my nvidia gefore card let's me do this. How can i properly install and use that video card? 

I would appreciate any help i can get, maybe i can get ubuntu working because it's my best option, not making my hardware go "heat - sun mode" , i know ubuntu makes things easier.

I apologise in advance for my broken english  and for my clumsy explanations, if any of you understood my problem and can help me with some information i will be very thankful.

Regards!

---

### Post by dino99 on 2015-07-25
a relative old howto: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)   but it might help a bit
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

---

### Post by florin11 on 2015-07-25
First of all , how can i know that i have the Intel and Nvidia drivers instaled and up to date?

---

### Post by Vladlenin5000 on 2015-07-25
Do you have Ubuntu already installed or are we still asking [theoretical questions]("http://ubuntuforums.org/showthread.php?t=2287871")? If the former what did your friend tried? There's a chance you might need to undo part or all of it :biggrin: (sorry. couldn't help... I do feel your pain though, it's just this things often amuse me).

Generally and theoretically, the only differences comparing to the Windows method you so assertively described are this small details:
a) You don't need to install the Intel drivers. Intel Graphics drivers are open source therefore can be included in the distro and installed by default, no user input needed whatsoever (in 99,99% of the cases and yes, I've dealt with a nightmarish Acer once that belong to the 0.01%).
b) You need to install the proprietary Nvidia drivers like in Windows (this isn't the difference).
*Nouveau*, the default open source driver - not from Nvidia - for Nvidia cards/chips, is the one you use until you change for the proprietary ones. You're better with proprietary Nvidia drivers for any new or relatively new hardware and it's (almost) a *must* for games.
The difference is how you install the drivers. It's easier and faster than in Windows (more about that later after you tell us what Ubuntu release you installed; for that hardware newer is better).

Then you would do the same as you do in Windows to toggle the graphics with Nvidia X Server  Settings. I'm not sure if it's still the case but you may need to reboot whereas in Windows it works seamlessly.

This usually works -> [https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics) but you most likely will need different, newer, drivers: 352.xx

---

### Post by Vladlenin5000 on 2015-07-25
> **florin11 said:**
> First of all , how can i know that i have the Intel and Nvidia drivers instaled and up to date?

The GUI way: System Settings > Software & Updates. Find the rightmost tab, Additional drivers.

Please post your Ubuntu version (actually release number) and what nvidia versions are offered . Often it's the other way around but for your hardware 15.04 is preferable than 14.04 LTS although the hybrid settings should work as well in 14.04. You'll need the newer driver though but it's very easy anyway.

---

