---
title: "gdm failing to start but no logs"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by byronsalty on 2007-10-21
On a clean install of Gutsy, when I try to startup after the install I get sent to the command line login. There are no messages about gdm failing to start there but if I hit Ctrl+Atl + F1 on the splash screen I see all the messages going by and there is the:
```
 Starting Gnome Desktop Manager .... [fail] 
```
in the list. 

When I try ```
sudo /etc/init.d/gdm restart
``` I get the same [fail] result. 

The odd thing is I have no idea what's going on because I don't get any error logs. I checked /var/log/gdm and it's completely empty. I did a find /var/log -mmin -15 after attempting a startup and I don't see anything useful. 

Can someone tell me where to look to find out why GDM won't start properly?

---

### Post by byronsalty on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/155403](https://bugs.launchpad.net/ubuntu/+bug/155403) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Added Launchpad bug report.

---

