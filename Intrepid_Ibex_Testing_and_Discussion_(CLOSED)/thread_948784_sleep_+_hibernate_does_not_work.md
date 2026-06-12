---
title: "sleep + hibernate does not work"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mveltre on 2008-10-15
hi,

I've just upgraded to 8.10 from 8.04 on my hp/compaq nx7010 notebook. 

If i try to hibernate the system, the "locked screen" displays and ask me for my password. In the logs I can't see a problem, drivers are going to sleep (e.g. network manager) and waking up 1sec after. 

The "sleep" option is not displayed in the new menu for shutdown/log-off and also not available in energy options.

Any ideas?

Thanks,
Markus

---

### Post by mveltre on 2008-10-15
just a notice:

echo -n mem > /sys/power/state 

does work, the system goes to sleep mode. But doesn't wake up again correctly, which i expected. But "sleep" itself is supported by hardware and kernel...

Markus

---

### Post by PinkFloyd102489 on 2008-10-15
I have about the same problem on my laptop here. It'll sleep and hibernate but wont come back from those states. Only way to get it back is to do a hard shutdown (hold down power button) and restart the machine.

---

### Post by mveltre on 2008-10-15
I don't belive that's the same issue - as my "manual" approach to send the laptop to ACPI_S3 never works perfectly ;) It is just the check, whether hardware and kernel whould support this functionality ...

---

### Post by mveltre on 2008-10-16
by-the-way:

I should have menitioned, that I'm using a german version of ubuntu. But the log-out buttons are in english?

Markus

---

### Post by eyelessfade on 2008-10-16
When I started using Ubuntu 8.10 at alpha 4 sleep worked on my computer. Nvidia 8800gts and intel cpu. But since Beta 1 it has not. I have not tried hibernate since I have 4 times as much ram as swap :P

Now the computer goes to sleep, but never come back. I must say I miss the sleep function.

---

### Post by screaminj3sus on 2008-10-16
Sleep never worked right for me in ANY distro including ubuntu until intrepid. Now it works perfectly on my gateway m6862 laptop (and this is a brand new laptop too)

I do think this needs to be a priority to get it working on as many laptops as possible though, because ubuntu is essentially useless on a laptop if sleep does not work.

---

### Post by mveltre on 2008-10-16
with 8.04 (hardy) it worked for me, in 8.10 (intrepid) is not... thats the problem ;) I know there were some changes in the kernel from 2.6.24 to .27 regaring ACPI-Sleep, but to be honest i thought it's getting better ;)

Does anyone have an idea how to start debugging into this problem?

---

### Post by Kazade on 2008-10-16
Same problem here, the laptop *tries* to sleep (the screen goes blank) then it comes back. Last night I closed the lid thinking it would sleep, only for the battery to be dead a couple of hours later. Everything worked perfectly in Hardy. I haven't had a chance to investigate it yet or search launchpad.

---

### Post by mveltre on 2008-10-16
Now I tried it with booting from the last Ubuntu-Beta CD. There, suspend works! 

This means, something is wrong somewhere in my configuration? Any ideas?

Thanks,
Markus

---

### Post by henriquemaia on 2008-10-26
I also have sleep problems. The laptop goes to sleep, but upon turning on, the screen remains blank.

---

### Post by lswest on 2008-10-26
Sleep works for me on an HP DV6545eg, and didn't use to.  The only change from then to now is the fact that I no longer use ndiswrapper and use the Nvidia 177.80 drivers for hardware (the issue was always waking up the graphics card again, and when it did wake up...wireless wouldn't).

Just my experiences.

---

