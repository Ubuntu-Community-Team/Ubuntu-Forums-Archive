---
title: "samba error in 11.04"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2011-07-23
after upgraded to 11.04, I am getting error msg that samba is not installed.

any ideas?

Tired to install samba results in:

>
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: Fehler beim Bearbeiten von samba4 (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 samba4
<

---

