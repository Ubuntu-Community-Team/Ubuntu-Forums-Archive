---
title: "package upgrade info"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Hawkoon on 2011-02-05
Whenever I log in via ssh, I am being informed how many packages should be upgraded, and how many of these upgrades are security updates.

```
Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

52 packages can be updated.
19 updates are security updates.

```

Where is that info coming from? When I simulate an upgrade with ```
apt-get upgrade -s
``` I only get a list with the package versions to be installed. Also, using apt-get I can't find a way to resolve which of these updates are security related.

Anyone there to point me in the right direction?

Tanks,

Hawkoon

---

