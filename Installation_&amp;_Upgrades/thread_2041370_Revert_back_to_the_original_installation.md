---
title: "Revert back to the original installation"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by bluexrider on 2012-08-12
How can I revert back to the original installation without reinstalling and reformatting?

I cannot find the CLI that does this but I know it exists.

---

### Post by drs305 on 2012-08-12
Ubuntu does not have default 'system restore' function as far as I know unless deja-dup/duplicity backups have some new functionality.

Two options you do have would be to:
[LIST=1]
[*]Create a new user, which would reset all the user settings to the original defaults.
[*]Create/move your $HOME folder to a new partition, and then reinstall, designating the separate HOME folder and not reformatting it. This would preserve your user settings while the reinstallation would install only the default apps and system settings.
[/LIST]

---

