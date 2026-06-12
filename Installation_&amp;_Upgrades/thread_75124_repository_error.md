---
title: "repository error"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by tregetour on 2005-10-13
When I ask synaptic to reload packages it gets stuck, I hit cancel and it tells me:

<code>
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
</code>

Any explination and or help would be much thanked.

---

### Post by meborc on 2005-10-13
hmm... is it just me, or are you missing some / marks in the addresses... just a thought... ;)

---

### Post by tregetour on 2005-10-13
Erp -- I panicked too soon -- it fixed itself -- sorry to bother y'all.

---

### Post by InsomniacUK on 2005-10-13
I'm having the same problem. gb.archive.ubtuntu.com seems to be totally unresponsive at the moment.

---

### Post by meborc on 2005-10-13
right now, *as we speak*, millions of [COLOR="DarkRed"]**m$**[/COLOR] former users are downloading [COLOR="Sienna"]5.10[/COLOR] updates... i for one will stay way clear of apt-get until the situation is cooled down... there is no need to further put pressure on servers, which are flat out as they are already... so if u have some minor updates, with what u can wait for few weeks, i say that let the upgrade period go by and not go mad about having troubles with installing themes or games or applications or whatever which are acctually not needed anyway :D

---

