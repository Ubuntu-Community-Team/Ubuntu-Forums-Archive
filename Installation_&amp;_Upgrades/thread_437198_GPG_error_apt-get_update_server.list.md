---
title: "GPG error apt-get update server.list"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by emiliorecio on 2007-05-08
Hi. I have the same problem for second time whit apt-get update. Apt-get error

. Googlenadola, i found this explanation:
In Argentina Telefonica provide Internet service as Speedy. The proxy servers of speedy don't renew the cache from some days. So i do this:
1 - Create this script:
$$> sudo gedit script.sh

#!/bin/bash
export http_proxy=http://$1
apt-get update

2 - $$> chmod 755 script.sh

3 - run

$$>sudo  ./script.sh IP:PORT

were ip is one from this page [http://www.echolink.org/proxylist.asp](http://www.echolink.org/proxylist.asp)
This IP's are anonymous proxy servers. Use google to find more.

If work go to step 5
else go step 3
I need to probe this 3 times because some proxys don't work.

5 - Disable variable proxy
$$> export http_proxy=

6- run apt-get upgrade

It's work for me. I hope this work for you

Saludos!
Edit/Delete Message

---

