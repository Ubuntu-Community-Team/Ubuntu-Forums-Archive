---
title: "Strange startup hiccup with Karmic today?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-05-03
Booted up today and after full startup the upper right panel where the Applets for volume control/network/date/time/status/shutdown, are placed, everything was blank!
On bottom panel the Trash Applet was missing also!

Was going to do a restart but there was no shutdown Applet!

Thought I'd have to do a hard shutdown but once I hit the PC power button the shutdown panel appeared allowing for a normal restart. After a normal restart, everything appeared normal on desktop with all the missing Applets back in their normal places.

Anyone know what happened here?
Usually a restart cleanses the system clearing up minor screw ups like this, which seems to have happened in this case. Thought of posting this because this has happened once or twice before over the past years and was wondering what may cause it?

---

### Post by ajgreeny on 2010-05-03
I have no idea why that happened, but if it should occur in future, there is no need to hard reboot.

Use Alt+F2 to get the run dialog, in that type **xterm** or **gnome-terminal** and in the terminal that appears type ```
killall gnome-panel
```

That should kill the panel process and it should then restart automatically.

PS:
It is never good to shutdown the way you suggested.  If you can't get a GUI, use Ctrl+Alt+F1 to get to the cli and login there with username and password (password will not show anything on screen).  After login you can type ```
sudo reboot
``` or ```
sudo poweroff
``` to shutdown properly.

---

### Post by cybrsaylr on 2010-05-03
Thanks ajgreeny.
I realize a hard shutdown is to be avoided but everything on the desktop was unresponsive. Nothing happened no matter what I clicked on, in trying to avoid a hard shutdown. 

Then after a couple minutes I hit the PC power button and that's when the 'Shut Down the Computer' panel appeared allowing me to do a proper restart/shutdown.

I'll use the advice you posted in the future, if I can remember it. As I said this only occurred a couple times over the past years.

---

### Post by ajgreeny on 2010-05-03
Yes, if everything is frozen solid you have no choice, I agree, but try to remember for other occasions when just the GUI freezes, which can happen.

---

