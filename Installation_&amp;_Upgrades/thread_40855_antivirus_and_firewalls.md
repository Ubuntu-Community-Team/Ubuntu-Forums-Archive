---
title: "antivirus and firewalls"
date: 2005-06-10
forum: Installation &amp; Upgrades
---

### Post by newbie_ubuntu on 2005-06-10
I am a newbie as far as linux goes..as my login should suggest.

I am curious.. IS there a need for antivirus and firewalls on a linux system. why so?

If yes, please suggest a package that I can load on mu ubuntu machine.

Thanks

---

### Post by simbaB on 2005-06-10
Firewall is necessary unless you are behind a NAT box (like a cable/DSL router). You can 'apt-get install firestarter' for an easy-to-use GUI. Anti-virus is not necessary but is available. Check out [http://www.clamav.net/](http://www.clamav.net/). It's available as a package, although it's mainly intended for servers that serve Windows clients.

---

### Post by az on 2005-06-10
Antivirus, no.  Linux does not grow viruses very well.  Think of it as a pretty much sterile environment.  Viruses have no opportunities to grow.

Firewall, not really.  Nothing is installed by default (in Ubuntu) which listens to the outside world.  If you install a firewall and want to use an app which does, you are going to have to open that port anyway.

---

