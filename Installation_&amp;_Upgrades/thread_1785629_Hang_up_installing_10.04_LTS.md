---
title: "Hang up installing 10.04 LTS"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by Oryan02 on 2011-06-18
I'm trying to install 10.04 LTS and everything goes great until I get to step 2 of 7 after clicking my time zone it just hangs up.  I had no problems installing using the same live disk earlier today on another cpu, I even tried another image to see if that was the problem.  Installing 11.04 goes great too on the same cpu.  Any ideas?

Edit:  I should of mentioned this earlier, but I also can run directly from the cd.  The only issue is when I try to install it.

---

### Post by MAFoElffen on 2011-06-18
> **Oryan02 said:**
> I'm trying to install 10.04 LTS and everything goes great until I get to step 2 of 7 after clicking my time zone it just hangs up.  I had no problems installing using the same live disk earlier today on another cpu, I even tried another image to see if that was the problem.  Installing 11.04 goes great too on the same cpu.  Any ideas?

Edit:  I should of mentioned this earlier, but I also can run directly from the cd.  The only issue is when I try to install it.
Do you have a working internet connection when you run from the LiveCD?  The Internet "time sone check" process would be the first time the script makes a call to the Internet.  Which would imply either a NIC, router or DNS problem.  Just an observation.

---

### Post by jerrrys on 2011-06-18
if you have 11o4 working, stick with it. there are lots of changes going on and you will be in on them with 11o4.

but if you really want to go with 10o4, give the "alternate install cd" a try.

---

### Post by Oryan02 on 2011-06-18
> **MAFoElffen said:**
> Do you have a working internet connection when you run from the LiveCD?  The Internet "time sone check" process would be the first time the script makes a call to the Internet.  Which would imply either a NIC, router or DNS problem.  Just an observation.

Yes I have a good connection.  When I run the live cd I'm able to use the termal to ping and update the server with no problem.  Also tried to installing while the live cd is up and running after I made sure the connection to the sever was good, still hanging up...

---

### Post by Oryan02 on 2011-06-18
> **jerrrys said:**
> if you have 11o4 working, stick with it. there are lots of changes going on and you will be in on them with 11o4.

but if you really want to go with 10o4, give the "alternate install cd" a try.

I would like to stick with 11.04 but there is no support for the ELDK for embedded for 11.04.  [http://www.denx.de/wiki/view/DULG/ELDKSupportedHostSystems](http://www.denx.de/wiki/view/DULG/ELDKSupportedHostSystems)
I'll try the alt. cd, hopefully that will help.

Edit:  Found out the issue.  Turns out when I installed 11.04 it created an extra partition, so I ended up having 2 partitions for 11.04 (but the second was unbootable).  This isn't a common issue is it?  Killed the second partition and 10.04 installed fine, so now i've got a duel boot 11.04 and 10.04 for my embedded work.

---

