---
title: "Ubuntu 8.4 to 8.10 installer went wrong"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Declanthedork on 2008-11-01
So, I just downloaded the 8.10 installer off the Ubuntu website and put it in and when it finished, it had to restart. So the computer restarts and when the Ubuntu loading screen finishes, it gives me what looks like a command line list saying this:
> *Starting anac(h)ronistic cron anacron      [OK]
*Starting deferred execution scheduler ATD         [OK]
*Starting periodic command scheduler crond         [OK]
*Checking battery state...                         [OK]
*Running local boot scripts (/etc/rc.local)        [OK]

And it just stays like that. It hasn't done anything in hours. I've restarted the computer and it still comes up with the same thing after GRUB 1.5 and the loading bar. Thanks for your help! :mad:

---

### Post by hyperdude111 on 2008-11-01
Those messages are normal for the boot process, I have had them in hardy and intrepid...but I dont know what your problem is. There might have been a problem with the install you could try again.

Good luck

---

### Post by gjoellee on 2008-11-01
Yes there seams to be an issue with xorg to me. Lets try running xfix, see how here: [http://kshoster.net/node/18](http://kshoster.net/node/18)

---

