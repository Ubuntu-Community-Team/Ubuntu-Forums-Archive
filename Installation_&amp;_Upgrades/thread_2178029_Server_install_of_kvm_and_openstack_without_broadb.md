---
title: "Server install of kvm and openstack without broadband"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by K7AAY on 2013-10-01
Here is an unusual question.

I've always installed Ubuntu desktop (many versions and flavors) with a decent internet connection, but now I find myself preparing for my first-ever server (13.04) installation, in a place without broadband. I therefore wish to prepare for installing everything from media, which I would download before I wander off to the Boonies. 

How can I download all the files I would need for a complete Open Stack install, on a single machine, before I leave the blue blanket of my broadband connection?

Thank you kindly.

---

### Post by TheFu on 2013-10-01
1 - for a seldom connected server installation, you want 12.04 LTS, not the flavor of the day release.
2 - Grab the server DVD
3 - openstack on a single machine isn't very useful. It isn't worth the hassle. You might want to check out devstack instead.

Of course, you know your real requirements and perhaps you have new hardware that isn't supported by 12.04 and there are 1,000 physical machines in the dis-connected network where you will be working, so openstack stuff is what you need.

I am doubtful that you can take everything you need unless you setup everything when connected to the internet first, then migrate that to the new location.  apt-cache-ng would be my recommendation **after** grabbing the DVD release you plan to install.  I'd probably mirror every related project on github, sourceforge and bitbucket for openstack and all the components too. Don't forget openvswitch and lots of documentation too.

---

### Post by K7AAY on 2013-10-01
Need to practice this stuff for a behind-firewall install next week which will not permit connection to repositories.

Cx wants 13.04, cx is always right, been around and around on the issue of LTS but they want Grizzly Open Stack which requires 13.04 of which they are convinced. 

Set up a local mirror, problem solved.

"You can't always git what u wa-a-ant", but thank you.

And, I like yer .sig - you ever get to Puddletown, make sure to visit a Buster's BBQ, better than Sonny's.

---

