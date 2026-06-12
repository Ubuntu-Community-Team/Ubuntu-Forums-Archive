---
title: "no multiple screens after upgrade to 14.04"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by pmjs1115 on 2014-08-08
I just did a distribution upgrade through update-manager from 12.04 to 14.04. I get 3-4 messages about failing system programs that I haven't tracked down yet. One very annoying problem is that the ability to choose from 4 screens [lower left in the verticle icons] is gone. Trying to ctrl-alt-arrow produces an error [with no explanation].

Any ideas?

Thanks

Paul

---

### Post by kansasnoob on 2014-08-08
Lots of errors on the first boot after an upgrade to 14.04 seem to be a common thing, does it happen on every boot? Or not related to boot at all? You can see what they were in /var/crash.

Regarding workspaces look here:

[http://askubuntu.com/questions/260510/how-do-i-turn-on-workspaces-why-do-i-only-have-one-workspace](http://askubuntu.com/questions/260510/how-do-i-turn-on-workspaces-why-do-i-only-have-one-workspace)

---

### Post by grahammechanical on 2014-08-08
Keep in mind that the upgrade scripts are designed to upgrade a default 12.04 to a default 14.04. They do not and cannot taken into account all the customizations that users make to the desktop.

Unity in 14.04 looks similar to Unity in 12.04 but actually they are miles apart. We can now change the size of the launcher icons without installing Compiz Configuration Settings Manager, as one example. You will also notice, or perhaps you did not notice, that the icon to reveal the desktop is also gone. But we can get it back.

---

### Post by pmjs1115 on 2014-08-08
Thanks to all. Workspace issue solved. Reboot didn't show the same errors. For anyone who is interested, had to reinstall Google-chrome. So far, all else is working.

[If I knew how, I would mark this solved]

Paul

---

