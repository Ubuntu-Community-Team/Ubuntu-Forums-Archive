---
title: "Laptop video issue"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Halavar on 2010-04-29
I'm having a video issue installing 10.04 on a laptop.

The laptop has no primary screen (The LCD was broken long ago).  I acquired it and use it as a server.  I hook up my monitor to the external VGA port when I need to see during installs, and VNC into the machine otherwise.  

Installing 9.10 gave me no trouble at all using default installation settings, no changes at all.  10.04 though is giving me trouble.  While it's booting it shows the install options, I can watch the load progress screen, but when it gets to the actual X GUI, the secondary VGA output simply shuts down.  Toggling the output via the laptop's FN hotkey doesn't do anything.  I've tried all the basic options presented with the installer, and it still does it.  I need it to use the secondary output in order to install.  How can I make this usable?

---

### Post by Halavar on 2010-04-30
I'm moving ahead trying an upgrade direct from 9.10.  I will post results.

---

### Post by Halavar on 2010-04-30
Upgrade fails with the same issue.  :(

After much reading, I found that it's an issue with the Intel 82845/855 chipsets.  Amusingly enough, the problem existed for me when trying to install 9.04 a year ago too.  When I clean installed 9.10 though, the issue was gone, so I assumed it had been fixed.  10.04 seems to reintroduce the issues though.  :(

---

