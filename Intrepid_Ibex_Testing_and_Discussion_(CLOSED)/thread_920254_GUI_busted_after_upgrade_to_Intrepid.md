---
title: "GUI busted after upgrade to Intrepid"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by defmer on 2008-09-15
so here's how it went down...

1) I change hardy -> intrepid in /etc/apt/source.list
2) I run update manager, I did not select the partial upgrade, instead choose the full upgrade.
3) The update manager in the middle of installation quit citing problems with virtualbox.
4) so I un-installed everything related to virtual box using synaptic package manager. Synaptic asked me to restart and so I did.
5) The system boots only to terminal and I see no GUI. so I thought may be the I should complete the installation. so I use "sudo aptitude dist-upgrade" and complete the installation. 
6) system reboots and still no GUI. 
7) I can see the GDM is running (ps -A). lspci list my Nvidia card correctly. I stop and restart my GDM a number of time and it does so without any warnings/errors.
8) I checked the runlevels (rc2.d and rc5.d) and all of them have GDM to start.

so GDM is running and I individually reinstalled "ubuntu-desktop" and "human-theme" and yet there is no GUI display.

so what do I do now???????????:confused:

---

