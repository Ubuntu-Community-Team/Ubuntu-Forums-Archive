---
title: "Synergy Client(on ubuntu) can't connect with Synergy Server (on Centos)"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by scenarist on 2010-01-27
[FONT=monospace]
[LIST=1]
[*]**When I start Synergy Server on Centos 5.4**
[*][root@nedzad-pc ~]# synergys -f
[*]INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.18-164.el5 #1 SMP Thu Sep 3 03:28:30 EDT 2009 x86_64
[*]DEBUG: synergys.cpp,1051: opening configuration "/root/.synergy.conf"
[*]DEBUG: synergys.cpp,1058: cannot open configuration "/root/.synergy.conf"
[*]DEBUG: synergys.cpp,1051: opening configuration "/etc/synergy.conf"
[*]DEBUG: synergys.cpp,1062: configuration read successfully
[*]DEBUG: CXWindowsScreen.cpp,840: XOpenDisplay(":0.0")
[*]DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000
[*]DEBUG: CXWindowsScreen.cpp,110: screen shape: 0,0 1440x900
[*]DEBUG: CXWindowsScreen.cpp,111: window is 0x01d00004
[*]DEBUG: CScreen.cpp,38: opened display
[*]DEBUG: CXWindowsScreen.cpp,672: registered hotkey ScrollLock (id=ef14 mask=0000) as id=1
[*]NOTE: synergys.cpp,500: started server
[*]INFO: CServer.cpp,1140: screen "nedzad-pc" shape changed
[*]**But when I start Synergy Client on ubuntu**
[*]root@nedzad-laptop:/# synergyc -f 192.168.0.101
[*]INFO: synergyc.cpp,716: Synergy client 1.3.1 on Linux 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64
[*]DEBUG: CXWindowsScreen.cpp,847: XOpenDisplay(":0.0")
[*]DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000
[*]DEBUG: CXWindowsScreen.cpp,117: screen shape: 0,0 1366x768
[*]DEBUG: CXWindowsScreen.cpp,118: window is 0x03e00004
[*]DEBUG: CScreen.cpp,38: opened display
[*]NOTE: synergyc.cpp,330: started client
[*][COLOR=RoyalBlue]WARNING: synergyc.cpp,265: failed to connect to server: No route to host[/COLOR]
[*]DEBUG: synergyc.cpp,237: retry in 1 seconds
[*]WARNING: synergyc.cpp,265: failed to connect to server: No route to host
[*]DEBUG: synergyc.cpp,237: retry in 3 seconds
[*]WARNING: synergyc.cpp,265: failed to connect to server: No route to host
[*]DEBUG: synergyc.cpp,237: retry in 5 seconds
[/LIST]
How can I fix this problem ?

BUT I can make reverse connection >>> view my code on [/FONT][http://pastebin.com/f293ed44d](http://pastebin.com/f293ed44d)   

PLEASE HELP! Thanx in advance.

---

