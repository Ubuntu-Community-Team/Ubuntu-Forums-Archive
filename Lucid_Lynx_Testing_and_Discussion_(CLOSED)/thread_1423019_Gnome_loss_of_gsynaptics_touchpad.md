---
title: "Gnome loss of gsynaptics touchpad"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by richs-lxh on 2010-03-06
[COLOR=Red]Solved via a reinstall of a fresh Alpha3[/COLOR] (Problem occurred after upgrade from Alpha2 to Alpha3)

After playing with this for several days and exhausting the fixes/workarounds I could think of, I decided to ask on the forum for help.

I am testing Lucid Gnome on and Acer Aspire 3004, and until a few days ago it was ok, then an update wiped out my touchpad mouse.

**Bug Report:**
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/532173](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/532173)

**What I have tried and conclusions:** 
Configure/Enable manually with gpointer-device-settings
Configure/Enable manually with gsynaptics
Configure/Enable manually via the commandline

All attempts show the touchpad as active and working. I got it to work at GDM to be able to login, but as soon as it gets to the Gnome desktop, it's gone. Checking all settings show it should be working.

**Other Desktops** **/ Login Managers**
I removed Gnome (Ubuntu Desktop) and tried Xfce (Xubuntu-desktop) and Kde (Kubuntu-Desktop) as well as trying with GDM and KDM.
Kde - Works fine
Xfce - Works fine
Reinstall Gnome - No touchpad
I was thiking of the possibility of it being a GDM problem, but it made no difference if I used KDM. Incidentally, I also had the GDM Double Login problem which many have reported, this also does not affect Kde or Xfce.

After trying everything else I am pretty stumped as I have no idea what Gnome does once it loads, regarding hardware. Otherwise I would dig deeper and try to find where in Gnome the touchpad could be manually enabled on the back-end, as the front-end guis all report it as working.

All the log files are attached to the bug report above, and if you need any more information, let me know.

Thanks in advance,

rich

---

