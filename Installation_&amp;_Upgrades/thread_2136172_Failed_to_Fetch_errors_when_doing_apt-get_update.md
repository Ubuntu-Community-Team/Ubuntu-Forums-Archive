---
title: "Failed to Fetch errors when doing apt-get update"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by sreeve29 on 2013-04-16
I know this has been asked many times, but I've done a whole bunch of searches and nothing helps.

When I run "sudo apt-get update" a lot of the errors appear.
Here's a snippet:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Cannot initiate the connection to 8080:80 (0.0.31.144). - connect (22: Invalid argument)

I've attached the whole output from the command.


Yes, I'm behind a proxy server, but I know I can get out:
sreeve@pto:/etc/apt$ ping [www.cnn.com]("http://www.cnn.com")
PING cnn-56m.gslb.vgtf.net (157.166.248.11) 56(84) bytes of data.

I've tried a bunch of Ubuntu distros lately (11 and 12 server and desktop) and FWIW, this "Failed to fetch" error happens on both v12 (desktop and server) and on 11 server.
My 11 desktop doesn't have this problem at all.  They're all using the same proxy ip address.

Anyway I can "redo" the /etc/apt/sources.list file or the /etc/apt/apt.conf file [IMG]http://ubuntuforums.org/images/icons/icon5.png[/IMG]

---

