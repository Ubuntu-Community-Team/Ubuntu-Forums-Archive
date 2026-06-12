---
title: "Install package errors in Hoary 5.04"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by bullraiser on 2005-10-04
Hi,

  I installed Hoary 5.04 (through shipped CD's) and everything went fine, until I got few package errors on base configuration. Then I reboot and it prompted to insert the install boot CD. Even then, it throwed me I/O error and finally i used Ctrl+Alt+F1 option to login as root and started the Gnome session. Most applications are working fine, but I couldnt update my system, as the update manager throws me to fix some broken errors. 

  When I tried, it rejects as Unauthorized. Futher, I couldnt login as the user I created on install setup whereas I could login to Gnome desktop only through root user.
Guys, I need some way out. Could someone figure what could be the reason. But anyways, I am enjoying the Linux and the fast with my poor computer (128MB RAM :( ) is amazing. I think, I might reduce my dual boot to windows when i finished fixing broken errors here.

Cheers--

---

### Post by mlomker on 2005-10-04
It'd probably be best to start over and reinstall.  You didn't run out of disk space, did you?

---

### Post by bullraiser on 2005-10-05
If this could be the only reason, if you could figure out, then I would try reinstalling. But, the problem is that, I end up to the same path whenever I try reinstalling it again.

Also, I am not quite sure, why the Update Manger is prompting to insert the install boot CD when it can connect to Net. Any ideas to automatically download the package from Net and install it and which tool / command, should I run to do so?

Thanks --

---

### Post by mlomker on 2005-10-05
> Any ideas to automatically download the package from Net and install it and which tool / command, should I run to do so?


By default it is going to prompt you for the CD rather than using the Internet.  You can either remove the first line from the /etc/apt/sources.list or remove the CD 'repository' from within Synaptic.

---

