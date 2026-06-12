---
title: "removing unwanted packages post upgrade to 16.04"
date: 2016-04-29
forum: Installation &amp; Upgrades
---

### Post by HappyAsHellas on 2016-04-29
Whilst upgrading to 16 I was informed that removing old packages may take several hours. I didn't take the removal option at the time as I didn't have the time to wait. Is it advisable to remove them and if so how do I do it?

---

### Post by deadflowr on 2016-04-29
```
sudo apt-get autoremove
```
will show all packages no longer needed.
Which should include those you decided not to during the upgrade.

I think apt's man page make a nice point about whether to remove or not to remove:
> autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for other packages and are now no
           longer needed as dependencies changed or the package(s) needing
           them were removed in the meantime.

           You should check that the list does not include applications you
           have grown to like even though they were once installed just as a
           dependency of another package. You can mark such a package as
           manually installed by using apt-mark(8). Packages which you have
           installed explicitly via install are also never proposed for
           automatic removal.

---

### Post by vasa1 on 2016-04-30
> **HappyAsHellas said:**
> Whilst upgrading to 16 I was informed that removing old packages may take several hours. I didn't take the removal option at the time as I didn't have the time to wait. Is it advisable to remove them and if so how do I do it?
I got that message as well and accepted the option. It took a just few minutes even though I was upgrading from 14.04 to 16.04.

---

