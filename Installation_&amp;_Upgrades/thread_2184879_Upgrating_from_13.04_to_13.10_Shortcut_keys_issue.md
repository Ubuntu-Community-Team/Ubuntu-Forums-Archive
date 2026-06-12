---
title: "Upgrating from 13.04 to 13.10 Shortcut keys issue"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by anish.man on 2013-10-30
Does any one face the following issue after upgration from 13.04 to 13.10

1. Terminal shortcut not work. [Ctrl+Alt+T] is not open the terminal window i have checked the shorcut prefreance the key was assign for this shortcut.
2. System Lock shortcut not working. [Ctrl+Alt+L] worn lock my system any more.
3. Workspace Keys not working. when i switch workspace from left to right or viceversa it works for two uper workspace tab but the shortcut keys [Ctrl+Alt+Down] or [Ctrl+Alt+Shift+Down] not workin. The temprory sollution i just reassign those keys using CCM(compiz) in Desktop > Desktopwall > Binding > (move within wall) and (Move windows within wall)

---

### Post by Myna_MeFirst on 2013-11-01
Same issue here. The thing that is weird though, is that it was working for a week after the update, and it just stopped working yesterday. I've been racking my head trying to figure out what i may have changed, but the only thing that comes to mind, is that while docking and undocking the laptop i had some issues, and while trying to get the screen to come back up, the environment restarted (but the machine didn't reboot, so probably lightdm), and then it came back up automatically. My icons theme was reset and perhaps it broke something else.
Not sure if this helps anyone in finding out why the keys are not working, but there it is.

------------
UPDATE
------------
I found an article that offer a solution that worked for me. [http://askubuntu.com/questions/360696/keyboard-not-working-100-after-ubuntu-13-10-upgrade](http://askubuntu.com/questions/360696/keyboard-not-working-100-after-ubuntu-13-10-upgrade)
You need to try each option between Default, Ibus and none, and relogin in between (logout/login is sufficient). when i opened it the first time it was in default, then i tried none, then ibus, and finally back to default, all with logout/login in between. Now things work.
Weird? oh yes, but i am glad this fixes it.
good luck

---

