---
title: "Edgy Eft RC1 and Firefox RC3"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by Nigel Eke on 2006-10-21
Hi

I have installed Edgy Eft - clean install - but now have problems with Firefox.

If I navigate to [http://www.google.com/](http://www.google.com/) (for example) I get the Firefox error page 'Unable to connect'.  To eliminate DNS issues I also tried the TCP/IP address directly and I also get the same problem.

Also I can ping [www.google.com](www.google.com).  (The ping itself times out, but the name is translated to the TCP/IP address).

Have searched forums, but found nothing related to this.  As a bit of a noobie not sure what to look for next...

Any help appreciated.

Many thanks,

Nigel

---

### Post by Nigel Eke on 2006-10-21
Forgot to mention - The clean install also has further updates applied; I have also tried *sudo aptitude reinstall firefox*, but to no avail.

---

### Post by Nigel Eke on 2006-10-25
Resolved.  I wondered why there hadn't been any similar reports.
My bad - I'd set the wrong Gateway address on the n/w card.  Doh!
:oops:

---

