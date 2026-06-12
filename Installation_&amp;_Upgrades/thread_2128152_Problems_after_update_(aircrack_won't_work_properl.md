---
title: "Problems after update (aircrack won't work properly anymore, and OS crashes)"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by damog88 on 2013-03-22
Hi everyone!

I'm writing this because I have no idea of what happened, not even where should I start looking for...

The thing is that this wednesday there were some updates available in the Update Manager of Ubuntu 12.04, and, as I usually do, I hit the install button after having a brief look at the updates (I didn't really understand what they do...I know it's my fault, but until now, I haven't had any problem).

By the way, this week I have been working with aircrack-ng and it was working properly, no problems at all (before continuing, I was just doing tests with my home's wifi). But now, after the updates, I don't know why, but I follow the steps as before, and airodump does not detect any net, not even mine, and, actually, if I get disconnected from my wifi's house (wich it connects automatically), and then do the aircrack ritual, and after seeing that it doesn't work, I try to re-connect to my wifi, the system crashes. I'm pretty sure it's a problem of updates, so I'd like to know if there's a way to un-update, or undo these last changes.

Just to add. I looked in the log file of the apt application, and I can tell exactly what was installed and updated:

Start-Date: 2013-03-20  18:43:58
Commandline: aptdaemon role='role-commit-packages' sender=':1.78'
Install: linux-headers-3.2.0-39-generic:amd64 (3.2.0-39.62),  linux-headers-3.2.0-39:amd64 (3.2.0-39.62),  linux-image-3.2.0-39-generic:amd64 (3.2.0-39.62)
Upgrade: linux-generic:amd64 (3.2.0.38.46, 3.2.0.39.47),  linux-headers-generic:amd64 (3.2.0.38.46, 3.2.0.39.47),  linux-image-generic:amd64 (3.2.0.38.46, 3.2.0.39.47)
End-Date: 2013-03-20  18:45:05


Anyway, I'll say exactly what happens. Until now, when I wanted to work with aircrack, I was following these steps, and everything went fine. 


 (every command as su)


 airmon-ng stop wlan0 (to avoid conflicts of channels, and start the process from the very beggining)
airmon-ng stop mon0 (same as before)
airmon-ng start wlan0 (enables monitor mode)
airodump-ng mon0 (tells me what are the wifi lines in the surrounding environment)
airodump-ng -w captura --channel X --bssid XX:YY:ZZ:AA:BB:CC mon0 (fixes the target)
aireplay-ng -1 0 -a (mac del objetivo) -h (mac propia) mon0 (associates to the net)
.
.
.


 Thing is, that on wednesday evening, after I updated, when I arrive to the point "airodump-ng mon0", the app doesn't show me any wireless network, when before updating it did. And, actually, when I close the app and I try to reconnect to my wifi the OS completely blocks when it is going to show the available wireless lans (I'm not connected to the internet while running the program, just to avoid problems of fixed channels, as I said before...). I don't really know what's happening, and it's driving me crazy...!

Thanks a lot for your help!

Cheers!

---

### Post by haqking on 2013-03-22
Try the aircrack forums, aircrack is not supported here.

Peace

---

### Post by Elfy on 2013-03-22
As far as I can see the issue isn't in using aircrack but dealing with a possible update issue - that is supported.

---

