---
title: "stuff missing after upgrade to 20.04"
date: 2020-10-19
forum: Installation &amp; Upgrades
---

### Post by jgw on 2020-10-19
I have notice that there is now stuff missing.  The software updater, for instance, goes brings up the software and updates but software and updates no longer shows any ppa's (all gone).  then there is the problem with the ubuntu software thing.  That went away on one of my machines.  I reinstalled it but now its apparently gnome software.  I checked a machine with it still on (and updated to 20.04) and the software offered looks to be the same.  There is some other stuff as well (can't remember).  The strange thing is that everything doesn't seem to be the same on every machine anymore.  

Apparently ppa's are being handled differently now although I came across one site who says that isn't exactly true.  I also used to have a program.  I think it was called ypp (or something like that) that let one deal with the ppa stuff.  Its gone too. 

there there are waits.  if, for instance, I am in the terminal and want to do a "sudo apt update" it takes a minimum of 10 seconds before I am asked for a password.  This seems to happen with almost everything and happens even when nothing else is running.

I would be interested if anybody else is experience this stuff

Thank you..............

---

### Post by ajgreeny on 2020-10-19
When you upgrade from, for example 18.04 or 19.10 to 20.04 ***all PPA repos must be disabled or removed*** from software-sources.
If you do not do that yourself the upgrade system will do it for you; nothing has gone wrong, it is simply that you did not understand the need to do this.

Now you have upgraded to 20.04 you can restore all the PPAs you were using provided, of course, they are available for focal as they were for your previous version, which may not be the current situation.

---

### Post by crip720 on 2020-10-19
I have found the ubuntu software centre to be a bit wonky since it came out.  Thinking you upgraded from 18.04, maybe why PPAs were removed.  My upgrades been to next direct version and PPAs were only disabled, but this might depend on PPA.  The terminal waits do seem to be excessive for your system or any system.

---

### Post by jgw on 2020-10-20
thank you for the replies. 

Does anybody know if y-ppa-manager still works?

Here are a couple of links that may be of help in the new world of 20.04  Apparently, if you don't have ppa's your programs don't get updated.  I suspect this will probably be fixed in the future (hopefully?)

[https://www.ubuntubuzz.com/2020/08/list-of-ppas-for-ubuntu-2004-focal-fossa.html](https://www.ubuntubuzz.com/2020/08/list-of-ppas-for-ubuntu-2004-focal-fossa.html)
[https://itsfoss.com/ppa-guide/](https://itsfoss.com/ppa-guide/)

---

### Post by dragonfly41 on 2020-10-20
> [COLOR=#000000]Does anybody know if y-ppa-manager still works?[/COLOR]

Works O.K. here on Ubuntu 20.04.

---

### Post by grahammechanical on 2020-10-20
P.P.A. = Personal Package Archive. The person that produces the package archive has to convert it to the new release. And then continue maintaining the software in the archive. If the maintainer no longer wants to maintain their software then it will not be updated or upgraded anymore. We need to find out if the relevant developer has produced a P.P.A. for the new release and install that.

Regards

---

### Post by ActionParsnip on 2020-10-20
Ubuntu receives updates. I've no idea where you heard that PPAs are needed or software doesn't get updated but it's dead wrong

---

### Post by jgw on 2020-10-24
Apparently only certain things need a ppa to update and the rest is automatic.  I have no idea which need it but, I just installed two that apparently need it.  One was gimp and the other was y-ppa-manager.  I will mark this solved

---

