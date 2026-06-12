---
title: "boot problem after upgrading!!"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by vinay nadig on 2010-10-08
hi, i have been using ubuntu 10.04 for a few months now.. just yesterday i upgraded to the 10.10 beta version. i dual boot windows and ubuntu in my 160 gig hard drive. after the upgrade, update manager asked me to restart and i did so. Now the problem is that instead of the OS choices that i usually used to get when i started the comp have gone and the system gets booted to grub commandline. i am not very familiar with the grub commands and need help restoring my OS menu choices. ubuntu is installed in sdb5 and windows on sdb3.  any help would be appreciated. Thnx in advance!! :)

---

### Post by zvacet on 2010-10-08
If you can login in terminal you type

```
startx
```

or

```
sudo /etc/init.d/gdm start
```

Ubuntu 10.10 in not final yet so you can expect some inconvenience.

---

### Post by sikander3786 on 2010-10-08
How does the command line look like? Something like this?

Grub>

If that's the case, I doubt **startx** will not work as **zvacet** suggested above.

Boot into a live CD and post the output of bootinfo script as per instructions.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Do all this if you see a Grub> prompt. No need if you can boot into the shell that looks something like you@computername:- $

---

