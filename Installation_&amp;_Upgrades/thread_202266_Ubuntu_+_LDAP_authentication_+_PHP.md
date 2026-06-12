---
title: "Ubuntu + LDAP authentication + PHP"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by tinjman on 2006-06-23
Hello everyone,

I am using with apache 2 and php5. I need to install the LDAP module for PHP as I would like to use PHP to authenticate against our LDAP in the college here. 

From the Ubuntu forum I have learned I need to install the package php5-ldap 

sudo apt-get install php5-ldap

That package is installed now  but for some reason phpinfo() gives no LDAP info and  when I call the ldap_connect() function in PHP I get "Call to undefined function ldap_connect()"

I'm rather stuck at this stage and would appreciate and advice.

Further info: In my php.ini there is the line "extension=ldap.so". That's the only mention of ldap in the php file.
One last thing, I did a search for the ldap.so file and it is in the /usr/lib/php5/20041030/ldap.so. Am not sure if all that is correct.

Thanks

---

### Post by flickerfly on 2007-03-02
Restarting the apache server seems to have taken care of this for me.

---

### Post by silurius on 2007-04-10
Edit: move along, nothing to see here.

---

