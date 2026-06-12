---
title: "Snake bite Problem"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by damian2007 on 2006-09-10
btr@btr-desktop:/etc/init.d$ Traceback (most recent call last):
  File "/usr/bin/snakebite", line 144, in ?
    sb.webServer()
  File "/usr/bin/snakebite", line 85, in webServer
    ws = WebServer(self.conpar.dir_torrents, self.conpar.dir_web, self.conpar.dir_temp, self.conpar.username, self.r)
  File "/usr/lib/python2.4/site-packages/snakebite/server.py", line 21, in __init__
    s = self.r.create_serversocket(6060, '', True)
  File "/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twisted.py", line 762, in create_serversocket
    raise e.socketError
error: (98, 'Address already in use')


Anyone an idea how to solve this  ?

THX

---

