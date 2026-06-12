---
title: "apache2 update breaks VirtualHosts"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by MC_Claus on 2008-02-11
Hi forum

First post here, so hopes its the right place :-)

The other day, like 2-3 days ago, i updated my Ubuntu, and one of the updates was to apache2. 
Now when I try to access one of my sites, all it displays is a directory listing and not the sites as I was hoping for!

Anyone else experienced this? And found a solution?

I have tried just restarting apache2 and got
```
[Sun Feb 10 07:37:02 2008] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

```
...3 times, one for each VirtualHost (except default). I then tried updating from 
```

<VirtualHost *:80>

```
to 
```

<VirtualHost *>

It removed the error and restart/startup, but did nothing to my VirtualHost configuration.

Please help :-)

```

---

