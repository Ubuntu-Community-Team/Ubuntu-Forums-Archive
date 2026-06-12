---
title: "Troubles with updates..."
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by hellomatts on 2007-12-05
When I try updating, I get the following errors:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Can anyone help me with this?

Thanks!

---

### Post by sistoviejo on 2007-12-05
Are you updating from command line or from the update manager?
This might happen because you have another instance of the udpate manager or synaptics package manager open or because the update manager has no root privileges.
You could try to close all update manager sessions and/or synaptics package manager and try again.
Also you can try running gksudo update-manager from the command line.

---

### Post by kanna1620 on 2008-05-03
I had the same problem. And it is solved by just removing that lock file.

Just done this.

```
sudo rm /var/cache/apt/archives/lock
```

---

