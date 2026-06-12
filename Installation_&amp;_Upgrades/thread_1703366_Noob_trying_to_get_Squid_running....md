---
title: "Noob trying to get Squid running..."
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by paposeco on 2011-03-09
Hey guys I'm new to Linux but feel like with time me and Ubuntu are gonna get along just fine.

Im using Ubuntu 10.10 and I've installed Squid and Webmin.

Webmin is up and running and I think squid was suppose to be running fine too but I get an error when I try to run it that i just dont understand hope someone can help.

My idea first of all is making my hardware department machine cache windows update.

I figured I might be able to do it just by having this machine on the network with ubuntu and squid running and just configuring this machines address as a proxy on the client's computers.

So if my net work is 172.16.2.88 all other machines 172.16.2.XX with the proxy configured for the .88.

Is this possible?

The error I'm getting while trying to run squid is this: 

"2011/01/21 09:25:17| ACL name 'all' not defined!
FATAL: Bungled (null) line 180: icp_access deny all
Squid Cache (Version 2.7.STABLE9): Terminated abnormally."

I've googled it but have no idea what it means or how to fix it. I've been going at this for a week and I'm kinda tired of banging my head against the wall.

I've searched for a proper tutorial and I've found one that guided me brilliantly to this point. Webmin is up and running just updated to 1.530.

Any help would be most appreciated.

---

### Post by mpnordland on 2011-03-09
That is normal, squid needs to be configured before it will/can run.
see here for more details:[http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid]("http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid")

---

