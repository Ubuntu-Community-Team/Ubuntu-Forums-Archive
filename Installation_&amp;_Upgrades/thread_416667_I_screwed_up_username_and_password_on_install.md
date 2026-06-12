---
title: "I screwed up username and password on install"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by teastman on 2007-04-21
Okay - I 'm still new at all this.

I installed Innotek's Virtualbox on my machine at work and installed Kubuntu from the 7.04 beta desktop iso image into that virtual machine.  All seemed to have gone okay.  Kubuntu booted up and viola'!  Login panel for username/password.

Except the username and password **I KNOW I CREATED** during the install are not accepted in the login!

How do I start kubuntu to a "root" konsole and edit user profiles etc and correct the user setup files?  (yes I know there's no "root" per say in kubuntu but my sudo user can't log in!).  If a lot of that terminology sounds window-ish please forgive me - as I said I'm kinda new at this.

It went pretty well on my home machine - It's kinda nice to be able to "practice" here on a Virtual Machine in case I break something.

Thanks
Tim

---

### Post by heimo on 2007-04-21
Boot into recovery mode
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
and use
```
passwd [your username]
```
to change password.

---

