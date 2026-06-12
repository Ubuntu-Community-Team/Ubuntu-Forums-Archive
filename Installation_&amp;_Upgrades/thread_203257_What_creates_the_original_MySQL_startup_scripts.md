---
title: "What creates the original MySQL startup scripts"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by likeaneaglenow on 2006-06-24
I have deleted the mysql startup scripts in init.d after I removed MySQL from my system. When I use apt-get or the Synaptic package manager to re-install MySQL it doesn't re-create them. What installs them in the first place and how do I make them again? Any help would be greatly appreciated.

PS I don't want to re-write the scripts manually, I want to re-create them as per the original install.

---

### Post by jasutton on 2006-06-26
I don't know what you'd classify as re-writing manually, but you might try copying the scripts from another Ubuntu installation.

---

### Post by likeaneaglenow on 2006-06-26
Re: MySQL startup scripts for Ubuntu.
I don't have another ubuntu installation I can copy the scripts from. 
I'd love to know all about Ubuntu and MySQL. So for starters I want to know how the MySQL startups scripts get created/installed. And how I can repeat this procedure.
I thought simply un-installing and re-installing MySQL would re-create the scripts, but no, that didn't happen. Or am I missing something?

Any help at all would be appreciated.

---

### Post by jasutton on 2006-06-26
I thought that those scripts were created during the installation of MySQL as well.  You might try removing MySQL with the following:

```
sudo apt-get remove mysql-server --purge
```

Once it's removed reinstall it with the following:

```
 sudo apt-get install mysql-server
```

---

### Post by likeaneaglenow on 2006-06-26
Thanks for the reply!

I have already tried that, but did it again anyway. No luck. Still no scripts. I also tried apt-get remove mysql*, which freed up 68mb of disk space. On re-install again NO scripts. ](*,)

There has got to be an answer for this somewhere.

---

### Post by jasutton on 2006-06-27
Well, I did a little more investigation.  It turns out that the "mysql-server" package is just a pseudo-package pointing to "mysql-server-5.0" which has the real data.  That package has the file you need.  I even disected the DEB to make sure (see attached screenie).

To make sure that it re-installs, you can issue this command:

```
sudo apt-get install mysql-server-5.0 --reinstall
```

:)

---

### Post by likeaneaglenow on 2006-06-27
I did as you suggested but it didn't work. HOWEVER, I purged ALL MySQL (apt-get remove mysql* --purge) and I got a screen asking me if I wanted to remove all configuration files. I did and it wiped them all. When I re-installed the startup scripts were there!!! Finally. 
I'm sure if I purged just the MySQL server-5 it would have done the same thing. I will try it later.

Thanks for your help jasutton. You sure pointed me in the right direction.:D :D

---

### Post by jasutton on 2006-06-27
Glad I could help (and get away from studying History of Civilization for a while :D).

---

