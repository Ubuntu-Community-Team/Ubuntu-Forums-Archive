---
title: "Update OpenOffice but not through apt-get"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by matthewboh on 2008-11-25
I uninstalled OpenOffice so I could go with Version 3.0.  I'm now getting an important update message, and it wants to update Openoffice-core and the ttf-fonts - but I just checked in apt-get and there's nothing installed for OpenOffice.  Is this a problem or should I just go ahead and install it?

---

### Post by taurus on 2008-11-25
Maybe you want to remove all the dependencies as well.

```
sudo apt-get autoremove
sudo apt-get update
```

---

### Post by matthewboh on 2008-11-25
That did it!  Thanks

---

