---
title: "Online Update to Gutsy hangs during installing step ..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2007-10-18
Just ran the update-manager and downloading the packages worked fine.
Halfway through the "Installing the upgrades" step, things have stopped to proceed. I had the Terminal window of the update manager open and the last thing that was shown is:
   Running mktexlsr. This may take a while. ... done

Now the update manager GUI does not react to clicks for opening/closing the terminal section any more.

top shows that kpsewhich is using 100% CPU and is now running for more than 15 minutes, using up more than 65MB memory, which is constantly increasing.

That is not exactly a nice upgrade experience :sad:

What am I supposed to do now? Do I have to expect that my whole installation will be damaged or gone?

---

### Post by johann_p on 2007-10-18
Well I killed the kpsewhich process only to find out that it will be started many more times (this happens during the installation of several language-specific texlive packages).

So I did "chmod 444 /usr/bin/kpsewhich" to prevent the program from getting started in all the other post-installation scripts and that helped to skip that part and get the update process going again.

---

