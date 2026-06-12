---
title: "Upgraded to KDE Desktop - Errors"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by scorpiusmaximus on 2007-11-12
I have Ubuntu installled and I just upgraded to Kubuntu_desktop so I could log on and use the KDE desktop. I was setting up/configuring when I got to the Desktop - System Settings. On the Screen Saver tab, I get a greyed out page that says:
"The specified library screensaver could not be found.
The diagnostics is:
libGL.so.1: cannot open shared object file: No such file or directory
Possible reasons:
An error occurred during your last KDE upgrade leaving an orphaned control module
You have old third party modules lying around
Check these points carefully and try to remove the module mentioned in the error message. If this fails, consider contacting your distributor or packager."

I used apt to do the upgrade. 
I do not think third party modules are the problem although I did install Java and have a locked file (jre1.6.0_03) on my desktop that I can not Remove or Delete. I did re-install so that this file is in my /usb/lib/java diirectory but I can not get this file off of my desktop.
I notice that Gnome front viewer, menu editor & OpenOffice.org Formula are located in Lost & Found. I can not seem to figure out how to move them.

First, I, obviously, want to fix the libGL.so.1 problem but I do not know where to begin. 
I would love the Lost and Found programs to be in the right place.
I would like to get this java file off of my desktop.

ANn help would be greatly appreciated.

---

### Post by Triptol on 2007-11-13
I would recommend using aptitude and not apt. Aptitude does more check than apt.

you could check and see what: ```
aptitude install kscreensaver
``` does.

---

