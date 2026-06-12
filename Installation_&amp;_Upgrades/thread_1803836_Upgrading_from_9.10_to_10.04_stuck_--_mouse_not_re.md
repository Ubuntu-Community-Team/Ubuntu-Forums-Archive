---
title: "Upgrading from 9.10 to 10.04 stuck -- mouse not responding. How to cleanly restart?"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by karups on 2011-07-13
UPDATE: I no longer need help on this problem.  I killed processes until the prompt went away and then used the command-line to restart the upgrade.

While upgrading from Ubuntu 9.10 to 10.04 LTS, I am prompted to respond to something but my mouse/keyboard don't work! (Since I share the mouse/keyboard with another computer, the mouse was unplugged during the install process.) I have tried unplugging and re-plugging that USB mouse/keyboard (Logitech MX series) as well as another USB mouse and keyboard. I even dug out an old PS/2 mouse.  But I don't get any response.  I can still access the machine via ssh.

My primary concern is figuring out how to cleanly cancel the upgrade process (or better, continue it). Any ideas?  I tried "sudo modprobe -r usbhid; sudo modprobe usbhid".  I'm doing the upgrade using the normal Update software.

Although probably not relevant, the prompt it is asking me to respond to is: "Replace the customized configuration file /etc/sysctl.conf?"

---

