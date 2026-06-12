---
title: "synaptic and add/remove not working - feisty"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by donewithms on 2007-10-11
I installed Google earth for Linux the other day.  It worked once perfectly and then would not connect to their server.  Now my synaptic and add/remove programs won't work.  I am not sure Google earth caused the problem but I highly suspect it.  This is the error I get when I try to install or update:

(This is specifically for the Monopoly type game 'Atlantic' but the same basic message appears for any install or upgrade I try)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/atlantik_3.5.6-0ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegames/atlantik_3.5.6-0ubuntu2_i386.deb)
  Could not connect to localhost:4001 (XXX.X.X.X). - connect (111 Connection refused)

I replaced the I.P. #s with Xs.

I can get online fine and all my programs (except Google earth) seem to be working.  I have a second computer and it will update correctly.  I am using a router but have never had to change any setting for Ubuntu and computer #2 is working right.

I really don't want to reinstall because I have to wrestle with my music programs every time and it is a major headache.  

Could this be a permissions issue?  I had to give the Google earth .bin file permission to execute.  It was the first time I had to do that.  Is that causing a security problem?

---

### Post by wpshooter on 2007-10-12
Sounds like to me that something has messed up the information in your source listing.

Have you tried to open Synaptic and hit the "reload" button, let that finish and then reboot your system ?

---

