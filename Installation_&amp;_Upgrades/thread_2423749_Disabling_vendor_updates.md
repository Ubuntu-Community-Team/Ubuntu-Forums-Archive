---
title: "Disabling vendor updates"
date: 2019-07-28
forum: Installation &amp; Upgrades
---

### Post by apg6xswhjc on 2019-07-28
Hi

I'm running 19.04 on a Dell, and I foolishly answered "Yes" to checking for 3rd party/vendor updates to one of the questions on install (don't remember the exact phrasing).

In my Ubuntu Software, under Updates it's listing a Dell BIOS update. They are old BIOS versions that are known to be a problem. So, I don't want these updates checked or installed at all. I'll manage them myself and don't want them updated ever by Ubuntu.

I think this may be related to fwupd, but I guess my question is how can I stop this altogether and prevent this being listed in my updates?

Thanks

---

### Post by apg6xswhjc on 2019-07-29
After searching around, I bit the bullet.

I checked what I had installed and relevant services were  fwupd-offline-update.service and fwupd.service, and packages fwupd-signed, fwupd, and libfwupd2

I ran ```
sudo apt-get purge --auto-remove fwupd
```

I got 2 errors/informational warnings.

```
dpkg: warning: while removing fwupd, directory '/var/lib/fwupd' not  empty so not removed 
dpkg: warning: while removing fwupd, directory  '/var/cache/app-info' not empty so not removed

```

Rechecking, both the services and fwupd and fwupd-signed packages were removed. libfwupd2 remained, so I have left that for the time being.


In my Ubuntu Software, under Updates the Dell BIOS update is no longer listed.

The only issue I've noticed is that when opening Ubuntu Software for the first time it says "Sorry, something went wrong". But it seems to operate OK. I assume there is some hard hook to fwupd in there.

---

