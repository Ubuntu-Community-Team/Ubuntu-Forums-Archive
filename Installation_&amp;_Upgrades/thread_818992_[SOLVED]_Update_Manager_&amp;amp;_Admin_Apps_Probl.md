---
title: "[SOLVED] Update Manager &amp;amp; Admin Apps Problems"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by PhilCash on 2008-06-04
G'day All,

Update Manager stalls.
Synaptics Update Manager won't start.
Running Hardy, upgraded from Gutsy when Gutsy was released. 
This problem wasn't there after the upgrade; then occurred sporadically; then settled in for the duration.

Having trolled the forums trying to resolve these problems, I've found that many people are having the same trouble. I've found the following worked and offer it to the community:

In trying several commands suggested elsewhere; sudo aptitude update, sudo aptitude upgrade, sudo apt-get install -f, and sudo apt-get clean; I noted a response: unable to resolve host 'hostname', indicating an authentication problem.

Another post suggested editing lines in the /etc/hosts file from
127.0.0.1 localhost
127.0.1.1 hostname.domain
to
127.0.0.1 localhost
127.0.1.1 hostname

I'm not an advocate of changing such things parrot fashion, but this change to the hosts file worked for me.
I'd be grateful if someone can post an explanation of what the problem is, why this resolved it, if it is the correct way to fix the problem or just a work around, and what the correct resolution should be.

Cheers,
Phil

---

### Post by zvacet on 2008-06-05
> I noted a response: unable to resolve host 'hostname', indicating an authentication problem.

You get this message because in  /etc/host hostname was wrong.You resolved problem by puting right hostname.I saw many posts with the same issue so I think this is Hardy related,and all you need to do is simply replace wrong hostname with right one.

---

### Post by PhilCash on 2008-06-05
G'day zvacet,

Thanks for confirming this as a reasonable resolution. 

I remain puzzled as to why the problem initially appeared intermittently (ending and restarting Update Manager a few times used to get it working), and then it ceased to work at all, but there you go.

Is there a "Common Problem Resolution" area where such things can be listed? It would save a great deal of forum searching, similar posts, and trial & error of proposed fixes if known resolutions to common problems were listed in one place.

Cheers.

---

### Post by zvacet on 2008-06-05
[https://launchpad.net/ubuntu/+bugs]("https://launchpad.net/ubuntu/+bugs")

---

