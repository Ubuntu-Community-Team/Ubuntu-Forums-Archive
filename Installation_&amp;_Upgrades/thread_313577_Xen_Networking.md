---
title: "Xen Networking"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by sprucio on 2006-12-06
I've managed to setup Xen with ease but I'm having a difficult time trying to configure the network interfaces using a bridged network.

After starting xend, I see multiple interfaces like peth0, xenbr0 and such but I don't know which of these interfaces need to be configured.

Can anyone shed some light on this topic?

---

### Post by sprucio on 2006-12-06
Do I need to need to edit /etc/networking/interfaces in dom0, domU or both?

I've tried researching this for a good part of the day but I can't seem to find a solution.

---

### Post by cinderdust on 2006-12-08
You should configure dom0 & domU the 'normal' way with /etc/networking/interfaces.

The strange interfaces on dom0 (peth0, vif0.0, vif7.0, xenbr0) are used by xen for internal communication. Somehow. I don't understand the details and they don't seem to matter to me (yet).

When you config dom0 just work with eth0.

On a domU, I had trouble configuring eth0. I kept getting interface not found errors until I decided to call it eth1 and that worked. I don't know why. Per Xen manual eth0 'should' work.

This was on dapper with binary install of xen3.0.3

---

