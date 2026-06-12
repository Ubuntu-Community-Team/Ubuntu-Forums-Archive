---
title: "Installaton problem"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by Paulw33 on 2007-08-04
Yes, I a new user and after installing Ubuntu with no problems, I got hung up trying to visit Firefox and had to pull the battery from my laptop to get out of it.
Inserted install disk back in, booted and received 109 updates which went OK. after the restart it hung up again, booting up.I then did a recovery run and got this message:
Code bad EIP value. EIP {<000000000>} 00x0 ss:esp 0068:c98110ab8 <0>kernal painc-not syncing-fatal exception in interrupt.
Can someone help.
Paul

---

### Post by dabl on 2007-08-05
> **Paulw33 said:**
> 

I got hung up trying to visit Firefox and had to pull the battery from my laptop to get out of it.



There is no good way to know what happened to your operating system's configuration when you did that -- kinda like doing brain surgery with an arc welder.  There's a far better way to deal with a hung-up application in Linux -- you kill the process, not the system.

In Ubuntu, use System>Administration>System Monitor, click the "Processes" tab, scroll down to "firefox-bin", highlight it, and click the "end process" button in the lower right.  This will end Firefox but everything else will keep running.

So, after you have re-installed Ubuntu, if you have a problem with a stuck process in the future, fix it like this and maybe this will be your last time to re-install.  :)

---

### Post by Paulw33 on 2007-08-05
Thanx Dabl....I'll remember, but when it hung up on the Firefox thing, I couldn't move the pointer(mouse). Re-install works, am running fine now...hopefully.

---

