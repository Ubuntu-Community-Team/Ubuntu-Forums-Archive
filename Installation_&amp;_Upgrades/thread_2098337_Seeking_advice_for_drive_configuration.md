---
title: "Seeking advice for drive configuration"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by nainsurvolte on 2012-12-26
Good day,

I am in the process of beefing up my server in terms of capacity which is based on Ubuntu but will also be my media/home server.

My requirements are the following.
1) Have more than 1TB for TV recordings for my Mythtv server
2) Have about 1TB, redundant for family Photo & Video and the music library.
3) The rest would go to TV shows I recorded and compressed as well as my movie library that I digitized.

My problem is that I have 4x2TB ( 2x2TB WD EARS + 2x2TB WD EARX) . Without considering the fact that I have 4 physical drives, I was considering having 2x1TB for the Req. 2, and have 6TB for the rest (MythTV, Series and Films).

That would mean, from my limited knowledge of Ubuntu (Linux) that I would need to split 2 drive in 2 and group the rest together
ex:

sda [ sda1 1TB ][ sda2 1TB ]
sdb [ sdb1 1TB ][ sdb2 1TB ]
sdc [            sdc 2TB          ]
sdd [            sdd 2TB          ]

[ sda1 1TB ] + [ sdb1 1TB ] in Raid 1
[ sda2 1TB ] + [ sdb2 1TB ] + [            sdc 2TB          ] + [            sdd 2TB          ]

Is this solution pure fiction or possible? And even if it is possible, is there a better way? I am open to suggestions...

Thanks,

---

