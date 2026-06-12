---
title: "Recovering from ssh disconnect"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by echalmer on 2008-05-17
I upgraded 7.04 server to 7.10 using do-release-upgrade over ssh with no problems. I know this is not recommended.

I then started 7.10 server to 8.04 the same way. I foolishly allowed the ssh connection to drop during the process. It was doing the big download. I guess it's stuck now waiting for me to answer a question on the console I can't recover. (I can still ssh). I could see the console for a while using "who", but it is gone now.

Any suggestions on how best to recover from here?

---

### Post by echalmer on 2008-05-17
It wasn't so hard.

/etc/apt/sources.list entries were all updated to hardy. So I just used apt to upgrade (just applied changes, the downloads were done) and dist-upgrade. All looks fine after that I think:

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy

$ uname -a
Linux [email]server@example.com[/email] 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

---

