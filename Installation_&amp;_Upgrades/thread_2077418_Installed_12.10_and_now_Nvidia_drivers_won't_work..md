---
title: "Installed 12.10 and now Nvidia drivers won't work."
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by Cammy on 2012-10-28
I was running 12.04 and on Friday I installed 12.10 from USB.  Everything went fine, but I'm having some video problems.

I am running an nvidia 9500GT with dual monitors and a KVM switch that switched the primary monitor between my ubuntu machine and my Win7 machine.

When I go into software sources in Ubuntu , then to the "Additional Drivers tab and enable the nvidia drivers, a reboot gives me only one working monitor and no titlebars, no menus, no nothing except for the desktop.

Fortunately a right click gets me to the change background screen, and from there I can get back to software sources and get back to the Nouveau driver.

I'd like to figure out how to use the nvidia driver, because with the Nouveau driver, when I switch to my windows machine and ubuntu can't "see" my primary monitor, it kicks my resolution down to basic VGA settings (which is a problem of it's own).

Any advice on getting the nvidia driver to work?  It worked fine in 12.04.

---

### Post by bogan on 2012-10-28
Hi!", **Cammy,**

*{Assuming you can get to a Terminal, ['Crtl+Alt+t' or 'Crtl+Alt+F1'] }*

There is a bug around that causes the problem you Posted, due to the 'linux-headers-generic' not being installed. 
Run:```
 sudo apt-get install linux-headers-generic
```If it says " already the latest version" then the cause is something else.

If it installs, then:```
sudo apt-get remove --purge nvidia-current # substitute package name you installed
sudo apt-get install nvidia-current # substitute package name you want installed.
```Then reboot.

Chao!,** bogan.**

---

### Post by Cammy on 2012-10-28
Thanks bogan!  They installed, so let me see how that goes.

EDIT: Yep! Looks like I'm on the proper driver now.  Thanks!

---

