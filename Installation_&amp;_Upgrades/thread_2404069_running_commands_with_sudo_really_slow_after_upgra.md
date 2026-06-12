---
title: "running commands with sudo really slow after upgrade to 18.10"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by riverfr0zen on 2018-10-19
After upgrading to 18.10, every time I try to run a command with sudo, there seems to be a long (I'm talking 25-30 seconds) pause before the command is run that did not exist before.

This happens every time sudo is used, not just the first time during a session. It seems to happen regardless of the command. I did a `sudo ls -l` on a folder and it took 30 seconds whereas a regular `ls -l` was instant.

Anyone have an idea about what's going on?

EDIT: Problem seemed to resolve itself after a reboot.

---

