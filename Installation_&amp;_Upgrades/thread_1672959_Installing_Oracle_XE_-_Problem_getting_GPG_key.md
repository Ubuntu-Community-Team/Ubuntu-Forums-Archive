---
title: "Installing Oracle XE - Problem getting GPG key"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by zia.newversion on 2011-01-21
I am trying to add this repository to the aptitude repo list.
```
deb http://oss.oracle.com/debian unstable main non-free
```

I am trying to install Oracle XE... For that, I have to add this specific repo. I am following this article here.
[http://www.cyberciti.biz/faq/howto-install-linux-oracle-database-xe-server/](http://www.cyberciti.biz/faq/howto-install-linux-oracle-database-xe-server/)

There is no problem editing the sources.list file. But when I try to wget the GPG key, there is this error:
```
ERROR 404: Not Fount.
gpg: no valid OpenPGP data found
```

Looks like wget cannot access the key because it is not there. I do not know about the structure of GPG keys and their relation to repositories. All I know is for every repo that I add, there has to be a key retrieved from Ubuntu keyserver. However, in the above case, I am trying to get a key from the Oracle site which of course is not there. Has the structure been changed? What should I do now? I visit the oracle website and there is no information regarding the subject that I can find.

Any help will be duly appreciated. Thanks in advance.

---

### Post by Old_Grey_Wolf on 2011-01-21
I would try going to the Oracle XE download website and read Oracle's instructions. The article you linked to is 3 1/2 years old. I think Oracle released 11g since that article was written.

---

