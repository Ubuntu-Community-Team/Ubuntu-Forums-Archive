---
title: "Install on remote machine via VNC?"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by aseriesoftubes on 2009-12-11
I need to install Ubuntu to a machine that doesn't have a monitor attached to it (or anywhere near it, for that matter). I think I have a solution, but I wanted to run it by the community to see if anyone else has tried it.

So far, I've created a LiveUSB stick with quite a bit of persistent memory and booted it on a separate computer. In the LiveUSB session, I added a user, set that user to autologin, and installed and configured SSH and VNC servers. Then I put the USB stick in the target computer and booted it. I can now SSH/VNC into the LiveUSB desktop on the target computer from a remote machine.

Here's my question: is there any reason I shouldn't install Ubuntu to the target machine via a VNC session from a remote machine? Has anybody ever tried this? My attempts to Google this solution have been fruitless so far.

---

