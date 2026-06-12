---
title: "Problem with synaptic after upgrading from warty to hoary"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by najeli on 2005-04-12
I've used warty for two weeks about and I decided to upgrade to hoary one day after it was released.
So... I read a short manual on ubuntu page and with synaptic:
1. I changed repository from warty to hoary and switch off all other
2. I marked "all to update" and updated them. It said that synaptic should be removed. So I agreed, I could install it later.
3. I rebooted my machine and I've got brand new hoary running
4. I ran sudo apt-get install synaptic. No problems.

But problems came, when I wanted to run it. It asked me for pass, I've put it, but there was 
```
Failed to run /usr/sbin/synaptic:
Wrong password.
```
It was for SURE good pass, because it works when I run sudo or root terminal. And I can run sudo synaptic or simply synaptic from root terminal. And I tried it many times to be sure I typed it correctly.
The activator has this command to run synaptic:
```
/usr/sbin/su-to-root -X -c /usr/sbin/synaptic
```
And now I don't know what could be wrong... Any ideas?...

---

### Post by najeli on 2005-04-13
Hmm...

I've tried reinstalling gksu and menu packages, but it doesn't work either.
It's really not comfortable to run synaptic from commandline and I really do not know what to do.

I would be grateful for any directions.

---

