---
title: "Network Repository Package Cache"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by Aikon- on 2008-06-11
Hi everyone, I have a new problem now that I am running multiple machines with Ubuntu.

I have all repos enabled (i.e. updates, proposed, backports), as I have never really had a problem with them and I like being as up to date as possible without having to deviate from the repos.

This results in quite a few updates. Just the other day, I had 180MB of updates that needed to be downloaded and installed. This was fine when I had one computer, but now, each individual computer has to download almost all the same packages, and all of a sudden that update jumps to 360MB for two computers, 540MB for three, etc. etc.

Is there anyway that I can have a single package cache on my network that all computers poll? Here's an example of what I mean:

The first computer checks the cache, sees that the latest package versions aren't there, downloads the latest version and saves them in the cache then installs them.

A few hours later, the next computer goes to check the cache, sees that all the latest versions have already been downloaded, and just grabs those instead, leaving the total amount downloaded at 180MB for N computers, for 1 <= N <= infinity.

-Aikon.

---

### Post by Aikon- on 2008-06-26
Looks like I've found just what I'm looking for: *apt-proxy*

[http://www.linux.com/feature/139213](http://www.linux.com/feature/139213)

---

