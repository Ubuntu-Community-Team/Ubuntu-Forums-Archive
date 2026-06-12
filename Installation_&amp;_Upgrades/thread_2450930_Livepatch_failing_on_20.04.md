---
title: "Livepatch failing on 20.04"
date: 2020-09-23
forum: Installation &amp; Upgrades
---

### Post by timcassidy13 on 2020-09-23
I've seen the below issue for the past few days.
Canonical Livepatch has experienced an internal error. Please refer to [https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues](https://wiki.ubuntu.com/Kernel/Livepatch#CommonIssues) for further information.

```

myuser@mysystem:~$ snap info canonical-livepatch
name:      canonical-livepatch
summary:   Canonical Livepatch Client
publisher: Canonical&#10003;
store-url: [https://snapcraft.io/canonical-livepatch](https://snapcraft.io/canonical-livepatch)
contact:   [EMAIL="snaps@canonical.com"]snaps@canonical.com[/EMAIL]
license:   unset
description: |
  Canonical Livepatch Client
commands:
  - canonical-livepatch
services:
  canonical-livepatch.canonical-livepatchd: simple, enabled, active
snap-id:      b96UJ4vttpNhpbaCWctVzfduQcPwQ5wn
tracking:     latest/stable
refresh-date: 2020-03-24
channels:
  latest/stable:    9.5.5 2020-03-16 (95) 9MB -
  latest/candidate: &#8593;                         
  latest/beta:      &#8593;                         
  latest/edge:      9.5.5 2020-03-16 (95) 9MB -
installed:          9.5.5            (95) 9MB -

```

```

myuser@mysystem:~$ canonical-livepatch status
last check: 3 days ago
kernel: 5.4.0-48.52-generic
server check-in: failed: livepatch check failed: cannot send request: Put [https://livepatch.canonical.com/api/machine/cfffab30804144419daed292836eaa10:](https://livepatch.canonical.com/api/machine/cfffab30804144419daed292836eaa10:) dial tcp: lookup livepatch.canonical.com: no such host
patch state: &#10003; no livepatches needed for this kernel yet

```

```

myuser@mysystem:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

```

```

myuser@mysystem:~$ uname -a
Linux mysystem 5.4.0-48-generic #52-Ubuntu SMP Thu Sep 10 10:58:49 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

Most recent output from `journalctl -u snap.canonical-livepatch.canonical-livepatchd`:
```
-- Reboot --
Sep 23 00:04:59 mysystem systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: starting client daemon version 9.5.5
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: starting svc "mitigation loop"
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: service "mitigation loop" started
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: starting svc "socket servers"
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: service "socket servers" started
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: starting svc "refresh loop"
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: service "refresh loop" started
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: client daemon started
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: Client.Check
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: Checking with livepatch service.
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: No payload available.
Sep 23 00:05:00 mysystem canonical-livepatch[1271]: during refresh: cannot check: livepatch check failed: cannot send request: Put https://livepatch.canonical.com/api/machine/cfffab30804144419daed29283>
Sep 23 12:54:42 mysystem canonical-livepatch[1271]: Client.Check
Sep 23 12:54:42 mysystem canonical-livepatch[1271]: error in livepatch check state: check-failed
Sep 23 12:54:42 mysystem canonical-livepatch[1271]: Checking with livepatch service.
Sep 23 12:54:42 mysystem canonical-livepatch[1271]: No payload available.
Sep 23 12:54:42 mysystem canonical-livepatch[1271]: during refresh: cannot check: livepatch check failed: cannot send request: Put https://livepatch.canonical.com/api/machine/cfffab30804144419daed29283>
Sep 23 12:55:57 mysystem canonical-livepatch[1271]: error in livepatch check state: check-failed
Sep 23 12:55:57 mysystem canonical-livepatch[1271]: error in livepatch check state: check-failed
Sep 23 12:55:57 mysystem canonical-livepatch[1271]: error in livepatch check state: check-failed
Sep 23 12:56:36 mysystem canonical-livepatch[1271]: error in livepatch check state: check-failed
Sep 23 12:59:55 mysystem canonical-livepatch[1271]: error in livepatch check state: check-failed

```

---

### Post by agvantibo on 2020-09-23
Check your network capabilities, and look at the hosts file. This may help.

---

### Post by ActionParsnip on 2020-09-23
If you run:
```

telnet livepatch.canonical.com 443

```
Do you get a connection OK?

---

### Post by timcassidy13 on 2020-09-29
Sorry for the delayed response.  Yes, I'm able to open a connection via telnet to livepatch.canonical.com over port 443.  There's nothing funky in my hosts file either.

---

