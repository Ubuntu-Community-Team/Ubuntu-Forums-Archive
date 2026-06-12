---
title: "demo unable to resolve host"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by nufftenthousand on 2011-05-25
I'm trying to boot from my CD drive to try Ubuntu 11.04. Every time I try to boot, I get the splash screen, but then I get an error saying
```
sudo: unable to resolve host
```No host name after. Then some more stuff comes up and the screen glitches after about a minute.

I'm running an AMD Athlon 64 X2 processor, and I've tried an image of both 32-bit and 64-bit Ubuntu, but both do pretty much the same thing. I also checked the disc for defects from the start page options, and no errors. My system's currently running XP, but my goal is to wipe my hard drives and only run Ubuntu, if I can ever get it to boot...

Any ideas? If more info is needed, let me know. I'm new to Linux.

---

### Post by wildmanne39 on 2011-05-25
> **nufftenthousand said:**
> I'm trying to boot from my CD drive to try Ubuntu 11.04. Every time I try to boot, I get the splash screen, but then I get an error saying
```
sudo: unable to resolve host
```No host name after. Then some more stuff comes up and the screen glitches after about a minute.

I'm running an AMD Athlon 64 X2 processor, and I've tried an image of both 32-bit and 64-bit Ubuntu, but both do pretty much the same thing. I also checked the disc for defects from the start page options, and no errors. My system's currently running XP, but my goal is to wipe my hard drives and only run Ubuntu, if I can ever get it to boot...

Any ideas? If more info is needed, let me know. I'm new to Linux.
Hi, how long are you letting the cd run, it actually loads very slow and it looks like it is frozen when it is not.

---

### Post by nufftenthousand on 2011-05-25
I let it run for 45 minutes.

---

### Post by wildmanne39 on 2011-05-25
> **nufftenthousand said:**
> I let it run for 45 minutes.
Hi that error message means that it could not connect to the server, it might have been down, you could try to install and tell it not to download third party updates where it does not try too connect to the server.:)

---

### Post by nufftenthousand on 2011-05-25
OK. I'm not quite sure how to do that, but today I tried again and got something slightly different (I haven't changed anything as far as I know) and some more info.

With 32-bit I get:
```
grpck: cannot open /etc/group
grpconv: cannot open /etc/group
bus error
chmod changing permissions of `/etc/group': Input/Output error
chmod changing permissions of `/etc/shadow': Input/Output error
install: invalid user `ubuntu'
install: invalid user `ubuntu'
Generating locales...
  en_US.UTF-8... done
Generation complete
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
/usr/sbin/make-ssl-cert: line 117:     622 Bus error      chownroot: ssl-cert /etc/ssl/private/ssl-cert-snakeoil.key
sudo: unknown user: ubuntu
...
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
...    #(some seemingly good stuff)
Repeat this process for the rest of the CDs in your set
W: Skipping nonexistent file /cdrom/dists/natty/main/binary-i386/Packages
W: Skipping nonexistent file /cdrom/dists/natty/restricted/binary-i386/Packages
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
sudo: unknown user: ubuntu
```And then nothing else happens.

With 64-bit I get:
```
sudo: unable to resolve host (none)
...
no value set for `/apps/netbook-launches/favorites/favorites-list'
no value to set for `/apps/netbook-launches/favorites/favorites-list'
```and then a bunch of stuff with [OK] to the right of it, so I assume that's not a problem, but then it does nothing.

I'm not sure what most of this means. Does it give any more insight into what's causing the problem? Thanks for the help so far, btw, and sorry for the lengthy post.

---

