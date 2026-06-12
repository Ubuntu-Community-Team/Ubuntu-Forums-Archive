---
title: "Why wont alternate cd work for me?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Rowan_ on 2008-04-25
The upgrade manager wasnt working and so I downloaded the alternate CD (ubuntu-8.04-alternate-amd64) which is supposed to upgrade without a web connection right?
Each time i try to upgrade from the CD I receive an error message:

"Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."

At first it just had the same hangups as the Upgrade Manager, which lead me to believe that for some reason the CD installation is trying to connect to internet.  But i dont have a clue...... 

Has anyone else had this problem?

---

### Post by jackpetrilli on 2008-04-27
> **Rowan_ said:**
> The upgrade manager wasnt working and so I downloaded the alternate CD (ubuntu-8.04-alternate-amd64) which is supposed to upgrade without a web connection right?
Each time i try to upgrade from the CD I receive an error message:

"Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."

At first it just had the same hangups as the Upgrade Manager, which lead me to believe that for some reason the CD installation is trying to connect to internet.  But i dont have a clue...... 

Has anyone else had this problem?

Yes, I've had the same problem. I've tried using the alternate cd to upgrade and get this "error authenticating..." msg and then the upgrade program quits.

The only reason I've even tried the alternate cd is because the online upgrade quits on me with a "network problem" msg. even though I do not have a network problem.

So as of this moment, I can't upgrade...

- Jack

---

### Post by catalina on 2008-04-27
Hi Guys,

I see that you downloaded the amd64 alternate install.  Are you using a dual processor?  If not you need the i386 install (alternate version).

What are the specs on your system?  How much memory...processors...

---

### Post by jackpetrilli on 2008-04-27
> **catalina said:**
> Hi Guys,

I see that you downloaded the amd64 alternate install.  Are you using a dual processor?  If not you need the i386 install (alternate version).

What are the specs on your system?  How much memory...processors...

What makes you think I downloaded the amd64 alternate install?!!

I have the "ubuntu 8.04 i386" iso which I burned to a CD.

- Jack

---

### Post by Peter09 on 2008-04-27
just check that you can issue a command with sudo in a terminal.

```
sudo <any command>
```

If you have an error go to recovery mode and edit **/etc/hostname**

If your host name is more than a single word then change it to one simple word. Then try booting again.

PC

---

### Post by jackpetrilli on 2008-04-27
I regularly use "sudo" but I tried it again, just to make sure.  No problems with it.  

When I get that "error authenticating" msg, it lists a whole slew of files including things like compiz fusion, etc.

- Jack

---

