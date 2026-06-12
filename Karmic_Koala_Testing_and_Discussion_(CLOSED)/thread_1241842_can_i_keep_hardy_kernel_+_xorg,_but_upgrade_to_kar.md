---
title: "can i keep hardy kernel + xorg, but upgrade to karmic software???"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-08-16
yea so i asked this questino before, or a similiar one
but the answer didnt work

so i have to maintain the following kernel and X version
 2.6.24-16-generic and X.Org X Server 1.4.0.90 respectively.

so ye
the software is old tho, i want the new cheese and the new nautilus with the sharing and i just want the new software in gnome
and seeing as i cant find a maintained official "gnome ppa"

can i put the karmic or jaunty reps on  the sources.list
and just upgrade what i feel like?

is that possible?

---

### Post by psyke83 on 2009-08-16
Yes, you can keep running the older kernel, but if any software (particularly system daemons) in Karmic rely on new infrastructure introduced in newer kernels, you'll have problems.

You can't keep the older Xorg server, and picking and choosing what software to install from Karmic will most likely cause dependency issues (think: RPM hell). Even if you get the packages installed, things will break - most software compiled with dynamic libraries, which will introduce instability for the older software on your system that expects to use the older version of those libraries.

---

### Post by nanog on 2009-08-16
> can i put the karmic or jaunty reps on the sources.list
and just upgrade what i feel like?

No need to perform a full upgrade -- just try installing the desired software. Dependency hell is a lot rarer than you would think and removing the offending package typically fixes the problem. Once you have a working package immediately pin it. 

The worst thing that can happen is breakage of apt or critical gnu libraries but this is very rare. Even these things are fixable by hacking var/lib/dpkg and/or chrooting in. If you have no idea what I am talking about then you should ignore everything I just said and just perform a full upgrade at the appropriate time.

---

### Post by jocko on 2009-08-16
> **puccaso said:**
> [COLOR=Red]yea so i asked this questino before, or a similiar one
but the answer didnt work[/COLOR]

so i have to maintain the following kernel and X version
 2.6.24-16-generic and X.Org X Server 1.4.0.90 respectively.

so ye
the software is old tho, i want the new cheese and the new nautilus with the sharing and i just want the new software in gnome
and seeing as i cant find a maintained official "gnome ppa"

can i put the karmic or jaunty reps on  the sources.list
and just upgrade what i feel like?

is that possible?

So, let's see if the answer works this time, then.

Is it possible?
-Yes.
Is it going to eat your kitten?
-Yes, unless you *really* know which packages are ok to upgrade and which to leave alone, and remove the new repos as soon as you upgraded the safe packages... Be prepared for breakage. I'm sure there will be dependencies that would force you to upgrade a lot of very important libraries, which would break a lot of the applications that you don't upgrade, because they are not compatible with the newer libraries...

---

