---
title: "Problem with bittorrent snakebite software"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by dabsan on 2006-09-02
I am getting this error message when trying to start snakebite in Terminal? Does anyone please have any ideas to fix this problem?
Many Thanks .......
 
darren@darren-desktop:~$ sudo /etc/init.d/snakebite start
Password:
 * Starting Snakebite...                                                 [ ok ]
darren@darren-desktop:~$ Traceback (most recent call last):
  File "/usr/bin/snakebite", line 145, in ?
    sb.webServer()
  File "/usr/bin/snakebite", line 86, in webServer
    ws = WebServer(self.conpar.dir_torrents, self.conpar.dir_web, self.conpar.dir_temp, self.conpar.username, self.r)
  File "/usr/lib/python2.4/site-packages/snakebite/server.py", line 21, in __init__
    s = self.r.create_serversocket(6060, '', True)
  File "/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twisted.py", line 762, in create_serversocket
    raise e.socketError
error: (98, 'Address already in use')

---

