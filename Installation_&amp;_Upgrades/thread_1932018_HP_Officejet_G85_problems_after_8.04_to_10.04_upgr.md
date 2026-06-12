---
title: "HP Officejet G85 problems after 8.04 to 10.04 upgrade"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by pbj1000 on 2012-02-26
I'm posting this in case others run across this problem.

After upgrading my system from 8.04 to 10.04, I couldn't get my parport HP Officejet G85 to print any more than 1 line every minute or so.  I didn't know if it was that the parport card I bought with the new mobo didn't work on 10.04 or something else.

I decided to toss the parport and connected the printer to USB with a Belkin cable.  Now jobs appeared to be queued and run but they disappeared without running.

I finally found a couple of posts that solved the problem.  To summarize, you have to install hplip-cups, select it as the PPD, and power-cycle the printer.  Scanning works after this too.

See:

[<http://www.magnussuther.se/2010/05/01/fixing-an-printing-issue-with-ubuntu-10-04-and-d1660/]("http://www.magnussuther.se/2010/05/01/fixing-an-printing-issue-with-ubuntu-10-04-and-d1660/")>

and

[<https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/576491>]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/576491")

---

