---
title: "After upgrade to Kubuntu 24.04 from 22.04, xscreensaver doesn't come up"
date: 2024-09-02
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2024-09-02
I recently upgraded to 24.04/Noble Numbat, and the transition was mostly smooth. However, I'm encountering an issue where xscreensaver no longer starts automatically. I tried uninstalling and reinstalling it, but that didn&#8217;t resolve the problem. When I navigate to System Settings ==> Startup and Shutdown ==> Autostart, I see XScreensaver Settings listed. Initially, I thought that only the settings were there, and that I needed to add the xscreensaver command. However, when I try to remove it, it disappears, but when I attempt to add it back, the only option available is the XScreensaver Settings. Under Properties ==> Application, the "Program" field shows "xscreensaver-settings". Should it be listed as "xscreensaver" instead, or is there something else going on? Additionally, under Properties ==> Permissions, the "is executable" box is unchecked. Should it be checked?

When I launch Xscreensaver-settings from the Launcher, it works correctly. The mode is set to Random Screensaver, with "Blank After" set to 99 minutes and "Cycle After" set to 10 minutes. The "Lock screen after" option is not selected. I can use the Preview button to view the selected screensaver. Does anyone have insights into why this issue is occurring? I miss having the random screensaver functionality like I did before the upgrade, as now it just displays a blue and white graphic with the Kubuntu logo. Here&#8217;s a screenshot of what it looks like:

[IMG]https://i.postimg.cc/L80XYXpH/Kubuntu24screen.jpg[/IMG]

Btw, that is not the Infinity-SDDM login screen that I chose in Kubuntu's settings, though it does require my password.  Infinity-SDDM does come up when I first boot the computer up.  It&#8217;s not a critical system issue, but I&#8217;d appreciate any guidance on how to fix it. I attempted to run xscreensaver from the command line but received a message indicating that it&#8217;s already running:

```
tom@tom-Dell-OptiPlex-7040:~$ xscreensaver: 21:26:38: already running on display :0 (window 0x3600001) from process 3058 (tom@tom-Dell-OptiPlex-7040)
```

---

