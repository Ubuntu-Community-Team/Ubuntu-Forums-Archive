---
title: "Printpro"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by drinehart on 2007-05-10
I recently tried to install a Dell printer on a Feisty system.  After looking around I found some promising drivers from print pro and downloaded them.  Unfortunately I couldn't get them to work and they are proprietary.  I found another way to install the printer but I now think I have a broken dpkg system because of the way the print pro web site said to install the Dell printer drivers.

The website said to use for Ubuntu:

dpkg -i --force-depends --force-overwrite printpro*.deb

Now when I try to use apt-get install XXXX (random program), I receive the following message:

E: The package printpro-dell needs to be reinstalled, but I can't find an archive for it.

Synaptic says the same thing.  Does someone know how to get rid of this message?

Duane

---

### Post by drinehart on 2007-05-10
Followup:

I saw on the ubuntu geek website this solution:

dpkg --remove --force-remove-reinstreq XXXX (package)

but when I tried it I received the following message:

/etc/init.d/cups: 200: /usr/sbin/cupsd: not found
cups: unable to restart scheduler.

So now I guess I have 2 packages now working.  

Please help.

Duane

---

