---
title: "running scripts at boot"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2005-07-19
I have two scripts that I run at boot.  Here is what I do to execute them (as root):

```

cd /usr/local
. woodlands.sh

cd bin/tomcat
. catalina.sh run &

```

How can I automate this?  I tried creating a script in /etc/init.d/ with the lines

```

/usr/local/woodlands.sh
/usr/local/bin/tomcat/catalina.sh run &

```
but that didn't work..  can somebody help me?

---

### Post by delltony on 2005-07-19
Basicially it has to be added to rc.update ( i think that is the right file) in any case the easiest way to do it I have found is do like you did and put the script in init.d  then install a program called "bum" (boot up manager) and then the name will be in the listing and you should be able to click on it to activate it on next bootup.
Hope this helps.

---

