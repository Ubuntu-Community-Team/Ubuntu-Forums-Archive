---
title: "how to install ONLY Gnome?"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by kcy29581 on 2005-06-11
Hi all,

I installed Ubuntu with the option server, to get a minimal installation and work from there. I have just installed xorg, but how do I install Gnome? I can see the package ubuntu-desktop, but that installs other things like gaim, openoffice, etc, not just the basic Gnome.

Any ideas on how to do this?

Thanks

---

### Post by gil-galad on 2005-06-11
Unless you have 56k or something, just install ubuntu-desktop.  It doesn't install that many extra apps, and you will get everything you need for gnome.

Or if you just want a basic gui you can always install XFCE or icewm.

---

### Post by kcy29581 on 2005-06-11
so are you saying that there is no "metapackage" that installs only gnome? You have to take the extra programs as a consequence?

In debian there is a package called gnome-desktop-environment for this purpose for example

---

### Post by SGC on 2005-06-11
**apt-get install gnome** will take 473 mb of disk space while **apt-get install ubuntu-desktop** will take 571 mb. It is not minimal , but 100 mb less.

---

### Post by kcy29581 on 2005-06-11
[QUOTE=SGC]**apt-get install gnome** will take 473 mb of disk space while **apt-get install ubuntu-desktop** will take 571 mb. It is not minimal , but 100 mb less.[/QUOTE]i havent seen the gnome package.. is it in universe or something?

---

### Post by kcy29581 on 2005-06-11
yep, just verified that I have no "gnome" package. apt-get install gnome, says no such package

---

### Post by SGC on 2005-06-11
[QUOTE=kcy29581]i havent seen the gnome package.. is it in universe or something?[/QUOTE]
 Yes it is in the universe repro

But wait I found more minimal gnome packages (both in the universe repo) :

apt-get install gnome-core.............................183 mb
apt-get install gnome-desktop........................295 mb

---

### Post by kcy29581 on 2005-06-11
am I right in saying that the gnome packages in universe aren't as "safe" as the ones in the official repos as they don't get security updates from the Ubuntu security team?

---

### Post by kvidell on 2005-06-11
[QUOTE=kcy29581]am I right in saying that the gnome packages in universe aren't as "safe" as the ones in the official repos as they don't get security updates from the Ubuntu security team?[/QUOTE]
 They're still the official repos, it's just that it's not a Ubuntu-Coded piece of software.
It's as safe as the version I have installed :) Only difference is you're installing it post-distro-configuration and I installed it during distro-configuration.
So no real risk or difference :)
- Kev

---

### Post by SGC on 2005-06-11
[http://www.ubuntulinux.org/wiki/MOTUSecurity/view?searchterm=universe%20security](http://www.ubuntulinux.org/wiki/MOTUSecurity/view?searchterm=universe%20security)
> The Ubuntu Linux Security Team takes care on the vulnerabilities within the universe repositories packages...

---

