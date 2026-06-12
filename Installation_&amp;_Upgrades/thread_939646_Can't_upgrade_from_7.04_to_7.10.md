---
title: "Can't upgrade from 7.04 to 7.10"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by mad_ady on 2008-10-06
Hello everyone,

I've just managed to upgrade my Ubuntu 6.06 to 7.04 after its life-time expired (it was a painful experience), and now I'm trying to get it up to date to the current release.

I can't however upgrade from 7.04 to 7.10! When I launch update-manager -c, it sees the upgrade as available, but when I click Update, it says that maybe the servers are overloaded and doesn't do anything else.

I doubt the servers are down; How can I find more information about this and how can I troubleshoot it?

---

### Post by Braytok on 2008-10-06
Its early monday morning where I am and lots of folks are trying out the latest 8.10 builds so it could be that the servers are in fact a bit over loaded.

I would suggest trying to download the 7.10 ISO and burning it to disk and try the upgrade that way.

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

but bear in mind 7.10 has some critical security issues so you'll want to update it right away if you do.

---

### Post by mad_ady on 2008-10-06
Thanks for your help; I will try the iso; and I will upgrade out of 7.10. I plan to arrive to 8.10, but I still have two upgrades to go. :)

---

### Post by Pumalite on 2008-10-06
If you are trying the ISO; it has to be the Alternate CD:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Don't forget to have your 7.04 fully up to date and remove all third parties from /etc/apt/sources.list

---

### Post by mad_ady on 2008-10-07
Thank you all for your help. It was a very painful experience (and I am a seasoned linux user), but I managed to upgrade to 7.10.

First the installer would quit because it couldn't uninstall ubuntu-minimal (uninstalled it by hand), then it complained it couldn't install some core packages related to python (I don't remember the exact packages); dpkg would fail configuring them because of a missing directory in /var/cache. After creating the directory I managed to trick it to install (sort of - it still died when it had 10 min left!).

Next, I tried to upgrade to 8.04LTS. Tried the web based update - of course the servers are overloaded :(.
Downloaded the iso and ran update from the cd - it crashes without error messages while calculating packages to be removed.

It seems I'm better of trying to do a clean install. 

Pitty, another upgrade from 7.04 earlier this year worked without problems on a different computer...

---

