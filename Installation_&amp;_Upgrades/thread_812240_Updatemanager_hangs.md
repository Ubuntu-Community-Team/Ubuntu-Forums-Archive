---
title: "Updatemanager hangs"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-29
On several computers it happens more and more often, that the update manager hangs. 

Thereby the password prompt does not pop up.

Is there anything known when that happens and how to fix that?

bye

Ronald

---

### Post by daydream on 2008-05-30
I have found the following tip that worked for me like a charm:

Edit /etc/hosts with an editor of your choice (e.g. sudo vi /etc/hosts). There should be two entries with IPv4 addresses starting with 127.0.x.x, like this:

    127.0.0.1 localhost
    127.0.1.1 mycomputername.mydomain 

Remove the domain name from the entry starting with 127.0.1.1, leaving only the computer name and save the file. Now try again.

When I made this change I got the password prompt as expected and all the updates where downloaded and applied.

\\:D/
[http://www.joewein.net/blog/2008/05/17/update-manager-hangs-in-ubuntu-804-and-how-to-fix-it/#comment-8060](http://www.joewein.net/blog/2008/05/17/update-manager-hangs-in-ubuntu-804-and-how-to-fix-it/#comment-8060)

---

### Post by epee on 2008-06-01
> **daydream said:**
> Remove the domain name from the entry starting with 127.0.1.1, leaving only the computer name and save the file. Now try again.

I tried that, but it didn't work.

I changed line:
```
127.0.1.1 <hostname>

```

to:

```
127.0.0.1 <hostname>

```

and then it worked fine.

---

