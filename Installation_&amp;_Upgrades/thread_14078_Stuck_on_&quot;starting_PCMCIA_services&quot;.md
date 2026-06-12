---
title: "Stuck on &quot;starting PCMCIA services&quot;"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by Firebar on 2005-02-04
Hi,

Hoping someone can help...

I've installed Ubuntu, install went fine, peachy infact.  BUT, when it comes to boot up, my laptop (Toshiba M60 centrino) gets stuck on "Starting PCMCIA services".  This isnt the only distribution this happens on, it happens in gentoo & SUSE 9.2 aswell.  This makes me think that this must be some kind of bug with the PCMCIA module used by the kernal or something (excuse me, I know nothing of Linux  :-P ).

Basically I want to boot into Ubuntu some time this millenium, and I was wondering whether anyone could tell me how I can disable the PCMCIA services from starting, either at the install stage, or after.  Bear in mind I cant even get into runlevel 2.

Any help would be much appreciated.

---

### Post by Firebar on 2005-02-05
Please, someone must be able to help?

---

### Post by nadador on 2005-02-11
This is a problem with some laptops, including Toshiba.

Use the:
              hw-detect/start_pmcia=false

boot option (read help screen F7)

Good luck!

---

