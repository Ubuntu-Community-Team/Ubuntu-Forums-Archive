---
title: "where are ldap headers?"
date: 2015-05-28
forum: Installation &amp; Upgrades
---

### Post by sam_w2 on 2015-05-28
I'm installed via ```
sudo apt-get install slapd ldap-utils
```, and ```
sudo apt-get dpkg-reconfigure slap
```d so that I can run a test ldap server and phpldapadmin in php but cannot get it to run. The error returned is 'Call to undefined function ldap_connect()' which indicates the php does not have the ldap extension installed.

My Ubuntu is 14.04 and I use phpbrew to manage my php installs. I've searched [high]("http://serverfault.com/questions/692072/call-to-undefined-function-ldap-connect-in-ubuntu") and [low]("https://github.com/phpbrew/phpbrew/issues/502") for why phpldadadmin won't find the ldap extension.

I've also checked into the ldap-utils [page]("http://packages.ubuntu.com/trusty/ldap-utils") but don't see where those files are deposited. Perhaps someone can show me what I'm not seeing.

My goal is to find the ldap libraries so phpbrew can find its headers and compile php with what I need. Since phpbrew cannot find them, I need help to finish this command:

```
[COLOR=#333333][FONT=Consolas]phpbrew ext install ldap  --  --with-ldap=....[/FONT][/COLOR]
```

[COLOR=#333333][FONT=Helvetica Neue]whereis ldap yields the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]ldap: /etc/ldap /usr/lib/ldap /usr/include/ldap.h /usr/share/man/man3/ldap.3.gz

I would have thought that /usr/lib/ldap would be the answer because it's filled with *.h files but phpbrew returns:
```
[/FONT][/COLOR][COLOR=#C33720][FONT=Andale Mono]Command failed: ./configure --with-php-config=/home/sam/.phpbrew/php/php-5.4.33/bin/php-config >> /home/sam/.phpbrew/build/php-5.4.33/ext/ldap/build.log 2>&1 returns[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]
```

Help me understand where the headers are for the ldap files I installed using apt-get, thanx, sam[/FONT][/COLOR]

---

### Post by dino99 on 2015-05-29
here is what i've found:
[http://serverfault.com/questions/692072/call-to-undefined-function-ldap-connect-in-ubuntu](http://serverfault.com/questions/692072/call-to-undefined-function-ldap-connect-in-ubuntu)
[https://gist.github.com/kherge-old2/a7172c7102fbd738837d](https://gist.github.com/kherge-old2/a7172c7102fbd738837d)
[https://github.com/phpbrew/phpbrew/wiki/Requirement](https://github.com/phpbrew/phpbrew/wiki/Requirement)

---

### Post by sam_w2 on 2015-05-29
> **dino99 said:**
> here is what i've found:
[https://gist.github.com/kherge-old2/a7172c7102fbd738837d](https://gist.github.com/kherge-old2/a7172c7102fbd738837d)


That one is the magic answer! Thx for finding it.

---

