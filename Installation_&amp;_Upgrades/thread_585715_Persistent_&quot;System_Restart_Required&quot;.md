---
title: "Persistent &quot;System Restart Required&quot;"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by b3nd3r77 on 2007-10-21
Hello,
Recently upgaded to Gutsy and everything is fine except I get a persistent blue icon "System Restart Required" Any clues?

Thanks,
b3nd3r77

---

### Post by rp3 on 2008-06-14
> **b3nd3r77 said:**
> Hello,
Recently upgaded to Gutsy and everything is fine except I get a persistent blue icon "System Restart Required" Any clues?

Thanks,
b3nd3r77

I have the same thing and have checked /var/lib/update-notifier
and found
```
firefox-restart-required
fuse-utils-needs-users-added-to-fuse-group
user-must-execute-asoundconf-set-default-card
```

On this one machine I can't seem to make the icon go away and can't find any help ???  Anyone?

---

