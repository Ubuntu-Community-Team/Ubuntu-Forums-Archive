---
title: "Upgrading from 17.04 to 17.10"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by jwinterton68 on 2018-10-08
I have inherited a v17.04 server which I'd like to upgrade to a supported version. I'd prefer not to do a clean install of 18.04 as there is quite a bit to configure (mail server, web server, various services) and I need to minimise downtime. An incremental upgrade to 17.10 and then to 18.04 seems to be the simplest path. However do-release-upgrade only wants to upgrade to 18.04 which then fails as "An upgrade from 'zesty' to 'bionic' is not supported with this tool."  Well fair enough but I don't want to upgrade to bionic yet. How do I get it to upgrade to 17.10 (artful)?

---

### Post by oldos2er on 2018-10-08
Since 17.10 is no longer supported, you'll need to do an [EOL upgrade]("https://help.ubuntu.com/community/EOLUpgrades"). It's a good idea to backup any sensitive data before proceeding.

---

### Post by jwinterton68 on 2018-10-09
Hi oldos2er, thanks for the reply. The "EOL Upgrade" is the process that I have tried but this results in an upgrade to 18.04 which fails as described above.
Aha OK so I see part of the problem 17.10 (artful) is not actually listed on old-releases. Perhaps I should not have re-directed my sources.list. artful is still available under archive.ubuntu.com.
So zesty is in old-releases and artful is in archive. Is this why I can't automatically upgrade from one to the other?

---

### Post by oldos2er on 2018-10-09
Sounds like a good possibility, but at this point you know more than I do.

In the future best to upgrade before a version goes EOL--fewer headaches that way.   :)

---

