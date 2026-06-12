---
title: "apt-get returning exit status 127 when trying to do upgrade"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by sohmc on 2012-01-04
When I tried to do a upgrade on all my packages, it aborted mid-way and got this error:
```
Setting up initscripts (2.88dsf-13.10ubuntu4.1) ...
/var/lib/dpkg/info/initscripts.postinst: 169: update-rc.d: not found
dpkg: error processing initscripts (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 initscripts
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've [searched on google](http://bit.ly/zRS8YC) and have gotten no relavant results.  The closest one I could find was an [old archive from 2008](http://ubuntuforums.org/archive/index.php/t-942225.html) but it did not help.

Now, if I try to install ANY package, I get the same error.  Is anyone else getting this error today?

---

### Post by 2F4U on 2012-01-04
From what version to what version do you attempt to upgrade or do you want do update your packages within a certain release, e.g. 11.10?

---

### Post by sohmc on 2012-01-04
Crap, I hate when this happens.  I find the solution after a few more minutes of tinkering with my google search.

In the hopes that someone else finds this thread, [here's the solution](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/"):

Find the offending package.  In my case, it was initscripts.  Then go to /var/lib/dpkg/info and delete all files associated with the package.  In my case, the command was: rm initscripts*

Then run: apt-get -f install initscripts

Once that's finished, you may want to install any other packages that were held back due to this problem: dpkg --configure --pending

---

### Post by matt_symes on 2012-01-04
Hi

Open a terminal and type these commands

```
which update-rc.d
``````
ls -l /usr/sbin/update-rc.d
```(That is a small L after ls)

```
echo $PATH
```(case is important)

Post back the results back here.

EDIT: I guess this post is redundant because you have found a fix.

Kind regards

---

