---
title: "Is There A Safe Way To Cancel Distribution Upgrade"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Pornbuntu on 2007-04-19
Hi,
I've had the update-manager upgrade running all day on the ca.archive.ubuntu.com servers, and (no offense, I realise it's a huge undertaking) but they're running like treacle. (or Maple Syrup i guess :) )
I'm between 0 and 10k most of the time, which means finishing some time next week.

Is there a safe way to abort this half way through, and thereby allow others to perhaps have a happier experience, but without fritzing my edgy install?

Thanks.

p.s.  The server+bandwidth behemoth Google uses Ubuntu internally do they not? Wonder if Shuttleworth can get onto Sergey & co in time for the next release, perhaps a gift of a few extra boxen + pipes for the main archives as assistance. I know they like FOSS. (and one here in Canada just in general. I never get better than about 60k from the poor old ca. servers).

---

### Post by berserker on 2007-04-19
Yes.  No changes are made to your system until all packages are downloaded.

---

### Post by Pornbuntu on 2007-04-19
Ok - but there's also no 'cancel' option. Is this a case of killing the update-manager process?

---

### Post by berserker on 2007-04-19
Yes.  Try 

```
sudo killall update-manager
```

---

