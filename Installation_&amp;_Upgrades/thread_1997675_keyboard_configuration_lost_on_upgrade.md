---
title: "keyboard configuration lost on upgrade"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by malkiah on 2012-06-05
Hi,

after upgrading from 11.10 to 12.04 my keyboard configuration for my user was lost. The only way to restore it is by executing:

sudo setxkbmap -layout 'es,es' -model pc105

everytime I restart.

I've edited xorg.conf and checked /etc/default/keyboard. Everything is telling the system to set spanish keyboard, but nothing happens.

If I go to the keyboard settings in the control panel, it says that the system input method is spanish, but that there is no input method set for the user. If I press the button to copy system data into the user data and restart the session, everything seems ok, put when I reboot, the config falls to english keyboard again.

Terminal in tty 1 has the keyboard correctly configured in spanish.

Any idea of what might be happening?

---

