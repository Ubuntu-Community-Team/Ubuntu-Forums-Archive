---
title: "do-release-upgrade not available for LTS (22.04 --&gt; 24.04)"
date: 2024-09-04
forum: Installation &amp; Upgrades
---

### Post by tomho on 2024-09-04
Hello,
I prepared to upgrade our ubuntu servers. Yesterday (3rd of Sep.), the upgrade was offered.
When I try to upgrade today, I receive the message that LTS update is not possible.
When I run "do-release-upgrade -c" I get the following message:

*user@server:~# do-release-upgrade -c*
*Checking for a new Ubuntu release*
*There is no development version of an LTS available.*
*To upgrade to the latest non-LTS development release*
*set Prompt=normal in /etc/update-manager/release-upgrades.*

LTS version 22.04 is currently installed and in the file .../release-upgrades there is also LTS configured.
Was the upgrade disabled or postponed?

Maybe someone could verify. Thanks!

---

### Post by boggin4fun on 2024-09-04
I fit the criteria of Someone and I can also verify this issue.  I upgraded two test servers almost a week ago using do-release-upgrade and following the instructions in the [documentation]("https://documentation.ubuntu.com/server/how-to/software/upgrade-your-release/").  I just now went to execute the procedure on my final test server and, to my surprise, discovered it is not available today.  I am in the same boat as you.  No idea if something was recently pulled or what changed, but I know it was not the procedure I followed when I upgraded the other two servers.  I'd be happy to hear if anyone else has this same issue.

Thanks

P.S. Post edited to fix a typo.

---

### Post by michaelpayne02 on 2024-09-04
[https://askubuntu.com/a/1525649/1153063](https://askubuntu.com/a/1525649/1153063)

---

### Post by tomho on 2024-09-05
Thanks for the information!
Maybe Canonical stopped the rollout on purpose. Unfortunately, I couldn't  find any official statement.
The link [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts) shows at least, that 24.04 is missing.

---

### Post by tomho on 2024-09-05
I found a filed bug ticket now at [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2078895](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2078895)

---

### Post by Bashing-om on 2024-09-05
tomho - Yup

Rollout on pause:
<https://lists.ubuntu.com/archives/ubuntu-release/2024-September/006225.html>

-these things happen-

---

