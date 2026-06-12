---
title: "do release upgrade 11.10 to 12.04.4 LTS"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by kgordon-0 on 2014-06-05
#do-release-upgrade --check-dist-upgrade-only          confirmed 12.04.4
tried:
[EMAIL="root@kgwebsite:/"]root@kgwebsite:/[/EMAIL]# do-release-upgrade
Checking for a new ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)
Err Upgrade tool signature
  Connection failed
Get:1 Upgrade tool [5612 kB]
Fetched 5612 kB in 0s (0 B/s)
WARNING:root:file 'precise.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.


Could someone please explain for me the above. Is it hopeless? I believe my network is ok.
Thank you. Kevin

---

### Post by fantab on 2014-06-06
That won't work as easy 'coz 11.10 is dead (end-of-life).
[https://help.ubuntu.com/community/EOLUpgrades ]("https://help.ubuntu.com/community/EOLUpgrades")

Preferably do a 'fresh and clean' install of any latest version. Its just that 'fresh and clean'.
EOL upgrades may work, may not work, and even if they work you may end up doing a lot of tweaking later.

If you have DATA to BACKUP then do so right now.

---

