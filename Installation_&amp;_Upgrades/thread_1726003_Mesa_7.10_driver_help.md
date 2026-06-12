---
title: "Mesa 7.10 driver help"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by snafu006 on 2011-04-10
So is there a way to get the Mesa 7.10 on ubuntu 10.10? I looked in synaptic and all i can find is the 7.9 driver anyhelp plz

---

### Post by M4570D0N on 2011-04-10
You can try the xorg-edgers PPA. I can't get it to work on Maverick but I have a perpetual live USB of Natty and ran the xorg-edgers-live-test script, which upgraded Mesa to the current 7.11 build, and it worked.

Make sure you read everything on this page before you do anything else.
[https://edge.launchpad.net/~xorg-edgers]("https://edge.launchpad.net/%7Exorg-edgers")

If you have a live USB, you can install the test script from here:
[http://bazaar.launchpad.net/~xorg-edgers/xorg-server/xorg-pkg-tools/files]("http://bazaar.launchpad.net/%7Exorg-edgers/xorg-server/xorg-pkg-tools/files")

Boot into the live session from the USB, save the script to the Desktop on the USB. Then, drop down to a virtual console (ctrl+alt+f1) and type:

```
sudo sh ~/Desktop/xorg-edgers-live-test
```If it works, it will automatically restart X and gdm and you can test out how it works on your system. I don't know if there is a similar script out there for doing this on a regular OS on a hard drive, or if that script can be easily tweaked for such purposes. Every time I've tried to update with that PPA on Maverick though, I get a blank screen except for my mouse on the gdm login screen. I have to boot in recovery mode and run in low graphics mode to get the graphics to show up so that I can uninstall the updates.

---

