---
title: "Reinstalling ieee80211 files"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by sevketcakir on 2008-08-07
Hello, 
I've been using ubuntu 8.04 for a while.
i was trying to install ieee80211. I downloaded ieee80211-1.2.18.tar.gz from sourceforge. While i was compiling it asked me to delete previous files. I said yes and compilation failed. Now I can't go back to previous version. How can I repair deleted package files and changed settings?
Is it included in any ubuntu package?(I'm thinking to reinstall but I don't know which packages can include these files.)
Thanks for your help.
Regards.

---

### Post by pixel_juice on 2008-08-29
I lost these files the same way the OP did. I was trying to compile this module for use with aircrack-ng. :( Serves me right I guess. By now you may have found a solution, but for those that stumble on this here's how I fixed it.

1. Search "linux kernel" in synaptic
2. Mark "net-tools" for reinstallation.
3. Apply changes.
4. Reboot.

I think that was the package that ACTUALLY replaces the modules, but if it doesn't, you can also try marking "linux-generic", all "linux-headers" that you have installed, all "linux-image" that you have installed", all "linux-ubuntu-modules" that you have installed for reinstallation.

The reason I don't know for SURE which package did the trick is that I reinstalled all that stuff at once. In hind-site the "net-tool" package seems like the obvious choice.

Hope that make sense. Happy hacking!

---

