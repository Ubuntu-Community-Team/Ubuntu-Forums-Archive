---
title: "Upgrade to 15.04 and now mongod won't start! SOLVED!"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2015-04-26
[FONT=Helvetica Neue][TABLE]
[TR]
[TD="class: postcell"][B]I made the mistake yesterday of upgrading to 15.04 :-).
[/B] Now my mongod can't start:

MongoDB shell version: 2.6.9
connecting to: test
2015-04-26T08:45:08.339-0600 warning: Failed to connect to 127.0.0.1:27017, reason: errno:111 Connection refused
2015-04-26T08:45:08.339-0600 Error: couldn't connect to server 127.0.0.1:27017 (127.0.0.1), connection attempt failed at src/mongo/shell/mongo.js:146
exception: connect failed

So I tried:
sudo service mongod status
which results in:[INDENT]&#9679; mongod.service
   Loaded: not-found (Reason: No such file or directory)
   Active: inactive (dead) [/INDENT]

So next, I searched for the lock file related to mongodb and removed it.
This too was no help. 

So next I tried:

sudo -u mongodb mongod --repair --dbpath /var/lib/mongodb/
sudo service mongodb start

Which results with:[INDENT]sudo -u mongodb mongod --repair --dbpath /var/lib/mongodb/
2015-04-26T08:56:39.844-0600 [initandlisten] MongoDB starting : pid=17760 port=27017 dbpath=/var/lib/mongodb/ 64-bit host=Parke.dynu.com
2015-04-26T08:56:39.844-0600 [initandlisten] db version v2.6.9
2015-04-26T08:56:39.844-0600 [initandlisten] git version: df313bc75aa94d192330cb92756fc486ea604e64
2015-04-26T08:56:39.844-0600 [initandlisten] build info: Linux build20.nj1.10gen.cc 2.6.32-431.3.1.el6.x86_64 #1 SMP Fri Jan 3 21:39:27 UTC 2014 x86_64 BOOST_LIB_VERSION=1_49
2015-04-26T08:56:39.844-0600 [initandlisten] allocator: tcmalloc
2015-04-26T08:56:39.844-0600 [initandlisten] options: { repair: true, storage: { dbPath: "/var/lib/mongodb/" } }
2015-04-26T08:56:39.860-0600 [initandlisten] repairDatabase tracker
2015-04-26T08:56:39.860-0600 [initandlisten] allocating new ns file /var/lib/mongodb/_tmp_repairDatabase_0/tracker.ns, filling with zeroes...
2015-04-26T08:56:39.906-0600 [FileAllocator] allocating new datafile /var/lib/mongodb/_tmp_repairDatabase_0/tracker.0, filling with zeroes...
2015-04-26T08:56:39.907-0600 [FileAllocator] creating directory /var/lib/mongodb/_tmp_repairDatabase_0/_tmp
2015-04-26T08:56:39.908-0600 [FileAllocator] done allocating datafile /var/lib/mongodb/_tmp_repairDatabase_0/tracker.0, size: 64MB,  took 0 secs
2015-04-26T08:56:39.942-0600 [initandlisten] repairDatabase tracker-test
2015-04-26T08:56:39.942-0600 [initandlisten] allocating new ns file /var/lib/mongodb/_tmp_repairDatabase_0/tracker-test.ns, filling with zeroes...
2015-04-26T08:56:39.987-0600 [FileAllocator] allocating new datafile /var/lib/mongodb/_tmp_repairDatabase_0/tracker-test.0, filling with zeroes...
2015-04-26T08:56:39.988-0600 [FileAllocator] creating directory /var/lib/mongodb/_tmp_repairDatabase_0/_tmp
2015-04-26T08:56:39.990-0600 [FileAllocator] done allocating datafile /var/lib/mongodb/_tmp_repairDatabase_0/tracker-test.0, size: 64MB,  took 0.001 secs
2015-04-26T08:56:40.020-0600 [initandlisten] repairDatabase test
2015-04-26T08:56:40.020-0600 [initandlisten] allocating new ns file /var/lib/mongodb/_tmp_repairDatabase_0/test.ns, filling with zeroes...
2015-04-26T08:56:40.065-0600 [FileAllocator] allocating new datafile /var/lib/mongodb/_tmp_repairDatabase_0/test.0, filling with zeroes...
2015-04-26T08:56:40.065-0600 [FileAllocator] creating directory /var/lib/mongodb/_tmp_repairDatabase_0/_tmp
2015-04-26T08:56:40.067-0600 [FileAllocator] done allocating datafile /var/lib/mongodb/_tmp_repairDatabase_0/test.0, size: 64MB,  took 0.001 secs
2015-04-26T08:56:40.078-0600 [initandlisten] repairDatabase admin
2015-04-26T08:56:40.078-0600 [initandlisten] allocating new ns file /var/lib/mongodb/_tmp_repairDatabase_0/admin.ns, filling with zeroes...
2015-04-26T08:56:40.123-0600 [FileAllocator] allocating new datafile /var/lib/mongodb/_tmp_repairDatabase_0/admin.0, filling with zeroes...
2015-04-26T08:56:40.123-0600 [FileAllocator] creating directory /var/lib/mongodb/_tmp_repairDatabase_0/_tmp
2015-04-26T08:56:40.125-0600 [FileAllocator] done allocating datafile /var/lib/mongodb/_tmp_repairDatabase_0/admin.0, size: 64MB,  took 0.001 secs
2015-04-26T08:56:40.148-0600 [initandlisten] repairDatabase tracker-dev
2015-04-26T08:56:40.148-0600 [initandlisten] allocating new ns file /var/lib/mongodb/_tmp_repairDatabase_0/tracker-dev.ns, filling with zeroes...
2015-04-26T08:56:40.195-0600 [FileAllocator] allocating new datafile /var/lib/mongodb/_tmp_repairDatabase_0/tracker-dev.0, filling with zeroes...
2015-04-26T08:56:40.195-0600 [FileAllocator] creating directory /var/lib/mongodb/_tmp_repairDatabase_0/_tmp
2015-04-26T08:56:40.197-0600 [FileAllocator] done allocating datafile /var/lib/mongodb/_tmp_repairDatabase_0/tracker-dev.0, size: 64MB,  took 0.001 secs
2015-04-26T08:56:40.238-0600 [initandlisten] repairDatabase local
2015-04-26T08:56:40.238-0600 [initandlisten] allocating new ns file /var/lib/mongodb/_tmp_repairDatabase_0/local.ns, filling with zeroes...
2015-04-26T08:56:40.285-0600 [FileAllocator] allocating new datafile /var/lib/mongodb/_tmp_repairDatabase_0/local.0, filling with zeroes...
2015-04-26T08:56:40.285-0600 [FileAllocator] creating directory /var/lib/mongodb/_tmp_repairDatabase_0/_tmp
2015-04-26T08:56:40.288-0600 [FileAllocator] done allocating datafile /var/lib/mongodb/_tmp_repairDatabase_0/local.0, size: 64MB,  took 0.001 secs
2015-04-26T08:56:40.300-0600 [initandlisten] finished checking dbs
2015-04-26T08:56:40.300-0600 [initandlisten] dbexit: 
2015-04-26T08:56:40.300-0600 [initandlisten] shutdown: going to close listening sockets...
2015-04-26T08:56:40.300-0600 [initandlisten] shutdown: going to flush diaglog...
2015-04-26T08:56:40.300-0600 [initandlisten] shutdown: going to close sockets...
2015-04-26T08:56:40.300-0600 [initandlisten] shutdown: waiting for fs preallocator...
2015-04-26T08:56:40.300-0600 [initandlisten] shutdown: closing all files...
2015-04-26T08:56:40.300-0600 [initandlisten] closeAllFiles() finished
2015-04-26T08:56:40.300-0600 [initandlisten] shutdown: removing fs lock...
2015-04-26T08:56:40.300-0600 [initandlisten] dbexit: really exiting now
joel@Parke:/var/lib/mongodb

