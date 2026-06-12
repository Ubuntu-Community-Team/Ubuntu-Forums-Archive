---
title: "Natty Upgrade - Haaaaaaaallllllllp!"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by d3fau1t on 2011-04-29
Ubuntu asked if I wanted to upgrade, so I said yes, and when it got to the "Installing the upgrades" section, I went to bed. When I got up, the "Distribution Upgrade" window is frozen. The last action it says it was doing was "Configuring sgml-data".

How do I get this upgrade going again without wrecking it?

---

### Post by sikander3786 on 2011-04-29
There is not much you can do at this point I am afraid.

Is the keyboard responsive if you press the <Caps Lock> / <Num Lock> keys or it is totally frozen? Does your mouse work?

Don't shutdown or reboot your PC.

---

### Post by d3fau1t on 2011-04-29
Everything is working except the update manager. I can even do a ctrl-c in the terminal part and totally stop the upgrade, but I don't think I want to, obviously. 

The update manager just hangs at "Configuring sgml-data".

---

### Post by sikander3786 on 2011-04-30
You'll need to close the update manager and then run a few commands in your Terminal. There might be some lock problems or so, so we need you to be online when we are giving you the instructions.

---

### Post by manzdagratiano on 2011-04-30
If it really is frozen with no other windows popped up waiting for authetication which may be hidden behind existing windows, then I suggest the following:

1) Kill the update manager from the system monitor.
2) Log into tty1 with ctrl+alt+F1
3) Issue:
```
sudo dpkg --configure -a
```
This should correct half-installed packages
4) ```
sudo apt-get update && sudo apt-get upgrade
```
5) If all goes well, reboot, and enjoy your Natty install.

---

