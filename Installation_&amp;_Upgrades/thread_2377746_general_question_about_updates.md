---
title: "general question about updates"
date: 2017-11-16
forum: Installation &amp; Upgrades
---

### Post by wfriedwaldgmail.c on 2017-11-16
after running Ubuntu on my little HP laptop for over a year, I still have some very basic questions about OS versions and updates.

* what's the easiest way to tell what OS version I am running?

* what is the best way to implement OS updates?  (it seems like a while ago, I would actually see the system automatically downloading and installing updates.  Now I have NOT seen that for many months.  Is it still making updates invisibly?  If not, how do I get it to update?)

* is there any way to "refresh" the OS? Of course, the updates would probably do that.  (something like the equivalent of a "safe" restart on a Mac system.) I notice that when playing videos, the system gets a little jittery and shaking occasionally, sort of a burp.  Am trying to fix that.  That's my main concern, since the primary thing I use this laptop for is powering video presentations.

thanks very much for any feedback!

w

---

### Post by ajgreeny on 2017-11-16
Normally the terminal command ```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
``` is what you would use.

I have amended it to give a bit more info by using ```
lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn
Description:	Ubuntu 16.04.3 LTS
Codename:	xenial
Desktop:	xubuntu
XubuntuXenial 4.4.0-98-generic x86_64
```
I have an alias for this longer command in my .bashrc file with ```
alias version='lsb_release -dc && echo "Desktop:	$DESKTOP_SESSION" && uname -mrn'
```

---

