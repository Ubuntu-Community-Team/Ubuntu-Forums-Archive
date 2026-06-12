---
title: "Recent CUPS upgrade killed printing..."
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by CD Baric on 2008-04-15
After the recent automatic CUPS upgrade my printing stopped working.

Ubuntu 7.10
AMD Athlon 2400+ 1gig memory
HP 1200 Laserjet printer connected to LPT1

Printing worked perfectly prior to the upgrade over the weekend.

After the upgrade submitting a print job produces zero effect except endless error messages:

/var/log/messages
----
Apr 14 18:12:56 black parport0: INFO: open print channel failed; will retry in 30 seconds... 
Apr 14 18:13:12 black kernel: [ 1038.048000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Apr 14 18:13:12 black kernel: [ 1038.124000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Apr 14 18:13:12 black kernel: [ 1038.124000] NFSD: starting 90-second grace period
Apr 14 18:13:26 black parport0: INFO: open print channel failed; will retry in 30 seconds... 
Apr 14 18:13:56 black parport0: INFO: open print channel failed; will retry in 30 seconds... 
Apr 14 18:14:56 black last message repeated 2 times
Apr 14 18:15:56 black last message repeated 2 times
Apr 14 18:16:56 black last message repeated 2 times
Apr 14 18:17:56 black last message repeated 2 times
----

I tried uninstalling and reinstalling CUPS but no joy.

Finally I did a complete re-install of 7.10 and still no joy - same errors.

Printing works perfectly with XP and SLAX 6.04 Live CD - it is definitely a Ubuntu problem.

So, I do I fix this?

Bar

---

### Post by KuriKai on 2008-04-15
My printer also stopped working after the last CUPS updates (i'm also on ubuntu 7.10)
It thinks the printer is turned off even though it is on.
My printer is an "HP Photosmart C4100 series"

---

### Post by ACGarland on 2008-04-17
May as well chime in... I'm using an HP Laserjet 1320n.  I'm having 'mixed results' with printing. Small simple pages print just fine. But when printing PDF, even a simple 2-page document, from any application (KPDF, Kghostview, document viewer) the printer just blinks forever--as if it is downloading the file--and the log shows printer time outs:

ERROR: check device; will retry in 30 seconds... 
ERROR: check device; will retry in 30 seconds... 
ERROR: check device; will retry in 30 seconds...

The status of the HP laserjet itself shows that "the print job is continuing."

I'm using Ubuntu 7.1 on a Dell Inspiron 1420n with CUPS 1.3.2.

There was no upgrade involved here, so perhaps this is a different problem.  In any event, it is very frustrating not to be able to print basic PDF.

---

