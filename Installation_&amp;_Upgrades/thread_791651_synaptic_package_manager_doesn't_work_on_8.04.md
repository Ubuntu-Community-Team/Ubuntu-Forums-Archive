---
title: "synaptic package manager doesn't work on 8.04"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by gpetrov on 2008-05-12
I,ve upgraded from edubuntu 7.04 to ubuntu 8.04 and having problems since. Some items of the administration menu don't work e.g synaptic package manager. also when i click on the notification of available updates and whatever I choose to update, update manager just hangs and nothing happens.

help and advice are appreciated

---

### Post by gene spiller on 2008-05-12
I can't offer a solution, but maybe some more details.  I've also upgraded from Gutsy to Hardy, and ever since, Update Manager doesn't work, and neither does Synaptic.  When you try either of those, normally the system asks you for the root password to continue.  In this case, what happens is that I see for a few moments on the taskbar the task "Starting Administrative Application", which disappears without asking for a password.  The update manager (or gnome app install) is left sleeping, and will sleep forever.  Either can be killed using the System Monitor, and the process repeated.  I have no idea how to proceed from this point, and I can't get any updates to fix it either.

---

### Post by Rallg on 2008-05-12
This problem appeared at some point during beta testing of 8.04. Then it was fixed before the final distribution. Perhaps your systems has a problem file, obtained earlier?

If you have the same problem that appeared during beta test, you can fix it. Boot to recovery mode, and update and upgrade from there. Depending one where your system is at now, one or the other of these (or both) might work:

sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get update && sudo apt-get upgrade

Then log off and reboot to ordinary graphics mode.

You can also do it from Terminal within your ordinary boot to graphics mode.

Did that work?

As I recall, the problem was that an extra process was started when Synaptic or Update manager were launched. In your current state, you can probably do this: Attempt to launch Synaptic or Update. When nothing happens, launch the System Monitor (it's in the administrative menu), and select the processes tab. One of the gnome processes (I forget which one) doesn't belong. If you stop that process, then Synaptic or Update will magically open.

---

### Post by gene spiller on 2008-05-12
Check out this thread for a solution.  It worked for me.

[http://ubuntuforums.org/showthread.php?t=791148](http://ubuntuforums.org/showthread.php?t=791148)

---

