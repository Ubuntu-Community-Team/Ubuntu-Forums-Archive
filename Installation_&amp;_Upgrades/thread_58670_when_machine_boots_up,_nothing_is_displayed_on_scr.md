---
title: "when machine boots up, nothing is displayed on screen"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by westsiderailways on 2005-08-21
i have installed ubuntu on an old machine which was running windows 98se without any problems.  the installed went ok (did'nt have other machine running at the time of installation, so no network).
after the part installation it told me to remove the cd and rebboot. did that and then it installed all the packages it needed, after that it reboot and my LCD screen told me (out of range) flashing on the screen. so i tried my crt and after booting the screen just goes blank.

---

### Post by dberetta on 2005-08-21
i have an old amd 700Mhz i am using a crt screen also. 
When i first boot, i get the grub menu for half a second. after that my screen goes blank until xserver kicks in after the system is booted. If you here the hard drive running give it a little bit and see if it doesnt come up after that. 

if that doesnt help, i would wait a little longer to see if someone else has had the same problem.

---

### Post by Thulemanden on 2005-09-12
In that situation I would look into my vide drivers.

---

### Post by az on 2005-09-12
X misditected your monitor's capabilities.

Boot into recovery mode and type
dpkg-reconfigure xserver-xorg
and try different monitor settings.  Just plugging in your crt and doing it should detect your crt settings and it should work the first time.

Type 
init 2
to get into X (Gnome)

If you still get nothing, hit CTRL-ALT-F1 and log in, run
init 1
and try dpkg-reconfigure xserver-xorg again with different settings.

---

