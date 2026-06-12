---
title: "cant boot properly after upgrade to 9.10"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by richardy on 2009-11-25
Hi,
I recently upgraded to Xubuntu 9.10 from 9.04 on my Asus laptop (using external monitor). The upgrade seemed to go fine. HOwever on rebooting the computer i found i could not get past the login screen (computer would lock up), or after entering my password it would continually come back to the login screen (after screen going blank for a short period).

Using the previuos kernel (4.28-15) initially allowed me to boot properly but that only occured once, on every subsequent reboot i have had teh latter problem of continually being sent back to the login screen after initially logging in.

Any help with this issue would be much appreciated.

Cheers.

---

### Post by jaylsi on 2009-11-25
You probably need to re-install video driver after upgrade. Try this:
1) On login screen, click your user name, and enter password, but before hit enter, select "failsafe gnome" from session list on the bottom of screen, then login
2) Go to System->Administrator->Hardware Drivers to install video driver
3) Reboot

---

### Post by richardy on 2009-11-26
Hi Jaylsi,
Thnks for the reply. I did as you suggested but i when i got to "hardware drivers" there was nothing to install and a message saying "no proprietary drivers are in use on this system".

There also seems to be a lot of poeple who have been caught with the same problem.

Another thing that was quite odd was that when i was required to enter my password, the system wouldnt accept teh password i had logged in with.

Any further help you can give is much appreciated.

Cheers.

---

### Post by anglican on 2009-11-26
It could just be that some configuration for **something** in your home directory is borked. Try creating a new user and logging in normally as that user. If that works then you need to figure out which config is breaking your login - by trial and error probably i.e. (re)move config files one at a time until the problem goes away. Or you could just use the new userid instead...

H

---

### Post by richardy on 2009-11-27
Hi,
And thanks for the reply. I have made a few changes/alterations by making comparisons to a live version so that i can now get into the system but only if i boot to a command prompt and then using the command "startx". However this takes me by default to a gnome session but my desktop environment is actually XFCE. Anyway i tried to create a new user as you suggested but the system doesnt stay up long enough to make the change before freezing.

It is now starting to get really frustrating and i dont want to reinstall from fresh as i will lose all settings/previously installed programs etc but i may have to.

Since it looks like something to do with X is the problem, is it possible to uninstall X then reinstall it and can it be done from the command line or is it better just to reinstall but hoping not to have to.

Any help would be much appreciated.

Cheers.

---

### Post by jaylsi on 2009-11-30
richardy,
I am not sure about your password problem. Could it be that you have a different password for administration than the one for your own user account?

On X problems, did you try renaming /etc/X11/xorg.conf to a backup file and reboot? It makes system to use a default video driver without fancy stuff. If that does not cause lockups, at least you have a usable system.

---

