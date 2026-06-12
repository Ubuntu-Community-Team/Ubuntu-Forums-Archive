---
title: "Tomcat wont start"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by kgilmore on 2012-03-02
Hi,

I've been having alot of trouble installing alfresco on ubuntu (ec2 if that makes any difference).

I followed a long guide and would you know it failed on the very last step.
[http://blog.mycroes.nl/2010/04/installing-alfresco-33-on-ubuntu-lucid.html](http://blog.mycroes.nl/2010/04/installing-alfresco-33-on-ubuntu-lucid.html)

Basically tomcat6 failed to start and i get the;

```
* Starting tomcat servlet engine tomcat6      [[COLOR="Red"]fail[/COLOR]]
```

Please help!
Thanks.

---

### Post by vra5107 on 2012-03-03
Probably not a good place for this question. 

Does the server output any logs ? Did you try posting a question right below that blog? 

My experience has been not to install tomcat from apt-get. Just download it from apache.org website and extract it to your HOME directory. This way everything is centralized in one place. Saves a lot of trouble.

Venkat

---

