---
title: "tasksel going nuts"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2008-10-31
I just made a fresh install of Ubuntu Intrepid Ibex (well, I kept my /home partition), so I had to reinstall my lamp stack. This time, instead of installing the packages by hand, I thought I should use tasksel. So I ran:
```
sudo tasksel install lamp-server
```
But, for some reason php was not installed. So I decided to remove whatever tasksel had installed and install the stack myself. So I ran:
```
sudo tasksel remove lamp-server
```
Which, for some strange reason, uninstalled GNOME (!!). I rebooted and there I was, in a command line. Of course, I installed ubuntu-desktop, rebooted and everything is fine now, but why did this happen? I wonder what other things it removed!?

---

