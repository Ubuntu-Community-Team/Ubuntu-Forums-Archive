---
title: "Mootools giving me trouble with ZoneMinder"
date: 2013-11-03
forum: Installation &amp; Upgrades
---

### Post by Destruct0r on 2013-11-03
Hallo.
I have been having some trouble installing ZoneMinder, and am stuck with mootools not begin served from my server.  Zoneminder's 1.25 pacakge in Ubuntu refers to server path "/javascript/mootools/mootools-more-nc.js" note, not a relative path.  This made me think that the installation of libjs-mootools might be broken.  (I have made sure version 1.4.5 of libjs-mootools) is installed.

On my server I have the files located at /usr/share/javascript/mootools, but they are not begin served. ZoneZinder 404s on mootools:

```
404 Not Found - pathtomyserver/javascript/mootools/mootools-more-nc.js
```

I have [posted]("http://www.zoneminder.com/forums/viewtopic.php?f=29&t=21599&sid=c4105424b78bee82c8c6ef5290572ec8") something at the ZoneMinder's forums, but no replies.  

Any advice on getting this working?  I am using Ubuntu 13.10

---

### Post by Destruct0r on 2013-11-05
Got the solution working with Apache VirtualHosts.  (Installing Zoneminder should be easier! I'm looking at your Ubuntu!)  See post I linked to in previous post for more details.

Used some config help at  [http://httpd.apache.org/docs/current/vhosts/examples.html](http://httpd.apache.org/docs/current/vhosts/examples.html)

---

