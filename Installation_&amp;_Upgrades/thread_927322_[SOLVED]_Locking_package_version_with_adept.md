---
title: "[SOLVED] Locking package version with adept"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by Fredizdman on 2008-09-22
Okay, I know there is already a similar thread out there but for some reason I couldn't reply. Something about insufficient privileges :confused: 
Anyway, I was trying to figure out how to lock a package version with adept so that I wouldn't have to cancel it each time adept updater ran. I found this on the Ubuntu APT Howto

"#

echo "<package_name> hold" | dpkg --set-selections

This command places the desired package on hold. This is the same as Synaptic's Package->Lock Version.

    *

     -------- This command may have the unintended side effect of preventing upgrades to packages that depend on updated versions of the pinned package. apt-get dist-upgrade will override this, but will warn you first. If you want to use this command with sudo, you need to use 

echo "<package_name> hold" | sudo dpkg --set-selections **_not_** sudo echo "<package_name> hold" | dpkg --set-selections. "




Unfortunately, the adept icon still remains with its warning symbol, but when you run the program the "no change" action should already be selected.

Hope this helps!

Not too sure if you're supposed to start a thread with an answer,but as I said I wasn't able to reply. You guys can delete this if you want.

---

### Post by cariboo on 2008-09-22
Have a look ath this thread specifically post #7

[http://ubuntuforums.org/showthread.php?t=747470](http://ubuntuforums.org/showthread.php?t=747470)

Jim

---

