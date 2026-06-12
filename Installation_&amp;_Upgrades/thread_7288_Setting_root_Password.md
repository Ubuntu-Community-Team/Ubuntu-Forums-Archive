---
title: "Setting root Password"
date: 2004-12-05
forum: Installation &amp; Upgrades
---

### Post by Bob on 2004-12-05
Hi
I'm trying to get webmin working with ubuntu but webmin wants a root password, which because of sudo I don't have.
I've read the FAQ's and tried the sudo passwd etc etc but none of it seems to set a perminent password.
How do I set a root password? ](*,)

---

### Post by bazuka on 2004-12-05
sudo passwd root
type in _your_ password
choose root password

I have webmin running and this is how I did it.

---

### Post by p!=f on 2004-12-05
[QUOTE=Bob]Hi
I'm trying to get webmin working with ubuntu but webmin wants a root password, which because of sudo I don't have.
I've read the FAQ's and tried the sudo passwd etc etc but none of it seems to set a perminent password.
How do I set a root password? ](*,)[/QUOTE]
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

---

### Post by Bob on 2004-12-05
bazuka
Thanks for your reply, I've tried exactly what you suggested, unfortunately it didn't work.
I have been able to create a root password however
I cannot log into the system as root with the password I have created for root, however if I open a  user terminal and then su to root I have to use the password I have created for root to become root. 
So the password seems to be valid some of the time!!
Webmin still rejects the root password.

p!=f
Thanks for your reply but as I said in my post I'd looked at the FAQ's but to no avail.

---

### Post by randy on 2004-12-07
I'm pretty sure root login from the gdm screen has been disabled in the pam configuration.

---

### Post by p!=f on 2004-12-07
```
:~ $ grep AllowRoot /etc/gdm/gdm.conf
AllowRoot=false
```

---

### Post by hndrcks on 2004-12-08
In /usr/share/webmin/ there is a Perl script called changepass.pl to change root password in webmin use this:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

And that will fix it!

---

