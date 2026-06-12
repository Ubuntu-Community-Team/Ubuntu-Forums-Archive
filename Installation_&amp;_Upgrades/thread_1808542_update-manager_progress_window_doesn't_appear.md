---
title: "update-manager: progress window doesn't appear"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by mokrates on 2011-07-20
Following problem:

(I use Gnome (netbook-remix, which is kinda vanilla ubuntu gnome with maximus) without Unity)

the update-manager detects available updates, and the update icon appears. I click on it. The update-manager windows appears with all the available updates (where i can view and uncheck particular packages). I click on 'start update' (or what the button says.). update-manager asks me to input my password (cause the update needs root). 

After I enter my pw and click ok, nothing appears. The update runs, i can check that with ps on a console, and it finishes correctly. But the window with the update-progress doesn't show. sometimes there appear windows which ask me to restart nautilus or firefox or the 'power-button-icon' goes red to tell me to restart. everything works, but i don't get to see the progress, which is kinda annoying. I switched to update on a terminal, but that's just a workaround.

i suspect a problem with rights for my X-Server, but .xsession-errors (both in my user-$HOME and in root's $HOME) doesn't give me any error messages which would help me.

Sadly I don't know when this problem appeared. It may be since the update from 10.10 to 11.04, but i'm not sure.

thanks for your input

mo

---

### Post by mokrates on 2011-07-22
quick update

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/712292](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/712292)

---

