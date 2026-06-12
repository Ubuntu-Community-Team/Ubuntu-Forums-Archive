---
title: "Started 20.04-&gt;22.04 upgrade with local GUI. Possible to finish remotely?"
date: 2022-09-28
forum: Installation &amp; Upgrades
---

### Post by Phasmus on 2022-09-28
I started my OS upgrade in-person yesterday but had to leave the office while it was still updating packages. 

This morning logging in remotely my MOTD is:

```
Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.4.0-125-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

1747 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

New release '22.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

So it's not clear if it's done or not. It definitely hasn't been given permission to restart and quite probably the upgrade has paused asking if I want to replace some config files with the new version or suchlike. Is there any way to safely proceed with this upgrade without returning to my office to interface with the upgrade GUI? I don't want to do anything risky like run do-release-upgrade over ssh on top of an already running upgrade operation unless that's definitely something that will work.

---

### Post by TheFu on 2022-09-28
100% safe? No.

If you were running the do-release-upgrade inside a tmux or screen session, then you could reconnect to that session and see the terminal exactly where it is stuck from anywhere with ssh connectivity. If you don't have ssh setup and didn't start the process inside screen/tmux, then no.

When I was supporting Mom's Linux PC (RIP), I'd start the release upgrade from my home before traveling there the following day. That way, the downtime impact, if there were issues was less than a day. Pre-planning matters.  Plus, I'd ensure a know-I-can-restore backup existed BEFORE doing anything.

Never use the GUI to do release upgrades. That's law #2, after #1, which is thou shalt always, always, always, have an excellent backup before starting.

Remove GUI desktops run in different sessions than the GUI displayed on the local console.

---

