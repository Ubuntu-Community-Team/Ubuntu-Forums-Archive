---
title: "Preseeding network configuration without NetwerkManager"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by diska on 2007-12-17
Short question: Can I disable to installation of NetworkManager through preseeding?

Long version with background info:

I'm currently setting up an automated setup for use on the desktop computers of our company. The plan for the system is as following:

    * Unattended install using Preseeding
    * Managing the desktops using puppet
    * Authentication through ldap

Now the problem is that the default install of an ubuntu-desktop uses NetworkManager. This causes the puppet client to always exit when it's invoked through the init scripts because network interfaces aren't up yet. Also, when configured for LDAP the system hangs at boot, likely because it's doing user/group lookups while the network is not configured yet.

Uninstalling NetworkManager and configuring /etc/network/interfaces solves those problems. Now I'm wondering how to do this using preseeding. NetworkManager isn't part of the ubuntu-desktop meta packages so I was hoping I could somehow exclude it from the installation. I'll also need something to configure the interfaces file.

Ofcourse I could do this with a custom script that's run at the end of the installation, but I would like to keep all my customization handled through puppet so I'm hoping there's a way to disable NetworkManager during install.

---

