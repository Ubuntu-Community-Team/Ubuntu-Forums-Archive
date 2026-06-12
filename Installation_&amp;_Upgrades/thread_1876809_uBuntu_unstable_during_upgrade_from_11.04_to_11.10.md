---
title: "uBuntu unstable during upgrade from 11.04 to 11.10 (upgrade failed ) - cannot revert"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by sugumar on 2011-11-06
My ubuntu kept on asking for upgrade to 11.10. Yesterday, I just clicked  upgrade thinking that everything would go fine. It started upgrading and  downloaded 1 GB files. Finally, it said that that there was an error  and the system (ubuntu) was unstable and the packages would be revert  back (it will run some commands which I Forgot). But,  that didn't  happened and when I restarted the machine, I could see nothing. I see  only "Insert the boot disk". After that I tried with the ubuntu CD.   Ubuntu reported that I was using 11.10 and there were option  (upgrade  11.10 to 11.04). I checked the option upgrade 11.10 to 11.04 and it  started installling. After some point I got the error message saying  that the installer crashed.
I request you to please help me to revert my machine back to the stage before upgradation. My machine have windows and ubuntu.

Thanks and regards
Sugumar

---

### Post by zvacet on 2011-11-07
Boot in recovery mode and type

```
apt-get update && apt-get upgrade
dpkg --configure -a
apt-get -f install
```

Post output here if you get any errors.

---

### Post by bdmurray on 2011-11-18
The fact that an option to "Upgrade from 11.10 to 11.04" appeared in the installer is a bug and this actually does not work as you've observed.  I've documented steps to recover your system by reinstalling Ubuntu 11.04 in the following [bug report]("https://bugs.launchpad.net/ubuntu/natty/+source/ubiquity/+bug/891711").

---

