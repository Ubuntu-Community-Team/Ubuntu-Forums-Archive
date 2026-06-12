---
title: "Aptitude could not connect to us.archive.ubuntu.com"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by bbicknell on 2009-11-13
I've installed many packages using aptitude already over the last month (my sysadmin gave me an installation practically bereft of any tools). About a week or two weeks ago, aptitude stopped installing and started timing out whenever I tried to install anything.

These errors are typical:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main cron 3.0pl1-105ubuntu1.1
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.135), connection timed out [IP: 91.189.88.135 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main cron 3.0pl1-105ubuntu1.1
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cron/cron_3.0pl1-105ubuntu1.1_amd64.deb:](http://security.ubuntu.com/ubuntu/pool/main/c/cron/cron_3.0pl1-105ubuntu1.1_amd64.deb:) Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

I've seen many different addresses for us.archive.ubuntu.com, but they all time out. I can ping the servers and connect with telnet to port 80. I can't wget 'cuz that is not installed.

Although I know it was possibly dangerous, given that I've been using aptitude exclusively, I couldn't connect with apt-get either.

I have seen suggestions that the slow responses are due to the 9.10 release. But this has been going on for two weeks, and it isn't a slow response, it's a time out.

I've tried updating sources.list tried two different mirrors and got a message that the package I'm really trying to install, cron, could not be found.

---

### Post by earthpigg on 2009-11-13
hi,

have you tried letting ubuntu test ***all*** it's mirrors and picking the best one from your location?

system -> admin -> software sources -> download from -> other -> select best server -> let it test them all and suggest the best

---

### Post by audiomick on 2009-11-13
Hi. I saw a couple of other posts in the last couple of days relating to this. I think that server has a problem. Do what earthpigg says

---

### Post by bbicknell on 2009-11-13
Is there a command-line equivalent of what you suggest? This box is a server; there's no desktop or X installed on it. I don't see anything similar in the GUI form of Aptitude.

---

### Post by earthpigg on 2009-11-13
> **bbicknell said:**
> Is there a command-line equivalent of what you suggest? This box is a server; there's no desktop or X installed on it. I don't see anything similar in the GUI form of Aptitude.

got another ubuntu box plugged into the same router at the same location as that one?

run the test on that one, then edit the sources.list on the server to use whatever mirror the desktop/laptop/netbook system finds is the fastest.

or... the ultra nerdy way:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

wget the page source, grep that into a text file, and pipe it into a script that each pings 2 or 3 times and returns the fastest. extra points if the script includes ASCII art.

---

