---
title: "Duke mirror down?"
date: 2021-08-26
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-08-26
For some time I've used the Duke University Ubuntu Mirror.  I started because I have having trouble with US ubuntu servers performance. Those problems have been long resolved but I've never changed back. Starting Tuesday I'm getting errors updating from the Duke mirror. Is anyone aware of any problem with it? Other machines pointed at other mirrors or at ```
 /us.archive.ubuntu.com

``` work as expected.
```
# apt update
Get:1 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Err:2 http://archive.linux.duke.edu/ubuntu focal InRelease
  Could not connect to archive.linux.duke.edu:80 (152.3.72.12), connection timed out
Err:3 http://archive.linux.duke.edu/ubuntu focal-updates InRelease
  Unable to connect to archive.linux.duke.edu:http:
Err:4 http://archive.linux.duke.edu/ubuntu focal-security InRelease
  Unable to connect to archive.linux.duke.edu:http:
Fetched 114 kB in 30s (3,738 B/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
54 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Failed to fetch http://archive.linux.duke.edu/ubuntu/dists/focal/InRelease  Could not connect to archive.linux.duke.edu:80 (152.3.72.12), connection timed out
W: Failed to fetch http://archive.linux.duke.edu/ubuntu/dists/focal-updates/InRelease  Unable to connect to archive.linux.duke.edu:http:
W: Failed to fetch http://archive.linux.duke.edu/ubuntu/dists/focal-security/InRelease  Unable to connect to archive.linux.duke.edu:http:
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by TheFu on 2021-08-26
[http://archive.linux.duke.edu/ubuntu](http://archive.linux.duke.edu/ubuntu) seems to be working from here. I used **lynx**:
```

                                                                                                     Index of /ubuntu/
                                                            Index of /ubuntu/
     ___________________________________________________________________________________________________________________________

../
dists/                                             23-Apr-2021 11:26                   -
indices/                                           26-Aug-2021 16:12                   -
pool/                                              27-Feb-2010 06:30                   -
project/                                           28-Jun-2013 11:52                   -
ubuntu/                                            26-Aug-2021 16:18                   -
ls-lR.gz                                           26-Aug-2021 16:13            20957164
     ________________________________________________________________________________________________
```

---

### Post by Dennis N on 2021-08-26
I would try the "select best server" button. It will find the fastest connection that's available at the moment.

---

### Post by rsteinmetz70112 on 2021-08-26
Thanks, 

It's weird I can't get it at all, maybe a DNS problem?

```
This site can’t be reached
archive.linux.duke.edu took too long to respond.

Try:

Checking the connection
Checking the proxy and the firewall
ERR_CONNECTION_TIMED_OUT
```

I'll switch to another mirror.

---

### Post by rsteinmetz70112 on 2021-08-26
Switched to another mirror. I'll mark this solved.
Thanks again.
I now just need to check my other Ubuntu computers to see if they are using the Duke mirror.

---

