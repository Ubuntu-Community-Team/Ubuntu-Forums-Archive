---
title: "Update manager error icon in panel"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Worp8d on 2011-01-25
There has been a red circle icon with a big white bar through it in the notifications area of my panel for days now.  The alt-text (is that what it's called for an icon?) says "A problem occurred when checking for the updates."

When I click on the icon the update manager appears and "builds data structures" but says there are no updates available.  ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
``` does nothing.  Right-clicking and selecting "preferences" from the drop-down menu does nothing.  I can end the process "update-notifier" in the system monitor but the icon comes back on reboot.

I can't access the settings from update manager (when I click on it it just "builds data structures" again and does nothing) and I have no repositories added that I can think of.  This is very frustrating as the update manager appears to be locking the administration directory on occasion so I can't use sudo.

I thought I could use ```
sudo apt-get remove update-manager
``` and then reinstall it but when I tried that it told me it wanted to remove ```
ubuntu-desktop
``` and that sounded bad.

Any ideas, anyone?  Anything at all at this stage would be appreciated.

---

### Post by Worp8d on 2011-01-25
Okay, seems my problem was that I'd tried to upgrade to Python 2.7 and had followed [this]("http://tareqalam.wordpress.com/2008/11/28/change-the-default-python-version-in-ubuntu/") guide to changing the default Python version.  Ubuntu *does not like this.*  Changed it back and everything is working.

---

