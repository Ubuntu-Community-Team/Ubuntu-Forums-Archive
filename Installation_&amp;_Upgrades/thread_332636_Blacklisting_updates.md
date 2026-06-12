---
title: "Blacklisting updates"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by loftwyr on 2007-01-06
I have a new install of Edgy on an Acer Aspire 5050. With the installation, it works fine but when the kernel security update (10.34) gets installed, it no longer boots. Kernel panic from the ide driver.

I have figured out how to back out the update but how do I prevent it from being installed again? As soon as I back it out and reboot, it shows up as an update in the update manager.

I'd like to prevent this update from being applied but I don't know how to blacklist it.

Help?

---

### Post by loftwyr on 2007-01-06
I've continued to search but even forcing the version doesn't help, although it crashes the package manager.  

I've turned off automatic updates so I'm safe from the kernel panic for now but I could really use a hint on how to make this update go away.

---

### Post by uniq.user on 2007-01-17
> **loftwyr said:**
> I have a new install of Edgy on an Acer Aspire 5050. With the installation, it works fine but when the kernel security update (10.34) gets installed, it no longer boots. Kernel panic from the ide driver.

I have figured out how to back out the update but how do I prevent it from being installed again? As soon as I back it out and reboot, it shows up as an update in the update manager.

I'd like to prevent this update from being applied but I don't know how to blacklist it.

Help?

To blacklist updates in apt-get edit the file /etc/apt/apt.conf.d/50unattended-upgrades:
My file looks like this:

// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu dapper-security";
//      "Ubuntu dapper-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//      "vim";
        "gaim"; "gaim-data";
};


NOTE THE "gaim"; "gaim-data"; line.
This entry blacklists gaim and gaim-data packages from being updated.

---

