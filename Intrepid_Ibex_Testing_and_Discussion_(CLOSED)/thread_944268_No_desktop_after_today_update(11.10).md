---
title: "No desktop after today update(11.10)"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chacham23 on 2008-10-11
I tried to restart with all kernels I had 4,5,6,7 and nothing no desktop I think it nautilus problem I will try to reinstall..

someone got that problem also?

---

### Post by iponeverything on 2008-10-11
If you have internet connectivity:
do a  
 <ctl> <alt> <F2>
login
sudo apt-get update
sudo apt-get upgrade

If not:

```
cd /var/cache/apt/archives/

sudo dpkg -i libxi6_2%3a1.1.3-1ubuntu2_i386.deb
sudo dpkg -i ubuntu-desktop_1.119_i386.deb fast-user-switch-applet_2.24.0-0ubuntu2_i386.deb gnome-applets_2.24.0.1-0ubuntu1_i386.deb gnome-applets-data_2.24.0.1-0ubuntu1_all.deb gnome-panel  gnome-control-center_1%3a2.24.0.1-0ubuntu3_i386.deb gnome-session_2.24.0-0ubuntu1_i386.deb nautilus_1%3a2.24.0-0ubuntu2_i386.deb nautilus-cd-burner_2.24.0-0ubuntu1_i386.deb gnome-panel_1%3a2.24.0-0ubuntu1_i386.deb gnome-panel-data_1%3a2.24.0-0ubuntu1_all.deb gnome-settings-daemon_2.24.0-0ubuntu1_i386.deb
```

---

### Post by chacham23 on 2008-10-11
I connected to home network(the modem is connected to the other computer - XP).

With graphical interface I click on th "auto eth0"(I think) and it recongnize the other computer.

my Q is how I do this on command line(-no desktop):confused::confused:

thanks :)

---

### Post by chacham23 on 2008-10-11
someone?? bumped

---

### Post by iponeverything on 2008-10-12
Open a Virtual terminal with <CTL><ALT><F2>

---

### Post by wyth on 2008-10-12
You can also try going into a previous kernel (click Esc on boot to get the options). The 2.6.24-21 kernel update knocked my desktop offline as well -- I just get a mouse, a flat screen (no icons, wallpaper, nothing), and a box as if I'd booted into safe/recovery, but there's not command line.

Booting into the previous kernel works fine.

---

### Post by wgrant on 2008-10-12
Ensure that you have ubuntu-desktop and xserver-xorg-input-all installed.

---

### Post by wyth on 2008-10-12
I think you can ignore my earlier advice -- didn't realize this was for 8.10.  My issue was on 8.04.

---

### Post by andreselsuave on 2008-10-12
I also have the exact same problem . I haven't tried the fix proposed above but I will tomorrow. Have you tried the fix? Can u please notify me if you get to fix it? thank you!

---

### Post by Capoeira on 2008-10-13
Hi,

I've simular problem after updateing Kunbuntu-Inrtepid.
During the update-process i was asked to confirm the replacement of a configuration-file, which i confirmed. for my chame i dont't remember the name of this file (din't write it down).
Now, after reboot ans login, i get a white screen first and then black and white windos with no contend, no panel, only mousecurser.
I'm about 90% sure that this is because the new configuration-file enabled the window-effects of KDE (my graficcard doesn't support open-gl) and caused this issue.
apt-get update and upgrade didn't solve it.
Now can anybodey help me out:

What is the configurationfile for the systemsettings called (searched for ecently changed files in .kde but didn't found it)?

or,
Does anybody now how to disable KDE-window-effects in Konsole?

Please help me as i run here the live-cd now. I want my Kubuntu back ;-)

---

### Post by Capoeira on 2008-10-13
ok, i solved this renaming home/.kde/share/config into home/.kde/share/configold. And than after successfully loading kde, renaming configold to config again. disabled the window-effects and relogin.

---

