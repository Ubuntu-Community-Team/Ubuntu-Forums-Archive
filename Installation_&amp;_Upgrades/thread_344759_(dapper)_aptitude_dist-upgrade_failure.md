---
title: "(dapper) aptitude dist-upgrade: failure"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by ender42 on 2007-01-23
So, I'm using aptitude instead of apt-get, since it suppossedly handles dependencies better.

Have upgraded from Hoary, thru Breezy to Dapper.  But, upon atarting to play with Dapper, it said: updates available.

So, did the ```
aptitude update
```, then did the ```
aptitude dist-upgrade
```.  It wanted to kill something, so I said, fine, then it failed.  I tried removing *deb from /var/cache/apt/archives (maybe there was a space issue on / - I was at 97ish%), and tried it again, I get this failure:

```

Fetched 176MB in 31m27s (93.5kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 93193 files and directories currently installed.)
Preparing to replace lvm2 2.00.32-1 (using .../lvm2_2.02.02-1ubuntu1.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lvm2_2.02.02-1ubuntu1.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
root@machine:/var/cache/apt/archives #
root@machine:/var/cache/apt/archives # df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              9612604   8413856    710452  93% /

```
...

But I should have enough space right now...

Any ideas?

Yes, I did leave terminals, gaim, and ssh open...

Sucks that <code> doesn't work.  Sorry that I was cut-n-pasting from email :)

---

### Post by taurus on 2007-01-23
```
df -h
```
Or
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ender42 on 2007-01-28
Did those, and that doesn't help :)

---

### Post by taurus on 2007-01-28
```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ender42 on 2007-01-28
That appears to have worked.  It didn't hang this time, and default out with an error message.

Got some random errors in the mix, but maybe I can take care of those myself.

Now, where'd you go to get that help?  Because I'd much rather find things to read and solve my own problems than bother people.

---

