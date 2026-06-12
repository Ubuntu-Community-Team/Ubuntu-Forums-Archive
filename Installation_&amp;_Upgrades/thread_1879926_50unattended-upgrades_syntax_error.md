---
title: "50unattended-upgrades syntax error"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by bpb_21 on 2011-11-12
I'm having an issue with enabling unattended upgrades on a Ubuntu 11.10 server.  I edit the file to taste, as in [https://help.ubuntu.com/11.10/serverguide/C/automatic-updates.html](https://help.ubuntu.com/11.10/serverguide/C/automatic-updates.html)

When I go to install an additional (and I think unrelated) package for the server, I get the error message E: Syntax error /etc/apt/apt.conf.d/50unattended-upgrades:21: Extra junk after value

Looking in the 50unattended-upgrades file, line 21 has:
Unattended-Upgrade::AutoFixInterruptedDpkg "true";

If I remove the semicolon at the end, and do so for other uncommented lines in 50unattended-upgrades, I finally end up with this error:
E: Suntax error /etc/apt/apt.conf.d/50unattended-upgrades:51: Extra junk at end of file

Well, there's nothing at the end of the file except for one blank space.  So I'm not sure how to get rid of this error.  It pops up when I do anything with apt-get.

Any help, always appreciated!

(In fact, if I uncomment anything in the 50unattended-upgrades file it gives an error about extra junk at end of file.)

---

