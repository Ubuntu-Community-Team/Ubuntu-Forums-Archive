---
title: "Upgrade 14.10 - Desktop loaded but not Unity"
date: 2014-11-18
forum: Installation &amp; Upgrades
---

### Post by noonio on 2014-11-18
Dear all, 

I have recently upgraded from 14.04 to 14.10 with the graphic tool. 
So far so good, apparently everything went smoothly and I was asked in the end to reboot. 

Sadly enough, on reboot what happens is: 
BIOS loading: OK
Grub loading: OK
Boot on Ubuntu 14.10: OK (I don't remember the version of the kernel whatever)
Logo Ubuntu: OK
Desktop with nice wallpaper that I had previously set: OK

[B]BUT, I have no decorator whenever I open a folder.
I also do not have Unity loading (well my diagnosis here), there is no bar at all, on the left side and on the top side of the window.[/B]

I've tried already the following: 
Reinstall my graphic card driver, fglrx: with purge options while doing apt-get remove
--> Same result, no Unity, but nice wallpaper

Install the proprietary ATI driver: worse behaviour, error while loading the X server (I have not copied the log, I should I know, but I'm writing this from my workplace).
--> Only mouse pointer showing

I don't remember exactly how, but I have managed somehow to remove the ATI drivers and to load default ones
--> Desktop + Unity + Decorator BUT very very laggy naturally... and oddly enough sound only while I'm in tty and not in X environment

At some point, I have reinstalled also drivers + compiz + default behavior of compiz, without better results.

I have tried to find out some information related to my problem, but with poor success :(
Do you maybe have some advices or a guideline that I might follow ? 

I would love not to ****ly reinstall my system, I'm too lazy. 

Regards, 
Renaud

---

### Post by mörgæs on 2014-11-18
If you are lazy then a reinstall could be the best option. Sounds like you are spending lots of time troubleshooting.

---

### Post by noonio on 2014-11-19
Well I understand what you mean, re-installing might be the easiest way to have a new fine OS. 

BUT, on the other side, I meant by lazy that I really do not want to spend some time installing everything afterwards. 
Let alone configuring everything, even if I keep my configuration files, there will be some discrepancies. 

My system is like 4 years old, I like it, it was just fine. I will never ever again update my system so soon after official release :(

No other suggestion ?

---

### Post by folky2 on 2014-11-19
hello,

@noonio
i have  exactly the same problem on my pc (upgrade 14.04 TLS =>14.10)

my config:

AMD A6-3500  //  AMD Radeon HD 6530D

reinstall 14.04 TLS is the one solution for me.

many problems for the 14.10 .

---

