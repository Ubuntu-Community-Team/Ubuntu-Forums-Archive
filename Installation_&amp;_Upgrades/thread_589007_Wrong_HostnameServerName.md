---
title: "Wrong Hostname/ServerName"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by dbrooke on 2007-10-23
hello, upon install, I listed a servername or hostname. Well, I changed this name during configuration because I decided that I didn't want to register that name... ie. host.domain.com.

I am a bit confused by all the host/server name enteries upon install of the server... anyway, I settled upon a name ;-)  and have been trying to find all the old names to change them.  Currently, I did a:

grep -nr 'dbrooke' /

(because "dbrooke" is in the name) ..however, it is still finding ;)  )  perhaps I should not have done this from the root?? 

Anyway, is there some obvious places that a noob should check to change them.... as all my apps seem to be having a h3ll of a time finding a qualified domain name  <-- go figure.

TIA!

Donovan

---

### Post by ezak on 2007-10-24
to change your hostname you would simply type in:

sudo hostname blah.examplehostname.com

Then to check it is correct type in:

hostname 

So it will show you what the hostname for the system is. ;)

---

### Post by dbrooke on 2007-10-28
thanks Ezak!

Donovan

---

### Post by iceportal on 2008-02-20
Bump!

I'm having trouble too!

I've got my server set up, and the hostname is [www.z3row3b.com](www.z3row3b.com).

When I tried to set up the system though, it made the full hostname:

[www.z3row3b.com.z3row3b.com](www.z3row3b.com.z3row3b.com)

because z3row3b.com was the domain!

So now, my SMTP server thinks the proper domain is [www.z3row3b.com.z3row3b.com](www.z3row3b.com.z3row3b.com), and I can't send mail.

Any thoughts on how to fix it?

You can email me at ubuntu (at) gridrunners (dot) com if you can help me immediately... I need this fixed ASAP!

Thanks so much!

---

