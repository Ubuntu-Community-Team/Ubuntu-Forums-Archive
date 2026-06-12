---
title: "Non blocking startup script (X11vnc)"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Trollslayer on 2008-04-13
On 7.10 I need to run a script as root that won't exit (to start X11vnc) after the X server has been started.
I'm guessing that putting a script in /etc/rcS.d where [COLOR="Red"]S70x11-common[/COLOR] is as say S71x11vnc-common so it will run at the right time.
The question is - how do I get this to spawn another process to avoid blocking?
I tried [COLOR="Red"]x11vnc &[/COLOR] but that acted as normal.

---

### Post by krunge on 2008-04-14
You might want to try the 'Xsetup' script method described under 'Continuously' here:

[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

This way is probably more convenient than a rc script because the variables $DISPLAY and $XAUTHORITY are automatically set to the correct values.

Be sure to apply the KillInitClients=false setting if you are using GDM as a login greeter.

---

