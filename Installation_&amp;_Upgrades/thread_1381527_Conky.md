---
title: "Conky"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2010-01-14
Once installed, I can start it in the terminal, but after closing the terminal used to start Conky, I can't run my mouse over Conky or it will disappear. Once it disappears, I don't see it again until I give the shutdown command to Ubuntu. What am I doing wrong or what do I need to do to get Conky to not disappear?

---

### Post by running_rabbit07 on 2010-01-14
I am having the exact problem in Lucid also.

---

### Post by running_rabbit07 on 2010-01-15
And then?

---

### Post by Kevbert on 2010-01-15
If you close terminal after starting conky from terminal it will close soon afterwards. You need to go to System-Preferences-Startup Applications and add conky (as the command and name).

---

### Post by running_rabbit07 on 2010-01-15
Thanks for the reply, I have tried that also. Conky shows up and the first time I click on something, Conky disappears and doesn't show again until shutdown. In each situation, Conky still shows as running in the System Monitor.

---

### Post by Kevbert on 2010-01-16
Are you running a wallpaper switcher ? eg Drapes.
It may be an own_window setting in the conky script you're trying to run, not sure which one, but here's an extract from mine:
```
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar

```

---

