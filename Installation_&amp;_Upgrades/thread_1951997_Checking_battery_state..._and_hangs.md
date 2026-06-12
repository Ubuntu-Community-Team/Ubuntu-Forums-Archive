---
title: "Checking battery state... and hangs"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2012-04-03
Hi, 

I tried upgrading from 11.4 to 11.10 by typing 
```

sudo do-release-upgrade

```

It downloaded packages during over 4 hours (slow connection), then it took over one more hour to install everything. Finally it said I had to reboot. 

I typed y for "yes, reboot".

It stopped things, and eventually it reached a stage where it was saying:
checking battery state... OK

And then nothing. I finally pressed the button and it stopped completely. Then I pressed it again to start it. 

Grub functions. The option on top of the list is 30.0.0.17 or something like that. When it is selected, the screen displays "KUBUNTU" with the little dots underneath it, as if it was booting normally. 

Then it reverts to white upon black text. It sais "I'm starting this, I'm stopping that", the last line again becomes "checking battery state". And nothing. I wish it would forget about the battery, the computer is plugged into the mains anyway. 

I tried failsafe options. At one point it said it could not find its screen. I copied xorg.conf.failsafe over xorg.conf. At another point it seemed to be saying the file system was read-only, so it could not startx or do xinit because it could not write the lock file somewhere. I can't install any packages nor even do apt-get update because it does not connect to the internet. 

I tried 
```

sudo service kdm start

```

and when that failed I tried 
```

sudo service kdm stop
sudo service gdm start

```

It seems that whatever I do it always ends up checking the battery state.

Please help.

---

### Post by Mariane on 2012-04-04
bump

---

### Post by Mariane on 2012-04-05
bump

---

### Post by LinuxFan999 on 2012-04-05
I would recommend doing a clean install of Kubuntu 11.10, since your current installation is broken and cannot be fixed.

---

### Post by searchfgold6789 on 2012-04-05
Same issue here. I tried reinstalling my graphics drivers, now I'm going to try to disable my xorg.conf.

---

### Post by Zorael on 2012-04-06
Is there anything of interest logged in **/var/log/Xorg.0.log** and/or **/var/log/kdm.log**?

---

### Post by Mariane on 2012-04-08
Actually, there was something wrong with the battery. The power jack was not making good contact. The computer was plugged into the mains but not charging, and the battery chose to fail during the upgrade, of all times... 

I found a site to help me take it apart:
[http://www.scribd.com/doc/61048900/Taking-Apart-Dell-Vostro-1510](http://www.scribd.com/doc/61048900/Taking-Apart-Dell-Vostro-1510)
and another site to order a power jack from: [http://www.powerjack.us/](http://www.powerjack.us/)

I had to take the laptop completely apart to reach the power jack, whether it will ever work again is anyone's guess.

---

