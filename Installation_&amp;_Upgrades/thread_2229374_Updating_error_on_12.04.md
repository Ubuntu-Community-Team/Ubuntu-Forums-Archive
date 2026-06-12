---
title: "Updating error on 12.04"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by M.Yusuf_YILMAZ on 2014-06-12
Hi;
Using ubuntu 12.04. 

Im getting error when i use sudo apt-get update. It says 

[COLOR=#000000]*W: Failed to fetch *[/COLOR][http://repo.maxindo.net.id/mariadb/r...se/Release.gpg]("http://repo.maxindo.net.id/mariadb/repo/5.5/ubuntu/dists/precise/Release.gpg")[COLOR=#000000]* Could not connect to repo.maxindo.net.id:80 (203.173.91.21), connection timed out*[/COLOR]


[COLOR=#000000][I]W: Some index files failed to download. They have been ignored, or old ones used instead.

how can i fix it ? 

Thanks[/I][/COLOR]

---

### Post by slickymaster on 2014-06-15
[http://en.wikipedia.org/wiki/Bump_(Internet)](http://en.wikipedia.org/wiki/Bump_(Internet))

[COLOR=#000000]As a general rule, give about 24 hours after posting a thread to bump it, if it hasn't gotten a response.[/COLOR]

---

### Post by M.Yusuf_YILMAZ on 2014-06-18
Anyone ?

---

### Post by QIII on 2014-06-18
Hello!

You are getting that error because the url for that repo is unreachable.  

How did you add it to your sources?

---

### Post by M.Yusuf_YILMAZ on 2014-06-19
Im new user at linux/ubuntu i dont know how did i mistake.

---

### Post by xc3RnbFO8P on 2014-06-19
open Software & Updates > Other Software
and remove or uncheck this line  **[http://repo.maxindo.net.id](http://repo.maxindo.net.id)............**

---

### Post by M.Yusuf_YILMAZ on 2014-06-19
Thank you it worked. :)

---

