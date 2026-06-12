---
title: "System Tray Notifications' Error (Kget)"
date: 2012-04-06
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-04-06
Hi everyone. I have a problem related to system tray notifications.
I recently switched completely to ubuntu from windows coz i liked it. Now i got a problem.
I installed Kget to download files. By default, its settings are such that [B]Settings> Configure Kget> Advanced (bottom left panel) > Enable System Tray.
[/B]
I knew tray notifications had some problems regarding unity. so, i installed dconf-editor and from there, i did all necessary changes as **desktop>unity>panel> **and under the **systray-whitelist** , i set the value to **['all'] **so that the apps that let enable tray notifications can easily be shown up.

But with kget, i got weird thing. 
When i close kget and repoen it, i get a message saying that kget is already running. Strange thing is it even doesn't show up in notification area when closed though. So i have to execute
```
killall kget
```everytime i use kget.

If i uncheck the option to enable system tray for kget via its own settings(as above), i can close it and again restart it without having to use the **killall kget** command anymore. 

Surely its a problem of unity being unable to handle tray notifications...(thats how i understood) But is there any way around to solve this issue?

Any help would be appreciated.

Regards,WinuxUser

---

