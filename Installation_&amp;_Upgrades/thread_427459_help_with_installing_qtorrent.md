---
title: "help with installing qtorrent"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by zerobinary on 2007-04-29
the qtorrent i download from graveyard is different from the one i get on synaptic package manager
i got error like this when i try to run it
root@zerobinary:/home/zerobinary/Desktop/qtorrent-0.9.5# qtorrent
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/bin/qtorrent", line 15, in <module>
    w = TorrentWindow()
  File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentmain.py", line 383, in __init__
    torrentwindow.TorrentWindow.__init__(self, parent)
  File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentwindow.py", line 55, in __init__
    self.setSizePolicy(QSizePolicy(3,3,0,0,self.sizePolicy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type
root@zerobinary:/home/zerobinary/Desktop/qtorrent-0.9.5# qtorrent
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/bin/qtorrent", line 15, in <module>
    w = TorrentWindow()
  File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentmain.py", line 383, in __init__
    torrentwindow.TorrentWindow.__init__(self, parent)
  File "/usr/lib/python2.5/site-packages/pyqtorrent/torrentwindow.py", line 55, in __init__
    self.setSizePolicy(QSizePolicy(3,3,0,0,self.sizePolicy().hasHeightForWidth()))
TypeError: argument 1 of QSizePolicy() has an invalid type

---

