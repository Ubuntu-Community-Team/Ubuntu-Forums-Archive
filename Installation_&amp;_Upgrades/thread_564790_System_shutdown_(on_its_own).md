---
title: "System shutdown (on its own)"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2007-10-01
Never happened before, my computer came out of sleep mode and did its own Shutdown, which caused me to investigate the menu System --> Administration --> System Log. Under the user.log, with the time Linux went into shutdown are messages like this:

```
Oct  1 06:17:31 user-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
```

My question: does anybody know if these calls to redhat are supposed to be on my Ubuntu??? I only recall installing one .rpm made for Redhat (and it was a botched half-installation)

---

