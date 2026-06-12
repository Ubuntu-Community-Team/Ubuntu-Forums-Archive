---
title: "RDesktop &amp; FireFox Kiosk"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by rushinblue on 2007-10-26
Greetings to all!!! I am new to Ubuntu been using it for a month or so, really liking it. I want to customize an installation of it to do two things.

[LIST=1]
[*]FireFox
[*]RDesktop
[/LIST]

That's it, nothing else. How can I achieve this?

Thanks

---

### Post by Pumalite on 2007-10-26
[http://www.rdesktop.org/](http://www.rdesktop.org/)
(I imagine you want to run a Server?)

---

### Post by BlindFate on 2007-10-26
You could uninstall pretty much everything, I suppose. 


Or maybe if your users are not very savvy you could simply delete the panels and all unwanted shortcuts from the desktop. I'm unsure as to if it is possible to set permissions so that only root can run (specific) programs or not.

---

### Post by InTheSand on 2007-10-26
> **rushinblue said:**
> ...I want to customize an installation of it to do two things....

Ubuntu's probably overkill for this!

I presume you want to turn a PC into a web kiosk and effectively a thin client for an MSTS environment...

Have a look at something with a much smaller footprint (and less features and therefore much reduced startup / shutdown times) such as DSL - [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

I use it to recycle old knackered PCs (ones that have no chance of running Ubuntu!) with as little as 32Mb and a Pentium 133 to turn them into auto-starting thin clients running rdesktop.

 - Ali

---

### Post by rushinblue on 2007-10-29
Thanks for the pointers.
I have one problem. Ubuntu is picking up the NICs but DSL & thinstation do not.

---

### Post by rushinblue on 2007-10-30
Additionally, D*** Small Linux, isnt the most suitable name for a business. Are there any others?

---

### Post by airwaves on 2007-10-31
rushinblu:

Two Items. First, DamnSmallLinux is based on the 2.4 kernel, so many newer NICs won't function with it. A good workaround is DSL-N, DSL's bigger brother... 

[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)

Second, when properly configured the name of the distribution is only visible during bootup... and even then it only shows "DSL". If "damn small" was plastered all over the screen and couldn't be removed... well, then I could see that as a viable argument. In this instance there's zero reason why  DSL can't be adapted to what you're trying to do.... I wouldn't be concerned in the least about the name being unprofessional. I quite regularly build custom DSL distributions which are used in very high profile Fortune 500 companies and major public events... works like a charm.

---

### Post by timcredible on 2007-10-31
if you're looking for a kiosk solution, and you have network access, you might want to use a thin client like PXES or 2X products.  I have a small how-to about thin clients at [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=22&Itemid=29](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=22&Itemid=29)

---

### Post by rushinblue on 2007-11-20
Ok, I am also wanting to use this as more than just a kiosk now. I would like to connect an old PC to a new virtual machine. I have tried playing with ThinStation, but I dont think the hardware is compatible, because I just cannot get it to work at all.

---

