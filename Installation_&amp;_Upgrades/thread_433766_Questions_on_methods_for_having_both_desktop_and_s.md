---
title: "Questions on methods for having both desktop and server installed"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Pro_D on 2007-05-05
Hello, brand new ubuntu user here (well I have been eyeing it for some time).

I was wonder how best to go about installing ubuntu desktop on an ubuntu server.

Ideas:

1> install desktop onto server - seems a bit off and seems like it could kill files.

2> use apt-get (sudo apt-get install desktop-ubuntu) to install the desktop environment -bandwidth heavy and I already have the desktop disk burned (ISP is super flaky right now).

3> maybe modify the sources of apt to include the desktop disk and then install with apt- I don't know if this would work or what lines to add in (I can edit around ok).

I already have figured out (I think) what to do to configure things once that is done, just kinda stuck here and googling about didn't help much with this particular question.

---

### Post by zvacet on 2007-05-05
If you allready have desktop installed go to the **synaptic>edit>mark by task** and select what you want (dns server, LAMP).

---

### Post by Pro_D on 2007-05-05
I am actually starting on the server end of things...  I forgot to mention 6.06 LTS so that I can get updates for the server for a while.  Our win2k server (which I am trying to retire) has been running the same install of 2k since around when win2k came out :), granted it hasn't been called on to do much.

Gonna experiment more tomorrow, got pulled away from computers for the day unexpectedly...  Might try going with the above suggestion if I think I can get everything going from scratch (the server install took care of a few things automatically).

---

