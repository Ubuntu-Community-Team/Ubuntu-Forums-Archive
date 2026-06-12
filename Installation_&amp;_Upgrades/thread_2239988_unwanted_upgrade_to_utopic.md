---
title: "unwanted upgrade to utopic?"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by gmalac on 2014-08-17
Can't figure how this happened, on my headless server I was on 12.04 LTS and dist-upgrade to install 14.04
Now I am getting errors with Postgress and can't start it.
Tried remove it and re-install, no luck!
Doing *lsb_release -a* i get:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Utopic Unicorn (development branch)
Release:	14.10
Codename:	utopic
How is this possible and more important any idea as to either go back to 14.04 or install Postgress (openerp is broken without Postgress, all the rest seems working though)
Thanks
guy

---

### Post by coffeecat on 2014-08-17
> **gmalac said:**
> How is this possible

Certainly not from running apt-get dist-upgrade which simply does an upgrade within a particular release with different handling of dependences than the ordinary upgrade command. I suspect you may have done "do-release-upgrade -d" but check back through your bash history and post whichever command got you to this state.

If you are running 14.10, you can't downgrade to 14.04. You would need to do a fresh install of 14.04.

---

### Post by gmalac on 2014-08-17
thanks for that
Yes must have done do-release-upgrade but I was on 12.04 so how it went up to 14.10????
I don't have the skills to do a fresh install, this is an old headless hpex490, no screen no keyboard....
Guess I will have to wait for 14.10 to become out of development then.
Problem is Postgress though,  and no more OpenERP for some months.
thanks again

---

### Post by coffeecat on 2014-08-17
> **gmalac said:**
> 
Yes must have done do-release-upgrade but I was on 12.04 so how it went up to 14.10????

Yes, I was wondering that. I really don't know offhand whether if you do "do-release-upgrade -d" in 12.04 it takes you directly to 14.10. I would have thought it should not. If you run this command:

```
history
```

You'll get your bash history. It must be instructive to have a look to see which exact command or commands you ran.

---

### Post by grahammechanical on 2014-08-17
The d switch means development release and there is only one development release at any time. The command could not upgrade to 14.04 development release (trusty tahr) because those repositories are now the official 14.04 (trusty) repositories. So, it must be Utopic Unicorn (14.10). It is machine logic.

Looking on the bright side, I am finding Utopic Unicorn stable enough to be boring. I use it daily. Keep regular backups of the data and run daily updates. The lack of a desktop environment and a user interface reduces the risk from running the development release.

---

### Post by coffeecat on 2014-08-17
> **grahammechanical said:**
> The d switch means development release and there is only one development release at any time. The command could not upgrade to 14.04 development release (trusty tahr) because those repositories are now the official 14.04 (trusty) repositories. So, it must be Utopic Unicorn (14.10). It is machine logic.

Yes, indeed, the -d option means upgrade to the devel release. That's clear. However, I would have thought an upgrade beyond 12.04 -> 14.04 would not be allowed to happen, since such an upgrade jump is not supported, and I would have expected running "do-release-upgrade -d" to result in an error rather than just proceeding to an upgrade directly to 14.10. Since I don't have a 12.04 to test this on, it would be interesting to see exactly what command or commands the OP ran.

---

