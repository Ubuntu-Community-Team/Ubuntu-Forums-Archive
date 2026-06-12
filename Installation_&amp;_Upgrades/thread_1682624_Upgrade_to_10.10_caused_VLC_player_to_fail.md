---
title: "Upgrade to 10.10 caused VLC player to fail"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by whowinsdares on 2011-02-06
**VLC player fails after upgrade to 10.10** 			
 			
I upgraded to 10.10 my VLC player wont work at all, 
I tried the advice in this thread:

[http://forum.videolan.org/viewtopic.php?f=13&t=86092](http://forum.videolan.org/viewtopic.php?f=13&t=86092)

which was to enter in console:

vlc --reset-config --reset-plugins-cache

 I got the following result, and my problem isn't fixed:

*********@*********:~$ vlc --reset-config --reset-plugins-cache
VLC media player 1.1.4.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x98c58fc] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x9a2ec44] skins2 interface error: no suitable dialogs provider found  (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x9a2ec44] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x98c58fc] main libvlc error: interface "default" initialization failed

If someone could please help me it would be much appreciated..

---

