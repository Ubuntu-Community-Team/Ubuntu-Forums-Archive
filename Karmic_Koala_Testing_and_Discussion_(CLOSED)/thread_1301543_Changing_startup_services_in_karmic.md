---
title: "Changing startup services in karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by matthewbpt on 2009-10-26
Karmic has transitioned to officially use upstart now I gather, so what is the procedure to enable and disable services now? Before there was a Services menu option in System > Administration that showed some services, and you could the package sysvconfig to change the services which would start on boot. But now the menu item is gone, and the sysvconfig package is no longer in the repos. I understand that upstart is supposed to be better than the old init method, but I want it to be configurable too!

Cheers,
Matt

---

### Post by slakkie on 2009-10-26
```

cd /etc/init
sudo service gdm stop
sudo mv gdm.conf gdm.letsnotstartatboot

```

This is basicly it, don't know if there is a (graphical) tool to dis/en-able startup scripts like update-rc.d does.

In short, upstart looks in /etc/init/* for .conf files, if these are present it tries to start the service.

To enable it:
```

cd /etc/init
sudo mv gdm.letsnotstartatboot gdm.conf
sudo service gdm start

```

man upstart
man 5 init

---

### Post by MacUntu on 2009-10-26
And for those services not in /etc/init it's still update-rc.d I guess. At least that's what I've used to prevent apache2 from starting automatically.

---

### Post by slakkie on 2009-10-26
Yes, for non-migrated stuff update-rc.d is still the tool to use.

---

### Post by mdurham on 2009-10-26
Can't you use 'bum' for this?

---

### Post by slakkie on 2009-10-26
bum is not upstart compliant afaik

---

### Post by mdurham on 2009-10-26
> **slakkie said:**
> bum is not upstart compliant afaik

Give it a try, it seems to work ok for me.

---

### Post by slakkie on 2009-10-26
Not here. kdm is managed by upstart and does not exist in /etc/rc?.d and bum is reporting it as not active, while it is started at system boot.

---

