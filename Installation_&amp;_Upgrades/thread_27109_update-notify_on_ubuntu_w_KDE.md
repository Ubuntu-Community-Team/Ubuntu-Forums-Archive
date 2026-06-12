---
title: "update-notify on ubuntu w/ KDE"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by Rory on 2005-04-14
Hi,

I've been trying Kubuntu but am not keen to continue as it doesn't have the update-notify that ubuntu does, and I want ensure I get security updates as they're released.

I understand that I can load ubuntu and then add kde through the repositories fairly easily.  If I do this, is this a way to have an Ubuntu KDE OS with the update-notify?

Thanks,
Rory

---

### Post by nocturn on 2005-04-15
[QUOTE=Rory]Hi,

I've been trying Kubuntu but am not keen to continue as it doesn't have the update-notify that ubuntu does, and I want ensure I get security updates as they're released.

I understand that I can load ubuntu and then add kde through the repositories fairly easily.  If I do this, is this a way to have an Ubuntu KDE OS with the update-notify?

Thanks,
Rory[/QUOTE]

I haven't tried this myself (running plain Ubuntu), I see two ways this could work if update-notifier supports the freedesktop specification.   

I think the program is called update-notifier, but check it to make sure.

1. Using session management
- start update-notifier with the run command in the KDE menu
- save your session
- log back in and check if it is running (command line, with ps aux |grep update)

2. without session management
- Check which folder is your KDE Autostart (assuming $HOME/.kde/Autostart).
- Open a terminal
- cd $HOME/.kde/Autostart
- ln -s `which update-notifier`
- log back in and check it it is running.

Good luck.

---

