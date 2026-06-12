---
title: "Gutsy Upgrade Problem with Schizophrenic Xserver"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by ADRegner on 2007-10-29
I have been running Feisty on my laptop until this last weekend when I upgraded (the recommended network upgrade) to Gutsy.  The update manager only came up with an error message/notification a few times throughout the process.  Once was to inform me of the depreciated packages, and several other times to tell me about some configuration file changes and asking me what to do about conflicts with the locally changed versions.  Each time I told it to use the new distribution's version.

After the process finished successfully, it rebooted, X appeared to come up like normal, but then it crashed.  And then X came up again.  And then it crashed and came up again, and again, and again...  From what I can tell, the display manager and/or X were loading and then at some point right after or during drawing the screen with the login prompt, it crashed and loads it again.  I am running an Ubuntu install with both kubuntu-desktop and xubuntu-desktop packages installed, and gdm as the default display manager.  For the tenth of a second I could see the login screen, I saw a pretty new Xubuntu logo and a text box labeled user name, so it looks like it was gdm with a new background from the upgrade.

Here is what I have done so far to fix it (all in recovery mode of course):

[LIST=1]
[*]ran `dpkg-reconfigure xserver-xorg` selecting the ati driver for my ATI Radeon x600.
[*]Manually installed the proprietary driver from the /usr/share/envy folder.  The same file that Envy downloaded and installed back in Feisty.
[*]Remembered that I should of uninstalled the proprietary driver I had installed with Envy in Feisty before running the upgrade.  In response to this I downloaded the latest version of Envy (which was not easy for me to do in w3m) and uninstalled the ATI driver (it was version 8.39) and then installed the new ATI driver. (version 8.40)
[*]Everything listed in the first post in [this thread.]("http://ubuntuforums.org/showthread.php?t=187177")
[/LIST]

After each of those attempts of fixing it I rebooted into normal mode and each and every time the "schizophrenic xserver" was unchanged.  I am out of ideas and in somewhat of a panic because this laptop is my life.  I have backups of all my personal data, but reinstalling and reconfiguring a new OS is the last thing I need right now.  My eternal thanks to anyone and everyone who can help.

---

### Post by ADRegner on 2007-10-30
bump.

i still have no clue on this.  anyone out there that can help?

---

