---
title: "Quiet upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by -Zeus- on 2010-04-30
Every time I have upgraded Ubuntu, it always goes through a number of steps, with prompts.  "Remove packages"... "unsupported packages"... "configuring grub-pc".  Is there a good way to do an upgrade with no intermediary human intervention?  Stuff at beginning and end is fine, but not partway through.  This isn't a server, I'm just lazy and want to do it overnight.

Thanks.

---

### Post by phillw on 2010-04-30
Hi,

there is an unattended upgrade (update?) option, but i cannot find any documentation on it.

Automated Updates
Use Synaptic Package Manager:
System -> Administration -> Synaptic Manager -> Settings -> Preferences -> General -> Reloading Outdated Package Information -> Automatic

Regards,

Phill.

---

### Post by -Zeus- on 2010-04-30
> **phillw said:**
> Hi,

there is an unattended upgrade (update?) option, but i cannot find any documentation on it.

Automated Updates
Use Synaptic Package Manager:
System -> Administration -> Synaptic Manager -> Settings -> Preferences -> General -> Reloading Outdated Package Information -> Automatic

Regards,

Phill.

Hi PhilW,

I think that is just about the normal update process, I'm talking about a distro upgrade.

---

### Post by cariboo on 2010-04-30
Make sure you are fully up-to-date. Remove any packages you installed via dpkg that aren't in the repositories, disable any ppa's, you will see a message that it is upgrading grub, as there is a newer kernel, but you shouldn't have to intervene unless you've got a custom grub.cfg.

---

