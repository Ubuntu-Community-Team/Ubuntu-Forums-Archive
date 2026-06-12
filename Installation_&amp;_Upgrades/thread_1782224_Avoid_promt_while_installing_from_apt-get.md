---
title: "Avoid promt while installing from apt-get"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by l_o_s_b on 2011-06-14
While writing a small install script that should be executed during the post part of a pxe install I found out that two packages promts for user-input during install.

sudo apt-get --yes -q --force-yes install mysql-server
sudo apt-get --yes -q --force-yes install likewise-open 

Mysql-server asks if I would like a root password for the mysql server. Likewise ask for "Default Kerberos version 5 realm:". Is there a way to feed those in from command line so the installation don't stop and wait for input?

I am doing this for the school I am attending where I assist/help the sysadmin in charge of the Linux deployment. The school is primary using Windows machines and servers and we are going to use likewise to connect to active directory. The sysadmin I am assisting likes Linux but as the entire system is Windows based he do not have that much experience and neither do I.

---

### Post by smurphy_it on 2011-06-14
I haven't used it before, but I think "expect" can help with this matter.  However, in the case of the mysql prompt for a password.  This is something you would typically put in once.

---

### Post by sanderd17 on 2011-06-14
As a very unsecure hack, you could use xdotool to send key codes to a terminal window. 

But if you e.g. do a sleep 5 and the step just takes 6 seconds, than that step will probably get the next answer (I don't know that for sure though).

---

### Post by l_o_s_b on 2011-06-14
Thank you for replying. 

I tried the xdotool and it did somewhat work on mysql-server. If I gave xdotool a string the password would end up blank. But thats not really a problem for us as it should only be used on localhost and everyone should get access. I am pretty sure there are better ways of doing it, but it will have to do for now.

Did not get it to work with likewise-open, but I will try again tomorrow. Most likely a user error...

---

### Post by JRV on 2011-06-14
I use

```
echo y|apt-get install PACKAGE
```

in install scripts.

---

