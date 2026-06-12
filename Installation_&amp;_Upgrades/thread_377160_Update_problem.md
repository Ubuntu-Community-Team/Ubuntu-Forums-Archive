---
title: "Update problem"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2007-03-05
Using Edgy.
Update Manager doesn't work.

"sudo update-manager" returns "warning: could not initiate dbus".

Any advice would be appreciated.

Cheers

---

### Post by morganGDFP on 2007-03-11
have you tried using gksudo instead of sudo?

---

### Post by Kateikyoushi on 2007-03-11
Check in system > administration > services that dbus is started.

---

### Post by Buster95 on 2007-03-11
The dbus box is ticked.
Is there any way of determining whether it is active?
Thanks

---

### Post by Kateikyoushi on 2007-03-12
Is that all the error message you get ? I found this on launchpad. [LINK]("https://launchpad.net/ubuntu/+source/update-manager/+bug/58424")

> warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply.

This message is harmless and should probably be removed.

Can you update from terminal ?

```
sudo aptitude update
```

---

### Post by Buster95 on 2007-03-12
Tried that. Same result.
Cheers

---

