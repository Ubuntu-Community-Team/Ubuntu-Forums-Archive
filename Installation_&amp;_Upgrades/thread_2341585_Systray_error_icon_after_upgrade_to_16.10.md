---
title: "Systray error icon after upgrade to 16.10"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by muppet317 on 2016-10-29
I've just upgraded to 16.10 and after the upgrade I now have this error icon in my systray:

[ATTACH=CONFIG]271841[/ATTACH]

When I click on it, there's just an empty black box where the drop down menu should be.

The output of ```
 ps -ef | grep indicator-
``` is 
```

m         2306  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
m         2307  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
m         2314  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
m         2317  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
m         2318  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-keyboard/indicator-keyboard-service --use-gtk
m         2328  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
m         2330  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-printers/indicator-printers-service
m         2335  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
m         2362  1551  0 15:27 ?        00:00:00 /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-service
m         3569  3556  0 15:31 pts/2    00:00:00 grep --color=auto indicator-

```

Any ideas on what this is and how to resolve / remove it? Thanks!

---

### Post by egeezer on 2016-10-29
In my case (Xubuntu Core 16.10, very little added software), that is where the Dropbox icon should be.  Ever since 16.04 the icon has failed to show properly, and I suspect a simple but obscure dependency problem.  Dropbox woks fine despite the lack of the icon, so I have chosen to let sleeping dogs lie.

I admit, if someone presents a simple fix involving no heavy additional software, I will happily use it!

---

### Post by ajgreeny on 2016-10-29
I very occasionally see that icon in place of my skype icon in the panel of Xubuntu 14.04.
I haver no idea why that happens as I can still show the skype window from it, and by refreshing the panel the proper icon always shows.

I do not know if it is possible to refresh/restart just the panel in Ubuntu, but that could be worth investigating.

Does the icon actually do anything when you either right or left click on it?

---

### Post by muppet317 on 2016-10-29
It's not dropbox or skype - and the dropdown menu (either left or right click) is blank - just an empty grey box

---

### Post by smorozov on 2016-11-27
I have the same issue with Skype and GoldenDict tray icons after upgrading to Ubuntu 16.10. The icons are displayed fine right after login, but if the screen gets locked and then unlocked, both icons are replaced with the error ones. If I close either of the two apps (e.g. Skype), the icon of the other one (GoldenDict in this case) gets temporarily restored.

---

### Post by a-karimi-k on 2017-01-12
> **smorozov said:**
> I have the same issue with Skype and GoldenDict tray icons after upgrading to Ubuntu 16.10. The icons are displayed fine right after login, but if the screen gets locked and then unlocked, both icons are replaced with the error ones. If I close either of the two apps (e.g. Skype), the icon of the other one (GoldenDict in this case) gets temporarily restored.

I also have the same experience. Any workaround?

---

