---
title: "system bus problem"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Genesius on 2009-03-04
Don't know if this is something easy to fix or if I need to report it on Launchpad, so I'll start here.

Updated to Jaunty two weeks ago, been running well so far, until I ran an update yesterday. Started getting multiple icons across the task bar. At one point I caught the word "system" in the icons, most of the time they were too small to read anything. After a minute or so my system stopped responding. Cold booted into recovery mode, assuming an install blew up I tried "dpkg --configure -a" and got this message:

Failed to open connection to "system" message bus: failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

So, anybody got a fix? Or do I just go into command line daily & run updates until an updated package fixes it?

---

### Post by Nullack on 2009-03-04
Cant replicate

Change sources to main to make sure your not being delayed by an old mirror, and synch with the repos, see if its still a problem

---

### Post by Genesius on 2009-03-05
OK, found the reason for the first part, anyway, with all the icons in the task bar.

Tried the guide from [http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/](http://tombuntu.com/index.php/2008/07/28/stackswitch-and-wallpaper-plugins-with-compiz-076/) to get a different wallpaper on each desktop with Compiz. When I open gconf-editor and go to apps > Nautilus > preferences and uncheck Show Desktop, "starting file manager" icons start spawning across the task bar. As long as I leave Show Desktop checked, I'm fine.

---

