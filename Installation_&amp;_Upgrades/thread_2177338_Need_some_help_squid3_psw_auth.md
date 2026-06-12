---
title: "Need some help squid3 psw auth"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by pM6AbH3 on 2013-09-28
I installed squid with :
>sudo apt-get install squid 

edited the squid.conf with :
> auth_param digest program /usr/lib/squid3/digest_pw_auth -c /etc/squid3/psw
auth_param digest realm proxy
acl authenticated proxy_auth REQUIRED
http_access allow authenticated

created the psw file with:
>htdigest -c /etc/squid3/psw proxy #username#

psw:
> #username#:proxy:#pswhash#

>service squid3 restart
the paths /usr/lib/squid3/digest_pw_auth & /etc/squid3/psw are correct

I am running Firefox 24.0 and after setting the proxyconf + the authentication he does not load any pages. I always wait 2 minutes, he is loading the site but nothing happens, no error.

---

