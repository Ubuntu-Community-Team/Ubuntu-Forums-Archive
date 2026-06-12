---
title: "[SOLVED] Oops, just lost the GUI"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bwallum on 2008-10-19
I have just messed up a 32bit box by removing some updates that were 'partial'. That is they were greyed out and I couldn't check the box. One might have been a kernel file.

I have the command line. I have tried to apt-get update but I am still without a GUI.

Any help on recovery would be gratefully appreciated.

Regards
Bob

---

### Post by bwallum on 2008-10-20
...and got it back.Phew.

I had managed to remove the entire X environment so no gui whatsoever. This is how I recovered.

When the system boots it leaves you with a command line. Use your normal log on and password then make sure your system is up to date with```
sudo apt-get update
```Then reinstall your desktop with ```
sudo apt-get install ubuntu-desktop
```Note that this is for Ubuntu. If you use XUbuntu or KUbuntu then install xubuntu-desktop and kubuntu-desktop respectively

---

