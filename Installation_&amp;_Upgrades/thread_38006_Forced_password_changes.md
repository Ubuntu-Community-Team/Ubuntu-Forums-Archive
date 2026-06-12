---
title: "Forced password changes"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by dblyth on 2005-05-29
So I've read about some of the problems people have had with the "Child terminated with 1 status" error message -- I'm having the same problem, and nothing is working.

*Every* time I log in, I am forced to change my password at the login screen, which is becoming quite a hassle. 

Also, every time in a regular terminal that I want to run a command with sudo, I get the message:

sudo: reset your password and try again, (null)Account or password is expired.

First of all, why is it making me change my password every time I want to do something, and second of all, could this be why the gksudo interface *never* works also?

---

### Post by nocturn on 2005-05-30
[QUOTE=dblyth]So I've read about some of the problems people have had with the "Child terminated with 1 status" error message -- I'm having the same problem, and nothing is working.

*Every* time I log in, I am forced to change my password at the login screen, which is becoming quite a hassle. [/quote]

When you are logged in, try this command:
```
chage -l
```

It will ask your password and show something like this:
Minimum:        1
Maximum:        99999
Warning:        14
Inactive:       -1
Last Change:            May 10, 2005
Password Expires:       Never
Password Inactive:      Never
Account Expires:        Never

If it is still expired, try changing the password from the command line with passwd.

> 
Also, every time in a regular terminal that I want to run a command with sudo, I get the message:

sudo: reset your password and try again, (null)Account or password is expired.

First of all, why is it making me change my password every time I want to do something, and second of all, could this be why the gksudo interface *never* works also?

Yes, gksudo will fail on this.

---

