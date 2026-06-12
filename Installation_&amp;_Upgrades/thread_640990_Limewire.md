---
title: "Limewire"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by studlee on 2007-12-14
i've installed the .deb limewire package and now everytime i try to install or run the updater or synaptic i get this error

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package limewire-basic needs to be reinstalled, but I can't find an archive for it.'

i can't reinstall it or remove it. is there a way to remove it or block the updater and synaptic from trying to update/reinstall it.

---

### Post by taurus on 2007-12-14
Try running these commands from a terminal.

```
sudo dpkg --config -a
sudo apt-get update
sudo apt-get upgrade
```

---

