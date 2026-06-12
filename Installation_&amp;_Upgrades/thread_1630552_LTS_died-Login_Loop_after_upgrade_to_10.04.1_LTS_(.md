---
title: "LTS died-Login Loop after upgrade to 10.04.1 LTS (had a fresh CD 10.04 inst. before)"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by AstroPhysik on 2010-11-25
[SIZE=2]Hello,

I had a perfectly working  10.04  LTS and updated it with synaptic to 10.04.1 LTS (around 1st Nov 2010..)
After a day i could not log in to the desktop and it looped again and again to the gdm login-screen.. 

I'm trying to fix this since nearly 4 weeks.., but i did not get far. **Even a fresh CD install and afterwards doing all the synaptic updates leads to the login loop...**

At first i thought this all happens because of the error:
[/SIZE][B](EE)AIGLX error: dlopen of usr/lib/dri/nouveau_viex_dri.so could not be found or opened.
[/B][SIZE=2]
But after the fresh 10.04 CD installation, i found out, that the error was already there, but had no effect!


i tried: 
sudo adduser, if there's a problem with only one user
swichting back from nVidia -nouveau driver to VESA driver or the failsafe driver...nothing worked
even deinstalling gdm and using wdm has no effect. (i maybe can login but there's a white screen, instead of a black screen which occured at gdm..)
i had a new 2 TB Harddisk: df says < 1%..

My techn specs:
[/SIZE]```
ubuntu 10.04.1 Kernel: 2.6.32-25-generic #45 ubuntu sat oct 16, 19:48:22 UTC 2010 - i686)

lspci | grep VGA 
01:00.0 VGA compatible controller: nVidia Corporation NV17 [Geforce4 MX 460] (rev a3)
```[SIZE=2]

Has anyone [/SIZE][SIZE=2]another idea?
Or did one [/SIZE][SIZE=2]of the login -loop posters solved this problem without skipping the release?

I really ran out of options, except: reinstall ubuntu 9.04 and live with no updates, skip the LTS and become a Unity-Beta Tester *oh no..* or try 10.10 but i do not want to leave a release every 12 months or so.. i want to stay with the 10.04 LTS!!! (if it is possible:confused:)

Please, please help me, 
Astrophysik
[/SIZE]

---

### Post by dino99 on 2010-11-25
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

---

### Post by AstroPhysik on 2010-11-25
the attachments:

Xorg.0.log_Lucid_10.04_fresh_cd_installation_without_any_updates     -   is the log after the fresh cd install..
Xorg.0.log_with_all_10.04.1LTS_updates                                                 -   after the updates 
Xorg.0.log_defect                                                                                       -   after a day or so..


regrads AP.

---

### Post by AstroPhysik on 2010-11-25
> **dino99 said:**
> remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

Hi!
there is no xorg.conf, it comes only (in my rescue attempts some weeks before..) if i try to install another noveau, or nv or vesa driver, but after a fresh cd + synaptic upgrade to 10.04.1 LTS there is no xorg.conf.

but thanks for the tip.
AP

---

