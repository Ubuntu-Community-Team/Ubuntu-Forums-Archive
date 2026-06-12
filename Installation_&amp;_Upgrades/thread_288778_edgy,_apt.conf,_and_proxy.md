---
title: "edgy, apt.conf, and proxy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by El Rey de Todo on 2006-10-30
I just reinstalled edgy from an rc disc which I downloaded a day or two before the official release and I've run into a huge problem with apt: **there is no apt.conf on my system**, and when I create one it just gets ignored.

I really need to specify an http proxy for aptitude but it's exceedingly difficult when the config file isn't read.  I finally managed to get updates going with the http_proxy environment variable but this isn't the proper solution to my problem and I really want to know why I don't have apt.conf.

Does anyone else (who did a fresh edgy install) have this file? Can you check to see what package owns it?  This has already pissed off another person I was trying to migrate to edgy, he ended up using FC6 instead.  I'd hate for more people to give up on Ubuntu because they can't configure a proxy!

---

### Post by srix on 2006-11-06
The documentation is not too good on this, but all you have to do is create /etc/apt/apt.conf with the following lines:
ACQUIRE
{
  http::proxy "http://<proxy ip>:<port>";
}

Run "apt-get update" and check.

HTH you to convert your friend back from FC6 :)

---

