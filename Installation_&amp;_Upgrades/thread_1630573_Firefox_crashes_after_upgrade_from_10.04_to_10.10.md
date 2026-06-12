---
title: "Firefox crashes after upgrade from 10.04 to 10.10"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by Odense on 2010-11-25
After I updated the Ubuntu on my Lenovo S10 netbook from 10.04 to 10.10 Firefox crashes when I try to open it. I tried uninstalling it and installing it again (with the add / remove software function) so I thought I would have a "plug-in free" Firefox - but it still crashes.  At the moment I am using Chromium - but I want Firefox back - so what do I do ?

---

### Post by Rubi1200 on 2010-11-25
Hi,
take a look here for some help:
[http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

(courtesy of forum member lovinglinux)

---

### Post by benbayer on 2010-11-27
I had this exact problem.  I tried sudo firefox as the link describes; that didn't help.  The terminal mentioned something about attempting to load libmoon.  That turned out to be Moonlight 2.0.  Uninstalling Moonlight 2.0 allowed Firefox to start.

---

### Post by Odense on 2010-11-27
Hmm - I am still not "nerd" enough to follow that procedure.
I cannot find ~/.mozilla/ and ~/.mozilla/firefox when I search for them.

I have not made any modifications to where Ubuntu installs the software so surely it must be possible to tell me the path where I should go and what command I should use to see the owner of the files ?

I would also like to know the full path where I should be when starting Firefox with SUDO ?

---

### Post by David Oxland on 2011-01-07
> **benbayer said:**
> I had this exact problem.  I tried sudo firefox as the link describes; that didn't help.  The terminal mentioned something about attempting to load libmoon.  That turned out to be Moonlight 2.0.  Uninstalling Moonlight 2.0 allowed Firefox to start.

Solved for me in the same way for me. Thanks!
No great loss except that I cannot open [http://crdatlas.ca/](http://crdatlas.ca/) because it calls for starlight or moonlight under ubuntu/linux

---

### Post by Odense on 2011-02-11
It worked for me too with a bit more effort
:P

---

