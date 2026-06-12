---
title: "can't connect to archives, tried several!"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by Joespower on 2007-05-03
Hey all, 

I'm using Dapper server (LAMP install) to test out some web apps.  For some time, I was able to run aqpt-get update/upgrade and everything went fine.  Recently, I've started having trouble connecting to the archives at all.  when I run the update command, it resolves the address of us.archive.ubuntu.com (91.189.89.8) correctly and tries to connect.  Eventually I will get a connection timed out error.  I can ping that server, and If I try to change to other archives (have tried ca, uk, gb) I get that same behavior.  I'm using sudo!  I have read that others are having trouble, and that the servers have had some issues recently, but others seem to fix this problem by switching to other archives.  That doesn't work for me!!  Here's what I get from aptitude...

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.89.8), connection timed out

Any help is appreciated!

---

### Post by Joespower on 2007-05-03
Seriously, I'm stumped here people.  This was working like a week or so ago, and then it just up and quit.  What gives?

---

### Post by dberg on 2007-05-05
I am having a similar problem. Solution?

---

