---
title: "Machine to up to date for Ubuntu?"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by Goonie on 2006-04-01
Hi all

I am looking for the ideal laptop to replace my old one which had problems with Ubuntu and I took an Acer 5652WLMi home yesterday to test (I'm lucky because I run a computer retail store and can test things before I buy them). This machine has the following specs:

Intel Core Duo CPU 1.66GHz
15.4" screen (1280x800)
2GB DDR2 Ram
100GB Sata hdd (5400rpm)
Nvidia GeForce Go 7600
Wireless lan 

First of all the xserver failed so I had to reconfigure xorg using the vesa driver and a resolution not native to the screen because 1280x800 was not an option when using the vesa driver (nv failed to start completely). So now I have a desktop in a low resolution. 

When I try lspci most of the devices come up as unknown devices, including the wireless.

Can this machine be set up with Ubuntu?

I'm a linux newbie at best so pardon me if my questions sound silly.

Thx
Gunnar Freyr

---

### Post by Bartender on 2006-04-01
Goonie -
You're probably one of a mere handful of people who have tried installing Ubuntu to a Core Duo machine.  If you'll send me that laptop, I'll be more than happy to dink with it and tell you what I found.  I'll admit that I'm not good with Linux but hey, willing to try ;)

---

### Post by Goonie on 2006-04-02
Hmm.....

I'll give it some thought hehe....

---

### Post by Bartender on 2006-04-02
Seriously, Goonie -

Google "linux laptop" and you'll find sites that list people's results with various distros and notebooks.   
But info on brand-new Core Duo machines is likely to be scarce for a while.  That's where you could offer some valuable input.  People following this forum would greatly appreciate hearing which new notebooks worked.  
You might even generate a few sales.

---

### Post by nocturn on 2006-04-03
[QUOTE=Goonie]Hi all

I am looking for the ideal laptop to replace my old one which had problems with Ubuntu and I took an Acer 5652WLMi home yesterday to test (I'm lucky because I run a computer retail store and can test things before I buy them). This machine has the following specs:

Intel Core Duo CPU 1.66GHz
15.4" screen (1280x800)
2GB DDR2 Ram
100GB Sata hdd (5400rpm)
Nvidia GeForce Go 7600
Wireless lan 

First of all the xserver failed so I had to reconfigure xorg using the vesa driver and a resolution not native to the screen because 1280x800 was not an option when using the vesa driver (nv failed to start completely). So now I have a desktop in a low resolution. 

When I try lspci most of the devices come up as unknown devices, including the wireless.

Can this machine be set up with Ubuntu?

I'm a linux newbie at best so pardon me if my questions sound silly.

Thx
Gunnar Freyr[/QUOTE]

Have you installed the nvidia drivers?  

If so, try adding Option "IgnoreEDID" "1"

---

### Post by Clopy on 2006-04-03
goonie, have you tried using nvidia's drivers?

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by Goonie on 2006-04-03
I'll give the nvidia drivers a go when I get a chance... 

I'm getting married you see and for some strange reason my fiance seems to think I should be involved in the preperation :=P 

Once that little detail is out of the way, I'll be back....

Goonie

---

### Post by makro on 2006-04-03
Hi Goonie!
I have an Acer 5652wlmi too!
Dual Core works fine with smp kernel.
Nvidia drivers doesn't work... X starts but a lot of vertical stripes appear instead login manager
Soundcard works but I can't hear CD from cd player (ksCD)
Card reader doesn't work
Wireless should work (search for intel wireless 3945 on this forum)
Bluetooh is ok

---

### Post by Goonie on 2006-04-03
[QUOTE=makro]Hi Goonie!
I have an Acer 5652wlmi too!
Dual Core works fine with smp kernel.
Nvidia drivers doesn't work... X starts but a lot of vertical stripes appear instead login manager
Soundcard works but I can't hear CD from cd player (ksCD)
Card reader doesn't work
Wireless should work (search for intel wireless 3945 on this forum)
Bluetooh is ok[/QUOTE]

Thanks makro

I'm going to wait for Dapper then before buying such a brand new type of laptop and hope things will be a bit farther along by then.

Goonie

---

### Post by makro on 2006-04-03
rumors say nvidia's new drivers will be out in a couple of weeks...
kernel 2.6.17 probably will have full support for 5652 mainboard

---

### Post by makro on 2006-04-05
I've just dist-upgraded (2.6.15-20)

soundcard is better managed (no mic boost for now)
battery status is now active
still waiting for nvidia drivers...

---

### Post by Goonie on 2006-04-09
I think I'm going to wait a bit before I upgrade to the 5652WLMi. Going to wait for Nvidia to release drivers and possibly a stable Dapper as well.

Good luck with your machine makro =)

Regards
Goonie

---

### Post by makro on 2006-04-09
Dear Goonie...
NVidia released new drivers on Friday...
Now this notebook is close to perfection!

See U soon!

---

