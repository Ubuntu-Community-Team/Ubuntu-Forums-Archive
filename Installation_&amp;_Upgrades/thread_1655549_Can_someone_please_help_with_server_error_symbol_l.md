---
title: "Can someone please help with server error symbol lookup error:?"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by marek.neo on 2010-12-29
The sourceslistu I entered the new resources and upgrade my mysql-server is not running, or postfix, or can not run another update, and so on. Some services like ssh and apache is running. when trying to update lists:

 : ~ # aptitude update
 aptitude: symbol lookup error: / usr / lib / libstdc + +. so.6: undefined symbol: _ZNSt7num_getIcSt19istreambuf_iteratorIcSt11char_traitsIcEEE2idE, version GLIBCXX_3.4

 when trying to start MySQL:

 : ~ # / etc / init.d / mysql start
 Rather Than through invoking the init scripts / etc / init.d, use the service (your eyes roll back! Super!
 utilities, e.g. service mysql start

 Since the script you are attempting to invoke Has been converted to an
 Upstart Jobs ook May you use the start (roll back eyes! Super! utilities, eg start mysql
 Start: Job failed to start


 It did not please anyone of you experienced this?

 Very thanks. Mark


This is on Ubuntu Server 9.10 and sourceslist is Maverick. Thanks so much for any advice, I do not know the Board

 Thanks

---

