---
title: "How to prevent automatic upgrade/update"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by hanserikbusk on 2007-10-04
I am running Dapper 6.06  LTS server. Running for months with no problems. But after at planned power down it couldn't boot.

The problem was unattended upgrade of the kernel to 2.6.15-29 from 2.6.15-28. The new kernel was obviosly placed above the BIOS supported cylinders.

Pretty bad for a server with multiple databases on VMWare machines. 
 
The boot area now has its own partition on the first part of the disk, but the VMWare server also had to be reconfigured to the new kernel.

Unattended upgrades is clearly a bad thing for what this cumputer is used for.

I have studied the /etc/cron.daily/apt to figure out why the upgrade took place, but I am not that good in deciphering bash-scripts.

Could someone please give me a hint: how can I stop the automatic update/upgrade of the kernel.
:(

---

### Post by pmorch on 2008-03-05
Does your system happen to contain
```
APT::Periodic::Unattended-Upgrade "1";
```
Anywhere? What does "sudo grep -r 'Unattended-Upgrade' /etc/" show? Here on gutsy and feisty there is a funky /etc/apt/apt.conf.d/50unattended-upgrades containing:
```

// allowed (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu feisty-security";
//      "Ubuntu feisty-updates";
};

// never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//      "vim";
};

```

Does /var/log/unattended-upgrades/ contain anything? I guess you could uninstall the unattended-upgrades package, as this seems to be the package with the functionality...

Hope this helps a little.

Peter

---

