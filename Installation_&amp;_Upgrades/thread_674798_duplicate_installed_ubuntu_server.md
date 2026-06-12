---
title: "duplicate installed ubuntu server"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by resadem on 2008-01-22
Hi,

I have an Ubuntu server installed with extra packages and application like sawmill, webmin, postfix, etc.
I want to make a working copy of this server , I want to move this ubuntu server to another server.
I wounder if I could make a copy of this ubuntu server and put to other server?

Thanks

---

### Post by Thanoulis on 2008-01-22
I'm not familiar with this kind of stuff, but did you try to 'ghost' it?

---

### Post by scorp123 on 2008-01-22
> **resadem said:**
>  I have an Ubuntu server installed with extra packages and application like sawmill, webmin, postfix, etc. I want to make a working copy of this server 

You sound like you'd want to take a look at this:
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

"RemasterSys" creates an installable live CD or live DVD of your installed system, e.g. you can clone systems with this.

I personally use this method (the second "low level" one mentioned in this post):
[http://ubuntuforums.org/showpost.php?p=3795815&postcount=2](http://ubuntuforums.org/showpost.php?p=3795815&postcount=2)

Specifically, if you go to the link that explains what I backup, read the part about getting the package selections back (= tell system 'B' to install the absolutely same packages that are already installed on system 'A' ...). It's very easy to do.

---

