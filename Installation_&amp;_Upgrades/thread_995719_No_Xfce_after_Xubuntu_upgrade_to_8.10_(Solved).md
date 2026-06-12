---
title: "No Xfce after Xubuntu upgrade to 8.10 (Solved)"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by Jored on 2008-11-28
Just in case it may help others with the same problem.

After an error free upgrade to 8.10 from 8.04, the system would only boot into terminal mode. 

The Xfce desktop had been removed by the upgrade process. No Gnome was installed either.

To reinstall the Xfce desktop, proceed as follows:

**Adding Xubuntu to an existing Ubuntu/Kubuntu**

Paste in this command in the terminal:

[HTML]sudo aptitude update && sudo aptitude install xubuntu-desktop[/HTML]

To use Xfce after you've installed it:

   1. Log out.
   2. Under Options in login window, select Startup Session-->Xfce Session.
   3. Confirm Xfce as default session
   4. Log back in again. 

Btw, for easons unknown, aMSN was also removed durint the upgrade process :confused:

---

