---
title: "upgrade 23.10 -&gt; 24.04.1 : post release upgrade upgrade: no linux-generic-hwe"
date: 2024-08-30
forum: Installation &amp; Upgrades
---

### Post by matt-rw on 2024-08-30
I just upgraded from 23.10 to 24.04.1, after install and reboot, I log in, get message that there are updates, and then this:
```

root# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-generic-hwe-20.04 : Depends: linux-generic-hwe-22.04 but it is not installable
 linux-headers-6.5.0-44-generic : Depends: linux-headers-6.5.0-44 but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

Should I do as suggested?

---

### Post by matt-rw on 2024-08-30
I pulled the trigger: 
```
root# apt --fix-broken install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  mailcap
Use 'apt autoremove' to remove it.
The following packages will be REMOVED:
  linux-generic-hwe-20.04 linux-headers-6.5.0-44-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 29.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 457504 files and directories currently installed.)
Removing linux-generic-hwe-20.04 (5.15.0.60.58) ...
Removing linux-headers-6.5.0-44-generic (6.5.0-44.44) ...
root# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  mailcap
Use 'apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

