---
title: "Failed to load session &quot;gnome&quot; on login"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by r_avital on 2013-08-12
I had a nice, working install of 13.04 64 Bit, no gnome-fallbac installed, just gnome3/unity.  I had to mess with it.

1. installed gnome-panel to see if I could add panels - which I could, but of course that installed gnome-fallback and all related packages.  Also, used compiz to de-activate the unity plugin, which made the launcher disappear.  At this point, everything still works nice.  Obviously, can't do much with the panels in a gnome session, had to go to fallback-no-effects to add some applets.

2. Logging back into gnome, I only get the black top panel with "activities" at the top-left corner.

3. Went into synaptic, looked at the log, to figure out what was installed, what was removed, when I did #1 above.  Followed that log, removed (including config files) everything that was added, added everything that was removed (two python packages).

4. Reboot, login (no alternate sessions available, just like it was after the fresh install).  At this point, I get the message:

Failed to load session "gnome" - In a nice little window with a logout button.

5. Used the Guest login, added a user (able to do it ONLY because I know the password of my original account).  Made the user an administrator, gave it a password.  Logged off.  Logged on as new user.

At this point, let's call the original accout A1 and the new one A2 for simplicity.

AS A2, I went to a TTY session, where I logged in AS A1, and did the following:

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get -f install
sudo dpkg-reconfigure ubuntu-desktop
sudo reboot

The fact that I was able to log on as A1 tells me my original account is still there, the problem is with some settings, configurations, right?

After reboot, attempted to log in as A1 to the only available session, still same error.

Rebooted, went into recovery, and did the above again, plus:
 sudo apt-get install gnome-session
sudo apt-get install lightdm
sudo apt-get install unity-greeter
sudo dpkg-reconfigure lightdm


Rebooted.  Attempted to log in as A1 again, same result.  I am posting this logged in as A2.

Can anyone think of a way to recover the full functionality of the A1 account?  It looks like everything I originally installed is still there, I just would hate to have to spend another day just redoing all the settings and customizations.

Many thanks!

---

