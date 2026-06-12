---
title: "ssh - Temporary failure in name resolution"
date: 2021-09-25
forum: Installation &amp; Upgrades
---

### Post by aljames2 on 2021-09-25
I upgraded my Ubuntu desktop to 20.04 from 18.04.  Now, when my backup server runs the script to pull backups from this new 20.04... I get this.

```
ssh: Could not resolve hostname backup-client-251: Temporary failure in name resolution
```

My ~/.ssh/config file still has the same host info it always had:

```

host backup-client-251
  user rdiff-bak
  hostname 192.168.102.251
  port  34629

```

I can ping & ssh into the desktop using the IP address, but not using "backup-client-251"

Probably something simple that got reset on the desktop upgrade.  Appreciate any tips.

Edit:  My DNS resolver is my pfsense router:  192.168.102.1

---

### Post by aljames2 on 2021-09-25
I was able to get past this problem by restarting SSH service on my backup server.  I am now having a different problem with rdiff-backup which I will start another thread to discuss.

---

