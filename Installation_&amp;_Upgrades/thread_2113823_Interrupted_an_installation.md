---
title: "Interrupted an installation"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by filipcro on 2013-02-08
I accidentally interrupted the installation of Google Chrome and when I booted after a few days I got an error message from the update manager:
"Could not initialize the package information
An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it.'"

The archive is on the desktop, but I can't reinstall because a lot of system programs don't work like the Software Center, Language support, Additional Drivers, etc.
I get this error message: "The application blah blah blah was closed unexpectedly."
Then I get this:
Title is "Invalid problem report"
And the message is: "Could not determine the package or source package name."

The computer once froze during an update when "sudo apt-get install -f" fixed all problems.
Now I get this:
After the usual
"Reading package lists... Done
Building dependency tree       
Reading state information... Done"
I get this again: "E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it."
The last backup i made was 1 year ago and there is no way I'll do a restore that old.

Is there anything I can do to resolve the issues?

---

### Post by darkod on 2013-02-08
When you say you have it on the desktop, does that mean you tried installing it from a .deb file?

If you have the .deb what if you try:
sudo dpkg -i /path/filename.deb

---

### Post by filipcro on 2013-02-08
It worked ^^
Thanks!

---

