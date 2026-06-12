---
title: "opera in gutsy only runs with sudo"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by topjohn on 2007-10-21
i recently installed gutsy and then immediately installed opera, my browser of choice.  i used this link to install opera:

[http://tuxicity.wordpress.com/2007/10/18/howto-install-the-latest-opera-browser-on-ubuntu-gutsy-gibbon/](http://tuxicity.wordpress.com/2007/10/18/howto-install-the-latest-opera-browser-on-ubuntu-gutsy-gibbon/)

it just pointed me to a link to the opera deb file and instruction to point to java folder in opera.  it ran once, but has ceased to run since.  when i run it "opera" in terminal i get this:

:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported
Segmentation fault (core dumped)

the only way i can get opera to run now is by using: 

"sudo opera -personaldir /home/user/.opera"

this way i can see all my bookmarks and use my wand passwords.

the above command gives me this in the terminal but will start opera:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: $HOME set to /root. Use -personaldir if you do not want to use /root/.opera/
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
opera: X Shared memory extension is not available. ZPixmap not supported
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

can anyone tell me how much of a security risk it is to run opera with sudo?  i'm sure a fix for this will come sooner or later.  until then, i don't mind using the sudo to start opera, but only if it's not risky.  thanks!

---

### Post by kerry_s on 2007-10-21
your screwed. anything that tries to compromise you has direct root access. on top of that you might be messing up your opera settings profile, since your running it as root, so thus root owned.

the best thing to do is export your bookmarks and the delete the .opera settings folder, then try running opera as a regular user again.

---

### Post by aysiu on 2007-10-21
You might want to read [this](http://ubuntuforums.org/showthread.php?t=497768). Not sure if it'll help.

---

