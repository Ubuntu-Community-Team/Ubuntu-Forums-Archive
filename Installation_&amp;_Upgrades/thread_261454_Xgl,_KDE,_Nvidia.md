---
title: "Xgl, KDE, Nvidia"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by _Petya_ on 2006-09-20
Hi!

I've been looking for a howto that describes how to install Xgl on KDE and Nvidia, but I haven't found a working one yet. I have Kubuntu Dapper installed, and tried the following:

I've created a file .Xsession:

#!/bin/sh
# Start up Xgl, compiz, and GNOME

# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &

# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1

# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &

# Start GNOME
exec gnome-session

After restarting X, it works, but there's no window decoration. What can I do?

Thanks,

Petya

---

### Post by wieman01 on 2006-09-20
This was pointed out to me a while ago. Honestly I have not tried it out yet,  but perhaps you want to give it a go (KDE script):

[http://www.kde-apps.org/content/show.php?content=43320]("http://www.kde-apps.org/content/show.php?content=43320")

Let us know how it goes, buddy.

---

