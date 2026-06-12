---
title: "Upgrade to 16.04 brings me to login screen"
date: 2016-08-15
forum: Installation &amp; Upgrades
---

### Post by ddubbz1979 on 2016-08-15
I came home to see the upgrade button on my Ubuntu screen. Thinking, "why not?" I hit it and now see a black screen with tty1 and asking to login. Nothing happens once I do. After reading through posts and playing around I ran code to configure dpkg --a. Last line after all the code ran says: dpkg: unrecoverable fatal error, aborting: unable to create '/var/lib/dpkg/updates/tmp.i':no space left on device

I'm at a loss . Love ubuntu and would love to get back to a gui and my files. Any help appreciated. Thanks in advance.

---

### Post by ddubbz1979 on 2016-08-15
Update:  after selecting to keep current version and typing reboot I'm back into ubuntu. Not sure if new version or not however. I am still being asked to run sudo dpkg --configure -a to correct problems.

---

### Post by howefield on 2016-08-16
I'd suggest running the command.

To confirm the version that you are running, try..
```
cat /etc/os-release
```

What's the output ?

---

