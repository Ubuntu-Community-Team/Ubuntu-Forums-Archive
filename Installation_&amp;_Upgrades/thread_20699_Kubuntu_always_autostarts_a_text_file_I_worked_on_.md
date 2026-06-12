---
title: "Kubuntu always autostarts a text file I worked on long time ago!"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by fizgig on 2005-03-18
Kubuntu keeps restoring a session where I had a text editor open to a small text file.  I went to "Control Center->KDE Components->Session Manager" and selected "Start with an empty session" but no dice.  Anyone know how to get rid of these autostarting programs?

This might be related: I notice any other changes I make like sound volumes don't stay the same when I reboot.

On another note, I would like smb4k to start in my taskbar as root (without me having to enter a password if possible).  A tip to help me get that rolling would be appreciated as well  [-o<

---

### Post by fizgig on 2005-03-18
little help?  :-|

---

### Post by fizgig on 2005-03-19
Well, it turns out that I had to add this to the top of the script file:

#!/bin/sh

Now it no longer shows the edit screen when I boot up.

---

