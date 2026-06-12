---
title: "Upgrading from Sarge -&gt; Breezy"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by Hypatia2 on 2005-10-27
I've got an old PC at home tat I've been using as a server running debian Sarge for a couple years. I rarely run an X server on it. Now, I'd like upgrade it to Breezy. Has anyone got any tips or advise on upgrading Sarge to Breezy?

I'd rather avoid having to reinstall.

I'm tempted to edit my sources.list to point to Breezy, and run apt-get dist-upgrade.  Will it work?

Thanks,
 Hypatia2

---

### Post by az on 2005-10-27
[QUOTE=Hypatia2]I've got an old PC at home tat I've been using as a server running debian Sarge for a couple years. I rarely run an X server on it. Now, I'd like upgrade it to Breezy. Has anyone got any tips or advise on upgrading Sarge to Breezy?

I'd rather avoid having to reinstall.

I'm tempted to edit my sources.list to point to Breezy, and run apt-get dist-upgrade.  Will it work?

Thanks,
 Hypatia2[/QUOTE]


It worked for me.

The transition from xfree86 to xorg makes you need to hit enter about fourty times during the dist-upgrade, but it works.

---

