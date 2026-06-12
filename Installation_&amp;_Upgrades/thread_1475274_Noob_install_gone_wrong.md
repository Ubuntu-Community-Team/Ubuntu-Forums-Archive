---
title: "Noob install gone wrong?"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by tomj528 on 2010-05-06
Hello all.
I'm a total newbie and I'm trying to get Mythbuntu 10.04 to work on a new HTPC that I built.  First off even though it's confusing as heck to start with, I love Mythbuntu.  Anyway, as if trying a new OS wasn't hard enough I'm also using the Hauppauge 2250 tuner cards (2 of them for a total of 4 tuners).  I ran the instructions at [http://ubuntuforums.org/showthread/php?p=9230549](http://ubuntuforums.org/showthread/php?p=9230549) and I have actually gotten them to work! I recorded and replayed a show last night.   I'm just using OTA digital signals so I should be all set.  The only problem is that when I boot up and try to watch tv I get "error: Mythtv is using all inputs, but there are no active recordings?"  If I exit out into Ubuntu desktop and then go into myth backend setup and then exit out and restart the front end all of a sudden the watch tv works.  Of course it all reverts back when I reboot.  The play dvd feature is also intermittant as well.  I think that the frontend is having trouble connecting to the backend.  I've had the IP addresses set at 127.0.0.1 and then tried setting them to the actual IP address (192.168.10.9) and neither fixed the problem.  When I enter at the terminal mythbackend this is the result.

tom@mythtv:~$ mythbackend
2010-05-06 17:54:18.161 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-05-06 17:54:18.161 Using runtime prefix = /usr
2010-05-06 17:54:18.161 Using configuration directory = /home/tom/.mythtv
2010-05-06 17:54:18.161 Empty LocalHostName.
2010-05-06 17:54:18.161 Using localhost value of mythtv
2010-05-06 17:54:18.165 New DB connection, total: 1
2010-05-06 17:54:18.167 Connected to database 'mythconverg' at host: localhost
2010-05-06 17:54:18.167 Closing DB connection named 'DBManager0'
2010-05-06 17:54:18.167 Connected to database 'mythconverg' at host: localhost
2010-05-06 17:54:18.170 Current MythTV Schema Version (DBSchemaVer): 1254
2010-05-06 17:54:18.171 MythBackend: Starting up as the master server.
2010-05-06 17:54:18.173 New DB connection, total: 2
2010-05-06 17:54:18.174 Connected to database 'mythconverg' at host: localhost
2010-05-06 17:54:18.467 New DB connection, total: 3
2010-05-06 17:54:18.468 Connected to database 'mythconverg' at host: localhost
2010-05-06 17:54:19.560 New DB scheduler connection
2010-05-06 17:54:19.560 Connected to database 'mythconverg' at host: localhost
2010-05-06 17:54:19.570 MediaServer::HttpServer Create Error
2010-05-06 17:54:19.571 Enabled verbose msgs:  important general
2010-05-06 17:54:19.573 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-05-06 17:54:19.575 Failed to bind port 6543. Exiting.
2010-05-06 17:54:19.575 Backend exiting, MainServer initialization error.
tom@mythtv:~$ 

So it looks like its having trouble connecting.

The rest of my setup:
MB Gigabyte GA-890GPA-UD3H
CPU AMD PHII 945 3.0G quad core
RAM 2x2g ADATA DDR3 1600
Asus DVD-R Burner
Gigabyte GV-NX84S512HP Graphics card with Svideo output to old tube tv for now.
 
Any help would be greatly appreciated.

Thank you

---

