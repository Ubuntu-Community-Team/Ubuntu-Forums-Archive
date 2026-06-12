---
title: "&lt;0&gt;Kernel panic - not syncing: Aiee, killing interrupt handler!"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by vibhu on 2006-12-02
Hi, 

I've been trying to get edgy to run on my system for last 2 weeks, and regret having let go of DD. 

My system is :
AMD Athlon 64 3700+
2G RAM
200G SATA HDD - 40G for linux, remaining is WinXp.
Nvidia 7900GT

Dapper Drape was running ok, but then i tried upgrading to Edgy using the updater. That's when everything went wrong. 

The first problem was that it would no longer boot into linux, and gave errors about not finding the root system.

Tried searching for some info, but could not get anything other than the usual acpi=off. that too did not work. 

Downloaded alternate64 and tried installing in OEM mode - as soon as UI is launched everything freezes. 

Tried installin in text mode - install goes fine but does not do post install steps. freezes. 

Installed base text only system - worked. I can login as user and use the command prompt etc. 

upgraded nvidia libs - works fine. 

instaled xserver and it worked :
sudo apt-get install xserver-xorg

then tried to install gnome (apt-get install ubuntu-desktop) and i start getting the above error even before the installation completed. 

Any ideas what i can do now ?

Thanks!

---

### Post by vibhu on 2006-12-02
Got it working.

In case someone runs into this problem, diable the acpi and apci in your motherboard's bios.

---

