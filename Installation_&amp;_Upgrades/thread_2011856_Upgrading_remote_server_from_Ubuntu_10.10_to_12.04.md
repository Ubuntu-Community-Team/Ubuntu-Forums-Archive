---
title: "Upgrading remote server from Ubuntu 10.10 to 12.04"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by DavidBrown2012 on 2012-06-27
I have a remote (VPS) server running Ubuntu 10.10.

Until recently I have been developing the server-side code (for a client-server project) on a local system running Ubuntu 11.04 and deploying it to the remote server, where it has run as a daemon for longish periods of time without any apparent problems.

I recently moved to a new development server running Ubuntu 12.04 LTS. Now I find the server program terminates almost as soon as it has started, and for no obvious reason - i.e. no errors in syslog or debugging information etc.

Eventually it dawned on me that the problem is probably caused by differences between the libraries used in 12.04 and 10.0, and that I need to upgrade the server. I'd be grateful for any comments on whether that seems like a feasible explanation. and for some advice on how best to go about upgrading the server. As it's a remote system it could cause me a lot of hassle if it goes wrong!

Many thanks!

---

