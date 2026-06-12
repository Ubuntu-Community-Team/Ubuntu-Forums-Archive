---
title: "Can't upgrade to 14.04"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by Krabun on 2014-04-17
I'm trying to upgrade from 13.10 to 14.04: (Main server)
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove
update-manager –d
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Software updater: No updates available

---

### Post by Mark Phelps on 2014-04-17
Updates are not universally available on all servers at the same time.  

You should generally wait a few days as the servers are getting hammered right now and a download that could take a few minutes any other day could easily take an hour or more on "release day".

---

### Post by grahammechanical on 2014-04-17
Why do you not use Software Updater?

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

You could also try the command

[FONT=arial]```
[COLOR=#333333]do-release-upgrade[/COLOR]
```[/FONT][COLOR=#333333][FONT=monospace][FONT=arial]

I am not sure what update-manager -d does but I think that it prompts the Update Manager to check is an Upgrade to the next release is available.

There is no rush. 140.04 will be with us for a long time. And many people will be trying to download and upgrade at this time. The servers will be slow.

Regards.
[/FONT]
[/FONT][/COLOR]

---

### Post by Krabun on 2014-04-20
Thanks for the reply.

---

