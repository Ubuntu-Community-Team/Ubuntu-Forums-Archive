---
title: "Desktop empty after Update"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by hamena314 on 2008-11-18
Hi there!

I use Ubuntu 8.10 and did several updates 2 or 3 day ago. After rebooting the machine, my Desktop shows nothing, except the background-picture.
The panels are gone, I cant do a right-click, no terminal, nothing.
My touchpad does also not work.

With a terminal-session I could start the panels manually by typing "gnome-panel". But when I reboot they remain absent.

I removed gnome-panels and ubuntu-desktop with
"sudo apt-get autoremove gnome-panels"
"sudo apt-get autoremove ubuntu-desktop"
and reinstalled it. Nothing changed.

I then installed the xubuntu-desktop and it works normal. With another testaccount I could log in to a ubuntu gnome session, but the panels stay absent also. It seems to be a bigger problem than just a crippled configuration file.

The only error message I get is when I start the gnome-panel manual in a terminal-session:

```
gnome-panel:8733 
atk_bridge_WARNING: AT_SPI_REGISTRY was not started at session startup
atk_bridge_WARNING: IOR not set
atk_bridge_WARNING: could not locate registry
```

When I hit CTRL-ALT-DEL a window pops up and I can log out.

No idea what I can do next or how to remove the faulty updates. :(

HAVE PHUN!

---

### Post by timjohn7 on 2008-11-18
I had the same problem and after 3 VERY frustrating days, I did a fresh installation.  I could not find a solution despite lots of help and attempts to fix things.
You can follow the thread in [http://ubuntuforums.org/showthread.php?t=982694](http://ubuntuforums.org/showthread.php?t=982694)
Perhaaps if enough people have the problem, something will get investigated.  There seems to be some serious issue here.

---

### Post by hamena314 on 2008-11-18
Actually I just solved my problem...

Right befor I updated my system (which is where something went wrong), I played around with gnome-orca, the accessibility-tool with a magnifier. It did not work, so I just ignored it - since it didnt start - and did the updates. Rebooting and my desktop was gone...
After googling and reading through the errormessages I am sure orca was still running in the background and distracted the update! It seems to be very unstable.

Removing gnome, gdm, ubuntu-desktop and nautilus, reboot and then reinstalling everything did the trick!

```

(I rebooted after each step. Just to be sure...)
sudo apt-get autoremove gnome-*
sudo apt-get autoremove ubuntu-desktop
sudo apt-get autoremove gdm
sudo apt-get autoremove nautilus*
(another reboot)
sudo apt-get install ubuntu-desktop
(reboot)
(everything works fine, except...)
sudo apt-get autoremove gnome-orca (just to be VERY sure :D )

```

Maybe this helps?

HAVE PHUN!

---

