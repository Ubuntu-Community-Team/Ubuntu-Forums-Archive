---
title: "[SOLVED] certain web pages not loading"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mkis62 on 2008-10-17
Hello
Upgraded from Hardy to Xubuntu Intrepid since alpha 6 ... was OK, smooth. But now some pages not loading in browser (yahoo mail, gnome-look.org, xfce-look.org and many others). Tried with Firefox, Opera, Seamonkey, Midori. 
Tried pinging ... got response, OK
Hoped was a problem with flash... Reinstalled the current flashplugin (apt-get remove --purge flashplugin-nonfree apt-get install flashplugin-nonfree). Currently I cannot install from repositories, the process hangs awaiting response from macromedia. Downloaded the plugin (on windoze) and after reboot, putting in /var/cache/flashplugin-nonfree/, installed with sudo dpkg --configure -a ... and still nothing, the page hangs on load: "waiting for ..."
Maybe is a problem with some system-wide plugins or with the network manager? I have no crahes except the Clearweather Screenlet (and the weather-related applets from xfce4-panel not getting data...)
Anybody got similar symptoms?
Thanks in advance

---

### Post by inportb on 2008-10-17
What if you tried a browser that does not support Flash at all? Something like w3m.

---

### Post by marmuta on 2008-10-18
I think I've heard this before. Try this thread:
[http://ubuntuforums.org/showthread.php?t=944600]("http://ubuntuforums.org/showthread.php?t=944600")

---

### Post by mkis62 on 2008-10-18
> **marmuta said:**
> I think I've heard this before. Try this thread:
[http://ubuntuforums.org/showthread.php?t=944600]("http://ubuntuforums.org/showthread.php?t=944600")

Thanks 
Lowering the MTU helps (sudo /sbin/ifconfig eth0 mtu 1430)

---

### Post by ronacc on 2008-10-18
I wonder if this is somehow hardware related ? I have no problem with any of the referenced sites , either in this thread or the one cited by marmuta .

---

### Post by mkis62 on 2008-10-18
I don't think it's hardware related. Actually I use a Travelmate 1240 -- with dual boot and in XP all working fine (but a bit slower). Tis is the basic reason why I'm using Xubuntu.

---

### Post by ronacc on 2008-10-18
by hardware related I didn't mean bad hardware ,I ment mabye the driver(s) for certain hardware aren't quite up to par in intrepid . Not everyone is seeing this problem and those that do see it seem to see it with all browsers , I tried the reference sites with Opera , Firefox and epiphany with no problems seen with or without flash (10) .

---

### Post by mkis62 on 2008-10-18
OK ... definitively is a problem with the network-manager. Removed the related items via Synaptic, manually edited /etc/network/interfaces and all is back, working (at this time no need for the network-manager applet). Obviously this must be a temporary solution...

Last edit:
Decided to reinstall network-manager (according to latest infos on launchpad). Works fine with my settings in /etc/network/interfaces.
Only the system tray not showing the nm-applet.

---

### Post by ronacc on 2008-10-18
file a bug on it or add your comments  if there aalredy is one.

---

