---
title: "KDM issue"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by maestrobwh1 on 2008-10-17
Upgraded my laptop from HH Remix to Intrepid last night... for the most part it went pretty well.  Annoying issue that occurs is when I log out:

I get something about grep: /usr/lib/kde4/etc/kde4/kdm/kdmrc file not found.  Not starting k display manager kdm-kde4.

There is also a message about some sound thing, I recall relating to alsa.

The resulting terminal shows no prompt. ctrl-alt-F1 brings up the terminal login, which I can then use to eventually drop to "init 1" and I get the choices to resume... and I get black screen but the computer is still on, so if I "Fn + Sleep" it flickers and sleeps {suspends} and then any button brings up kdm.  I mention this as these issues might be related.



I tried dpkg-reconfigure kdm, but it didn't help.

---

### Post by pbhj on 2008-10-17
With KDM (for KDE4) dpkg-reconfigure has only ever once worked for me, quite a while back. Currently KDM  won't install for me - it installs the package but files from the package (eg /etc/init.d/kdm !) are missing and no warning is given. I filed a bug report on it.

Tha current Intrepid version is just called kdm and not kdm-kde4, check you have the latest version.

---

### Post by inportb on 2008-10-17
Yep. In Intrepid, most packages-kde4 are now simply packages. KDE4 is the default in Intrepid and there is no easy way to install KDE 3.5.10 in parallel.

---

### Post by maestrobwh1 on 2008-10-18
These things are all true - but I guess I was not clear: kdm-kde4 is NOT installed... but something making a reference to it and looking for kdmrc in the wrong (old) place.

---

### Post by pbhj on 2008-10-19
My kdmrc is at /etc/kde4/kdm/kdmrc, fwiw.

Perhaps you could reinstall kdm-kde4 and then purge it to get rid of all it's file?

---

### Post by maestrobwh1 on 2008-10-21
Okay, most of that all got fixed with a recent update:-) and just for kicks, I installed gdm, then chose kdm as my diaplay manager so a combo of this helped remove the odd reference to the old /usr/lib/kde4/etc/kde4 directory.

I still can't log out and back in.  If I log out, I get

Not starting k display manager: kdm-kde4 is not the default display manager (no duh, it is now called kdm under kde 4.1 in intrepid)
*starting TtiMidity++ ALSA midi emulation

Then there is nothing.  If I hit ctrl+alt+F1, I can get to a console login, then I can do a "sudo /etc/init.d/kdm start" but sometimes I just get a black screen so then I have to ctrl-alt-F1 and then sudo -i" then go for "init 1" to restart the x-server and I get the logout usplash and it stops, so if I hit <enter> it selects the option "resume" which I can't see because it is somehow hidden.  I can see it after text rolls buy and it starts scripts and kdm starts.

For some reason, logging out does not restart kdm.  Obviously a logout (back to kdm) script was not modified when I was running 8.04 using kdm-kde4 as my display manager.  **What script would this be?**  Login from boot/reboot, and shutdown seem fairly normal.  

I did notice that I still had a kdm-kde4 script in /etc/init.d/ as well as a kdm script there.  I moved the kdm-kde4 script and I still had the issue.  I symlinked the kdm script to a link called kdm-kde4 and that helped by at least dropping me directly to a terminal rather than hanging.  I still have to restart kdm and occasionally go so far as to restart X

---

### Post by marttali on 2008-10-22
try this:
sudo aptitude purge kdm-kde4
sudo aptitude reinstall install kdm
sudo depmod -a
dpkg-reconfigure kdm, choose kdm

---

