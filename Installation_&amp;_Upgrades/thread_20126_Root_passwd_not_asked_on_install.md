---
title: "Root passwd not asked on install"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by g0at on 2005-03-15
When I install, ubuntu never asks me to set a root password, only a user account. Soooo... how de &)%@ am I supposed to use  su  or mount my win drives?
Also... stupid network setup thing, doesn't want to activate any ppp accounts. 

hmmmm.  :neutral:

---

### Post by IdoMcFly on 2005-03-15
[QUOTE=g0at]When I install, ubuntu never asks me to set a root password, only a user account. Soooo... how de &)%@ am I supposed to use  su  or mount my win drives?
Also... stupid network setup thing, doesn't want to activate any ppp accounts. 

hmmmm.  :neutral:[/QUOTE]
 use search on this forum or ubuntu home page, there are plenty of answer to this :)

---

### Post by -DomiNator- on 2005-03-15
sudo passwd root in console :)

---

### Post by lao_V on 2005-03-15
It seems that this is the most common question here. Does anyone really bother with reading the [installation]("http://www.ubuntulinux.org/support/documentation/howto/installation-i386") document anymore? Or how about even a [guide]("http://www.ubuntuguide.org")? Or even [searching]("http://www.ubuntuforums.org/search.php?") for a problem before clogging the forum with repetetive issues????

---

### Post by puesco on 2005-04-05
Hi there,
my name is Kai, I'm new to Ubuntu (experience with Debian Sarge and SuSE, though).
I just installed Hoary 5.04 and even though I recognized the absence of the root password, I cannot figure out, how to work as root...

kai@ubuntu:~$ sudo apt-get update
Password:

If I leave the password blank and just hit enter, nothing happens:
kai@ubuntu:~$ 

Trying to activate the root-password does not work, either:
kai@ubuntu:~$ sudo passwd root
Password:

It looks like there is a password set, but I certainly have not chosen one, and the installation is only 2 hours old, nobody but me having touched it... Does anybody have a clue what happened, or what can be done??

Thanks
Kai

---

### Post by skoal on 2005-04-05
When I installed Ubuntu the other day, I read how to do this somewhere in the online docs.

Basically, when you:

sudo passwd root

* You need to first enter your password as the normal user (the one using sudo).  Then, the following 2 password prompts are for the root password and the verification of it, respectively.  That's 3 password prompts by my count, if that's what was confusing you.

---

### Post by fayce on 2005-04-05
type su 
you'll be root

after that type passwd to configure the root password

---

