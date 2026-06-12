---
title: "No graphical login after upgrade from Hardy to Ibex"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by 81wtbvi02 on 2008-10-30
Everything looks normal, until there is only one black box on progress bar of splash screen.  Then, screen goes black for a few seconds, then switches to a text/console screen, with the boot messages.  The last one is "Starting NTP server ntpd".

I have to switch to another tty screen with ALT F2, login there, then run startx to get to my desktop.  To shutdown or reboot, I have to use CTRL-ALT-BACKSPACE to return to tty, then shutdown or reboot from command line.

here is the output of "uname -a":
2.6.27-7-generic #1 SMP Thu Oct 30 04:12:22 UTC 2008 x86_64 GNU/Linux

---

### Post by acracker on 2008-10-31
In either the console or the graphical version, try updating your system 'sudo apt-get update' then 'sudo apt-get upgrade'. I had this same problem but it was fixed after doing those.

---

