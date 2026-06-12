---
title: "Ubuntu 22.04 Beta - New default in unattended-upgrades makes installation slow"
date: 2022-04-12
forum: Installation &amp; Upgrades
---

### Post by bjarnesk on 2022-04-12
We're about to finish automatic installation of Ubuntu 22.04 Beta with PXE boot, but the new  --minimal-upgrade-steps default for unattended-upgrades makes it too slow. Ie it installs one and one package. Perhaps ok when servers are installed, but I'd rather speed up installation and handle any fallouts.

From the man page of unattended-upgrades

       --minimal-upgrade-steps
              perform upgrade in minimal steps (cancel with SIGINT). This is the default now.

       --no-minimal-upgrade-steps
              do not perform upgrade in minimal steps

There are some ways to solve this, but not possible to implement.

early-commands: runs before even the disk is partitioned
late-commands: runs after installation is finnished and unattended-upgrades have already run with slow one and one package update.

Possible fixes we have thought of, but are prevented by doing due to no place to inject it in user-data :

Do unattended-upgrades ourselves with option  --no-minimal-upgrade-steps
Inject a line into /etc/apt/apt.conf.d/unattended-upgrades with Unattended-Upgrade::MinimalSteps "false";
Disable updates and handle it in late-commands, but it only accept options all or security. We've set it to security to avoid more slowdown.

Any tips would be welcome

Cheers,
Bjarne

---

