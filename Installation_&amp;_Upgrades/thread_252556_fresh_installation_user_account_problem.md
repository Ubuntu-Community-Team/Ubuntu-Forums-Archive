---
title: "fresh installation user account problem"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by jameswnl on 2006-09-07
Hi,

Just installed Ubuntu 6.06 LTS.  During installation, it asks for username and password.  I filled in the fields to create one.  However it didn't ask for root password.  

Then after installation, when I tried to su, of course I can't coz I don't know root password which I never got chance to set.

Then I thought I might had clicked too fast and missed the root password prompt.  So I decided to reinstall the whole thing (great is that it's fast).

This time I created an account name as "root".  Installation was smooth.  But I can't login, it simply doesn't allow root login.

So what did I miss?

thx

---

### Post by jameswnl on 2006-09-07
I now know that I should have created a user other than "root" and then use "sudo" to set root password.

But in current situation (that I only created "root" account), what can I do to get around it (except another install)?

(I should have read this)
[http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)

thx

---

### Post by aysiu on 2006-09-07
There's no root login: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

You do *not* need to log in as root.

---

