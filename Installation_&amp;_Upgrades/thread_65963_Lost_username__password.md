---
title: "Lost username / password"
date: 2005-09-15
forum: Installation &amp; Upgrades
---

### Post by Master Shake on 2005-09-15
On one  machine that I hardly ever use, in which I had installed Ubuntu, I do not remember what my username or password for this station is.  IS there

a) Anyway to retrieve this info
b) any sort of back door to get this?  I'm sure if I could retrieve the username, I could figure out the password.

---

### Post by evilghost on 2005-09-15
Sure is, when booting, and GRUB loads, press [ESC] and choose Recovery  Mode.

This will boot into Linux single-user mode.

From there, simply type:

```

passwd {username}

```

Where {username} is the username you use.  The { and } are not necessary.  This will reset the password.

Hope this helped.

---

### Post by Master Shake on 2005-09-16
That's good information, but I need to recover the username too.  If I can't do that, can I create a new user from recovery mode?

---

### Post by Master Shake on 2005-09-16
I love the help I get on here, but I also love it when I figure things out for myself...

What I did was boot into recovery mode, and did the following:

useradd -d /home/mwshake -s /bin/tcsh -p shake  mwshake

This created a username of mwshake, created his home dir, and set his password at shake

 \\:D/  \\:D/

---

### Post by Master Shake on 2005-09-16
And another from the department of *duh*

Log into recovery mode, and did an ls /home and was able to retrieve my username.   :roll:

---

