---
title: "Can't Sudo or get to root"
date: 2015-05-12
forum: Installation &amp; Upgrades
---

### Post by Mike_Hughes on 2015-05-12
When I try to go to sudo su I get the following error - sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
macmike@ubuntuServer:/usr$. Was working just start this error. What do I do to fix this one. I can't start the server and log in as root either. I can't ssh in as root either. Gives me permission denied.  I tried resetting root password and it will not let me. My mysql server will not start either.

I try to do anything with sudo I get - sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
I tried to chown and says not permitted.

---

### Post by QDR06VV9 on 2015-05-12
Run in terminal
```
ls -l /usr/bin/sudo 
```
And paste back the return here.
Regards

---

### Post by shricharijigmail. on 2015-06-24
could u pls help me fixing it?

---

### Post by dino99 on 2015-06-24
'sudo' is only used to grant root privileges, and must be followed by a command
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

