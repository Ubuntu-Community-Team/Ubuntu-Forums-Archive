---
title: "Freemind does not load - a java issue"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by Sebata_Afrika on 2005-11-14
Yo!

I have recently installed Freemind and jre-1_5_0_05-linux. Now when I try to run Freemind nothing comes up. this is what comes out when i run it on terminal command:

java.awt.IllegalComponentStateException
   at java.awt.Frame.setUndecorated (Frame.java:533)
   at freemind.main.FreeMindSplash.FreeMindSplash (FreeMindSplash.java:52)
   at freemind.main.FreeMind.FreeMind (FreeMind.java:111)
   at freemind.main.FreeMind.main (FreeMind.java:647)
   at java.lang.VirtualMachine.invokeMain (VirtualMachine.java)
   at java.lang.VirtualMachine.main (VirtualMachine.java:92)

Then nothing happens

---

### Post by 1111 on 2005-11-23
1) be sure u really using 1.5, 'cause installing it is not enough :(
2) maybe u'r using a window manager that not support "undecorated frames" (or better: java dont support them for that win-manag). Check the config files of Freemind to see if is possible to disable the splash screen, and/or change the window manager.

1111

---

