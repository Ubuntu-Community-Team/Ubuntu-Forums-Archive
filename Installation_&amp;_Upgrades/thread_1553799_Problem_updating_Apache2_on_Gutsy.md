---
title: "Problem updating Apache2 on Gutsy"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by marke1 on 2010-08-15
I'm running Gutsy - I can't apply the latest Apache2 updates - all other updates are installed already. 

When I try to update apache2-mpm-prefork then apt complains that apache2.2-common is the wrong version (says it's 2.2.4-3ubuntu0.1) and that I need to have 2.2.4-3ubuntu0.2 - but it won't install, dpkg complains about dependencies, so I wind up having 3 packages that won't update: apache2-mpm-prefork, apache2.2-common, and apache2-prefork-dev

First I tried apt-get install apache2-mpm-prefork -- it fails due to the version issue mentioned above. 

Then I tried apt-get -f install -- still won't install

I tried dpkg --configure -a -D400 (last parm gives debug into) -- here's the  result: 
-------------
dpkg --configure -a -D400
D000400:   checking group ...
D000400:     checking possibility  -> apache2.2-common
D000400:       bad version, returning 0
D000400:     found 0
D000400:   found 0 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> openssl
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
D000400:   checking group ...
D000400:     checking possibility  -> libaprutil1-dev
D000400:       is installed, ok and found
D000400:     found 3
D000400:   found 3 matched 0 possfixbytrig -
dpkg: dependency problems prevent configuration of apache2-prefork-dev:
 apache2-prefork-dev depends on apache2.2-common (= 2.2.4-3ubuntu0.2); however:
  Version of apache2.2-common on system is 2.2.4-3ubuntu0.1.
dpkg: error processing apache2-prefork-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2-prefork-dev
-------------

If I try to install the updated apache2.2-common, then apt wants to also install the updated apache2-mpm-prefork, which is fine with me, BUT, the install fails for the same reason (wrong apache2.2-common version). 

Anybody know how can I fix this? 

Mark

---

### Post by marke1 on 2010-08-15
aptitude is saying: 

apache2-prefork-dev depends on apache2.2-common (= 2.2.4-3ubuntu0.2)
apache2-mpm-preform depends on apache2.2-common (= 2.2.4-3ubuntu0.2)

So I manually install the apache2.2-common package using dpkg -i because it wouldn't install using apt. 

Now apache2-prefork-dev updates properly. No problem with that anymore.

BUT, no2 aptitude is saying that apache2-mpm-prefork depends on apache2.2-common (= 2.2.4-3ubuntu0.1) -- First it say it depends on 2.2.4-3ubuntu0.2 and now it says it depends on 2.2.4-3ubuntu0.1? 

What's up with that?

---

### Post by jrothwell97 on 2010-08-15
Support for Gutsy ended in April 2009. You should consider upgrading to Hardy or Lucid.

---

### Post by marke1 on 2010-08-15
> **jrothwell97 said:**
> Support for Gutsy ended in April 2009. You should consider upgrading to Hardy or Lucid.

That's the idea..........

Does that involve simply changing "gusty" to "hardy" in sources.list and then apt-get update and apt-get upgrade? 

Or is there more to it?

---

### Post by jrothwell97 on 2010-08-15
> **marke1 said:**
> That's the idea..........

Does that involve simply changing "gusty" to "hardy" in sources.list and then apt-get update and apt-get upgrade? 

Or is there more to it.

Theoretically, yes.

In practice, no. You should really have gone via Update Manager, since that's the most hassle-free way of upgrading between releases.

However, try running

```
sudo do-release-upgrade
```

and hope that works - although I'm not knowledgeable enough about its behaviour to be sure whether you'll end up on Hardy, Intrepid or Lucid :oops:

Failing that, I strongly recommend a clean installation. Use the live CD to back up your existing data, and wipe it clean. (This has the added advantage of giving you Grub 2, ext4 and other improved technologies out of the box.)

---

### Post by marke1 on 2010-08-15
> **jrothwell97 said:**
> Theoretically, yes.
In practice, no. You should really have gone via Update Manager, since that's the most hassle-free way of upgrading between releases.


This is a server run via command line only. There is no GUI installed. 

> 
However, try running
```
sudo do-release-upgrade
```
 

We might do that. [Correction: do-release-upgrade does not exist in this server]

> 
Failing that, I strongly recommend a clean installation. 



That's the extreme easy way, the most time consuming, the most troublesome with large file systems -- and it just ain't gonna happen :-) The system is a very high traffic live Web server (millions of pages served every month).


What I'd really like to know is why the packages are broken. I unpacked the apache2-mpm-prefork deb file and it clearly says it depends on apache2.2-common = 2.2.4-3ubuntu0.2 - which is installed already. But, when I try to install apache2-mpm-prefork via apt, it claims to want 2.2.4-3ubuntu0.1. And if I try to manually install the deb file it doesn't install.

Something is definitely wrong. I'm thinking that somehow apt lost track of its versioning somewhere.

---

### Post by marke1 on 2010-08-15
So as it turns out, we had a customized /etc/init.d/apache2 script and it didn't exactly exit the way dpkg would expect. SO - that is what was preventing the upgrade process from running correctly because dpkg first stops apache2 and looks for a specific result.

---

