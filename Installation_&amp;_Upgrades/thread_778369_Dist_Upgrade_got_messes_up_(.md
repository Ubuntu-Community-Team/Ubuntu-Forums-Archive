---
title: "Dist Upgrade got messes up :("
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by pt1989 on 2008-05-02
Hi,
I've been using Ubuntu 7.10 and it rocks...
Last night I chose to do the dist upgrade and let the PC stay on the whole night and set it to shutdown at a select time... 
I guess the packages were all done with downloading and the PC shut during installation or mebbe even that was complete... but now Ubuntu is acting fuzzy like i can't login i get the GUI screen albeit with a lower resolution... however the system gets stuck at the orangish peach colored blank screen after logging in rendering Ubuntu useless.

Is there any way as to how i can fix this problem by either doing a repair with a 7.10 CD or a proper upgrade with a live CD of 8.04.
But it seems like 8.04 upgrades is problematic so far, so i'll keeo out of it.

I hope i get a solution asap coz i have to use Windows till then... :(


BTW it's **messed ** up sorry for the typo...

---

### Post by pt1989 on 2008-05-03
i tried doing this in Recovery mode:

```
apt-get update
``` &&
```
apt-get dist-upgrade
```

both threw dpkg was bricked and stuff

```
dpkg --config -a
```

The process went on for some time and then threw some errors... 
like certain packages not configured properly and stuff but i don't know what to do further.


Now in the GRUB bootloader menu i get another 2 options with Ubuntu 8.04 and a diff kernel and the old 7.10 is renamed to 8.04.
However this hasn't solved my problem, only that now the resolution has increased (probably cause more pacakges were configured) but not in the new kernel version only in the old one.

---

### Post by pt1989 on 2008-05-04
can anybody help me?? else i'll have to format and start over again

---

### Post by bulldog on 2008-05-04
> **pt1989 said:**
> can anybody help me?? else i'll have to format and start over again

The fastest way is to download the 8.04 ISO and do a fresh install.
If you have broad band internet,you will be up and running within one hour.
Sorting your problems out,could be fun and you can learn a whole lot,but it's certainly not the quickest way.

---

### Post by pt1989 on 2008-05-04
ok so i go for a 8.04 or wat... btw kubuntu has got KDE4? like officially in the 8.04 Hardy heron release... and also will I have to download the *.deb packages again or i can reuse the ones in the cache 
/var/cache/apt/archives 
for either ubuntu or kubuntu hardy heron releases coz i got like a gig of packages that's why?

---

