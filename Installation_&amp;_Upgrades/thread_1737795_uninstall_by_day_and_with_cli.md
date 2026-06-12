---
title: "uninstall by day and with cli"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Morpholinux on 2011-04-23
hi! I was wondering if there is a way to uninstall the last programs installed in a certain day with the cli?

I know that with ```
 cat /var/log/dpkg.log | grep "\ install\ "|grep 2011-04-23 "
``` I can get the "lots of things" I installed today....but how to give that list to apt or something to get them uninstalled?

thanks

ps. I do not want to open synaptic package manager and uninstall all of them one by one...

---

### Post by K_45 on 2011-04-23
Get the name of the packages with that command, then

```
sudo apt-get remove *app app app*
``` replacing app with what you want to uninstall. You can also remove the config files with --purge switch.

---

