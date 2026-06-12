---
title: "No Status Bar on Desktop After 10.04 Upgrade"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by bper on 2010-09-14
Hello,

On another machine, I upgraded a 8.04 desktop to 10.04 using the update manager. The update went well, but after the reboot and login, the default desktop background is loaded, but there is no status bar to select programs, access system settings, etc.

How can I fix the desktop to include the status bar so that I can use the system? I can right click on the desktop and it gives me options to create launchers, etc.

---

### Post by lechien73 on 2010-09-14
Some others who had experienced the same problem said that you could fix it by doing the following:

Press Alt+F2 to bring up the **Run Application** dialog
Type: **gnome-terminal** and click **Run**
In the terminal window type:
```
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

This should restore the default Gnome panels.

---

### Post by bper on 2010-09-14
Thanks,

That did work. However upon rebooting, the status bar is still not available.

Would I have to repeat this every time? Is there a way to fix it? I downloaded the updates to see if there were any fixes that would address this but the problem still exists.

Thanks again for your help.

---

### Post by lechien73 on 2010-09-15
Does the machine have an Nvidia graphics card? Others reported success by disabling the closed source drivers in **System > Administration > Hardware Drivers**, and then re-running the procedure I gave before.

If that doesn't work, then backing up the /home folder and trying a fresh re-install is probably your only option!

---

