---
title: "upgrade errors"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Gareth_2007 on 2011-10-16
hey all,

right Ive just upgraded to Ubuntu 11.10 and i saw a lot of errors occurring while it was updating. where can i view the log to see what went on? 

thanks

---

### Post by Gareth_2007 on 2011-10-16
wow ok maybe some one should rename Ubuntu 11.10 (Oneiric Ocelot) to Ubuntu 11.10 (Don't even bother) i now have 2 systems and one server all unable to boot after the update!

---

### Post by youngunix on 2011-10-16
> **Gareth_2007 said:**
> wow ok maybe some one should rename Ubuntu 11.10 (Oneiric Ocelot) to Ubuntu 11.10 (Don't even bother) i now have 2 systems and one server all unable to boot after the update!

they don't boot AT ALL, no splash screen, no black screen with messages, nothing...?

---

### Post by Gareth_2007 on 2011-10-16
the server has a kernel panic, but sorry the work stations boot but are stuck waiting for the network at login. tried recovering all 3 machines with no luck so about to try fresh build as its costing me money now :/

---

### Post by Lsurzy on 2011-10-17
> **Gareth_2007 said:**
> hey all,

right Ive just upgraded to Ubuntu 11.10 and i saw a lot of errors occurring while it was updating. where can i view the log to see what went on? 

thanks

> **Gareth_2007 said:**
> wow ok maybe some one should rename Ubuntu 11.10 (Oneiric Ocelot) to Ubuntu 11.10 (Don't even bother) i now have 2 systems and one server all unable to boot after the update!

> **Gareth_2007 said:**
> the server has a kernel panic, but sorry the work stations boot but are stuck waiting for the network at login. tried recovering all 3 machines with no luck so about to try fresh build as its costing me money now :/

Ok... How should I begin that I don't sound rude about this, I dunno so I'm just going to say it since it is good general advice regarding updating/upgrading any OS. I apologize for the cynical tone beforehand.

By assumption a new system release contains bugs and compatibility issues. (Yes, a new Ubuntu release is a new OS, not a Service Pack or an Update Rollup...) 

Also, since Ubuntu is based on Debian and it's package management, it is to be assumed that for the first 3 - 6 months the upgrade process will fail and brake spectacularly.

And since you obviously are running a business;

You should never try and upgrade your production environment like this. The whole upgrade-system in itself is a total kludge. (Applies to all operating systems)

To even consider adopting the new version of a whole operating system, I would do a test installation in a controlled environment (i.e. a virtual machine) and play around for the next 3 - 6 months. And only if I deem it absolutely necessary, upgrade the environment. By making a fresh installation and building the system back up from the ground. (Since reinventing the wheel seems to be the point of GNU/Linux projects these days, this is the only sane option anyway.)

"If it works don't fix it."


This is why Canonical provides long term support releases. Needless to say that fore mentioned assumptions still applies: The upgrade scripts will will brake something.

---

