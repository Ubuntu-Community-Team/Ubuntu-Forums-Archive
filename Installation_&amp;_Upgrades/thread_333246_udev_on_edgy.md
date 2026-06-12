---
title: "udev on edgy"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by bristleburger on 2007-01-07
udev rule syntax seems to have changed somewhere between dapper and edgy. It is now necessary to use the equality operator &#8220;==&#8221; for tests and the assignment operator &#8220;=&#8221; for assignments. With the previous version of udev in Dapper, the &#8220;=&#8221; operator served both functions.

For example, this rule worked well with dapper:
BUS="scsi", SYSFS{model}="Perfection1640", NAME="%k", SYMLINK="scanner", GROUP="scanner", MODE="0660"

...but results in the following errors in /var/log/syslog on edgy:
Jan  5 13:14:21 starbug udevd[2314]: add_to_rules: invalid BUS operation
Jan  5 13:14:21 starbug udevd[2314]: add_to_rules: invalid rule '/etc/udev/rules.d/01-my

This is the correct syntax for edgy:
BUS=="scsi", SYSFS{model}=="Perfection1640", NAME="%k", SYMLINK="scanner", GROUP="scanner", MODE="0660"

---

