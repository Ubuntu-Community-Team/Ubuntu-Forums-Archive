---
title: "Automatic login bug (and others)"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Alataire on 2010-05-03
In the screen System > Administration > Users and Groups > Password > Change I select the  box 'Don't ask for password on login' (automatic login). Since then, when booting, after I select my account on the login screen, I get a bunch of different error messages, in the following order: 
(1) "Could not update ICEauthority file /home/user/.ICEauthority"
(2) Error message that reads something like: Problem with the configuration server, ....
(3) Error from Nautilus: (translated from dutch): Cannot create mandatory directories: /home/user/Desktop
/home/user/.nautilus
(4) Update Window: "Record your encryption passphrase" > No idea what I have to do with this, if I execute the suggested action, this has no effect, and the system doesn't respond as indicated in the window itself.
(5) Now I get the blank default Desktop background, with nothing on it (no menu's, links, etc.) 
I am sort of logged in however, because I can get a screen to shut down, restart etc., when pushing my computer's on/off button. And after a break I get the normal login window that asks my password. If I enter it, the system hangs.
 
> Maybe this bug has to do with messed up file permissions? I have no idea. Maybe it's related to the fact that my home directory is encrypted (encryptfs)

**Work-around** to be able to login again and turn autmatic login off: boot with recovery mode, log in manually from the command prompt, and run 'startx' to start up ubuntu.

---

### Post by quixote on 2010-05-04
Well, that's the workaround I was going to suggest, but you beat me to it. :D

Lucid shouldn't be doing that though, just because you asked for auto login.  Have you checked the known bugs ([https://launchpad.net/ubuntu/lucid](https://launchpad.net/ubuntu/lucid)) ?  If it's not there, go ahead and file one.  Sounds like a bug to me.

---

### Post by Alataire on 2010-05-08
Thanks for your suggestion! I've reported this as Bug #577563 on [https://bugs.launchpad.net](https://bugs.launchpad.net).

---

