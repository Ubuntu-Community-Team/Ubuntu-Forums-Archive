---
title: "No graphics session after upgrading from 16.04 to 17.10"
date: 2018-06-09
forum: Installation &amp; Upgrades
---

### Post by Fausto Arinos Barbuto on 2018-06-09
Hello,

I've just upgraded one of my computers from 16.04 to 17.10. It wall went fine, but now I cannot start a graphics session. The desktop asks the password, I enter it, and after a few
seconds "thinking", the login screen returns to the starting point with no error messages (if I intentionally enter a _wrong_ password it returns a wrong-password message).

The funny thing is that I can start a graphics session if I open a text session (with CTRL+ALT+F1) and execute the "startx" command. But that's not acceptable. I want the system back to what it was.

Should this helps, here's the result of "lspci | grep VGA":

01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)

Many thanks in advance for any help.

Fausto

---

