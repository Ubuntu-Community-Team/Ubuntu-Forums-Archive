---
title: "errors - upgrade usiing update manager"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Ted D. on 2006-06-05
I am getting the following errors. Please advise and thanks
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

---

### Post by jrs1985 on 2006-06-05
Yeah, I'm upgrading from 5.10 & i'm getting this error as well:

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found



I'm using Synaptic update manager.

I'm thinking these servers are down. Can the ubuntu people fix that so that 5.10 users can update please.

---

### Post by jrs1985 on 2006-06-05
any help on this guys? anyone else with this problem?

---

### Post by lerrup on 2006-06-06
[QUOTE=jrs1985]Yeah, I'm upgrading from 5.10 & i'm getting this error as well:

Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found



I'm using Synaptic update manager.

I'm thinking these servers are down. Can the ubuntu people fix that so that 5.10 users can update please.[/QUOTE]

You don't need them to upgrade so untick them in synaptic or put a # by them in the /etc/apt/sources file.  They are not ubuntu official mirrors as far as I can see.

Then I would sudo apt-get update and sudo apt-get dist-upgrade from the command line (or terminal) and sit back and watch.

Good luck!

---

### Post by Ted D. on 2006-06-08
I deleted the items as recommended. Success.
Although I still used the update manager rather than the command method.
Thanks for your help

---

