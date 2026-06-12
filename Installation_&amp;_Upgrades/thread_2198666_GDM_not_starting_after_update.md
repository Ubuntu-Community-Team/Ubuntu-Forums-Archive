---
title: "GDM not starting after update"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by sundays211 on 2014-01-09
Hi,

Following the update to GDM today, the display manager is not launching automatically when I start my computer. Instead, I am thrown into a text shell. I am able to then start GDM by typing "sudo gdm start", but I would like this to occur automatically.

Any suggestions?

---

### Post by ibjsb4 on 2014-01-10
Ubuntu 10.04 has reached end of life and no longer supported, but this looks like the answer ..

[http://ubuntuforums.org/showthread.php?t=1385455&p=8692825#post8692825](http://ubuntuforums.org/showthread.php?t=1385455&p=8692825#post8692825)

Ubuntu 12.04 has a desktop that looks like your 10.04 desktop if thats what holding you back.

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by sundays211 on 2014-01-10
I'm running 12.04 currently (probably should have mentioned that). I haven't logged into these forums for ages, so that's why it's still showing my old distrobution.    If it helps, the following package upgrade occured yesterday: gdm (3.0.4-ubuntu15.1 to 3.0.4-ubuntu15.2)

---

### Post by ibjsb4 on 2014-01-10
Ubuntu 12.04 uses lightdm as a display manager :confused:

Try this:

```
sudo dpkg-reconfigure gdm
```

---

### Post by 316479 on 2014-01-10
> **sundays211 said:**
> Hi,

Following the update to GDM today, the display manager is not launching automatically when I start my computer. Instead, I am thrown into a text shell. I am able to then start GDM by typing "sudo gdm start", but I would like this to occur automatically.

Any suggestions?

It's a problem with  /etc/init/gdm.conf

It has a dependency on plymouth that isn't always appropriate.

In /etc/init/gdm.conf  remove or comment out the line

```
and plymouth-ready)
```

replace it with    ```
 ) 
```

---

### Post by sundays211 on 2014-01-10
Unfortunately, the solution suggested by [**[COLOR=#000000]316479[/COLOR]**]("http://ubuntuforums.org/member.php?u=880845") still doesn't appear to have fixed the issue...   

I switched to gdm after an issue with lightdm. Now, if I try starting with lightdm (via "sudo lightdm start"), I am only able to log into the guest account, attempting to log into my own account causes a fallback to the login screen, and I am unable to shutdown my computer (without performing a force shutdown by holding the power button).  

Also, does anyone know why I'm unable to have line breaks in my reply here? Every time I submit a post, all the line breaks get removed. (EDIT: Seems to be an issue with the manual editor. Enabling javascript for the site fixed it)

---

### Post by sundays211 on 2014-01-13
I've solved the issue, though the solution is more of a work-around than a proper solution.

I've added the following line to /etc/rc.local
```
gdm start
```

I'm still not sure why there is no call being made to start gdm (or any display manager) through the normal startup, so if anyone can help me find out why this is not occurring, please reply :)

Marking this as solved though, since the work-around does launch the display manager.

---