[/INDENT]
So finally, I tried again:
sudo service mongodb start
Which results in:[INDENT]Failed to start mongodb.service: Unit mongodb.service failed to load: No such file or directory.[/INDENT]

Still no help. 
So next I created a /data/db directory in the hopes that this might work.
But this was no help. 

So any ideas? I assume this is related to the move away from upstart?

Is there an easy way to downgrade?
 Or do I just need to restore my saved files?
It's sad because everything else looks GREAT!

Thanks...[/TD]
[/TR]
[TR]
[TD="class: votecell"][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[/FONT][FONT=Helvetica Neue]

[/FONT]

---

### Post by ruidc on 2015-04-27
did you try daemon-reload before starting? also check that your conf file points to the right data directory.

---

### Post by JoelParke on 2015-04-27
The data path is correct and exists with the right permissions, etc.
sudo service mongod reload
gives:
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mongod reload
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused

which is interesting...

---

### Post by JoelParke on 2015-04-27
[FONT=Helvetica Neue]For others that run across this - what a pain! It turns out that Mongo>2.6.3 has a known issue with start: Support Systemd (cannot start mongodb with init scripts with Fedora 15 or above) As noted here: [https://jira.mongodb.org/browse/SERVER-17742](https://jira.mongodb.org/browse/SERVER-17742) and it seems that this possibly won't be fully fixed for >2.6.3 until Ubuntu 16.04, unless there is a strong outcry.[/FONT]
[FONT=Helvetica Neue]So the solution for me was to issue:[/FONT]
**sudo apt-get install --reinstall mongodb**
[FONT=Helvetica Neue]This reverted back to mongo 2.6.3 and NOW ALL WORKS! For those that run across this... Thanks to all who looked at this![/FONT]

---

