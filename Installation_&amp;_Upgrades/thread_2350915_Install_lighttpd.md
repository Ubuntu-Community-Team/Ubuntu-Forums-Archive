---
title: "Install lighttpd"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2017-01-28
I'm trying to setup Roundcube opensource webmail software on Ubuntu 16.04 LTS and I'm stuck right here while trying to install lghttpd.

```
compile and install it with ::

  $ cd lighttpd-1.x.x
  $ ./configure
  $ make
  $ su -
  # make install
  # exit


take look at the configfile in ./doc/lighttpd.conf,
make your own copy of that file and modify it for your needs.
```

I can post the configfile of need be.

If someone could give me help getting this installed so I can get Roundcube working that would be great!  ;)

---

### Post by deadflowr on 2017-01-29
Both lighttpd and roundcube have packages in the Ubuntu repositories.
Is there anything wrong with using those?


EDIT:
Anyhoo,
did you try the commands above or...

---

### Post by shane_faulkinbury2 on 2017-01-29
I've never used the repositorie!  So I just add the lighttpd url in Other Software?

---

### Post by shane_faulkinbury2 on 2017-01-31
I guess I'll close this since no one can answer me!

---

### Post by geeksmith on 2017-01-31
Wow...closing after just 2 days, and after somebody offered help. No worries, the forum offers a money-back guarantee!

Have you tried something like this?

```

sudo apt-get install lighttpd

```

This is how you install software in Ubuntu. You may also use the software manager to do so.

---

### Post by deadflowr on 2017-02-01
> **shane_faulkinbury2 said:**
> I've never used the repositorie!
Why not?

>   So I just add the lighttpd url in Other Software?
No.

Again though, how far into the sequence of commands to install lighttpd did you get?

---

