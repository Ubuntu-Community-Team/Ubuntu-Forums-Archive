---
title: "How do I resume a package install interrupted?"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by jqball2u on 2008-04-16
I was using the Synaptic Package Manager to install some programs, left it to download & went to work.  When I got home, I saw a dialog box that required me to click it to continue installing the program and when I clicked on it, nothing happened, so, I clicked the [X] button on the upper rignt hand corner of the window to get out of the ?frozen? application but the SPM just kept on as if waiting for that app. to tell it to continue installing the other applications.

Is the a command-line command to tell it to finish installing those apps or do I have to re-download them all?:popcorn:

Thanks,
QBall

---

### Post by Pumalite on 2008-04-16
Post the output of:
sudo apt-get update
sudo apt-get upgrade

---

### Post by schiznik on 2008-04-16
you probably need to run:```
dpkg --configure -a
```This will finish off whatever dpkg/apt was up to when it was interrupted.

---

### Post by Pumalite on 2008-04-16
You might need:
sudo apt-get -f install

---

### Post by jqball2u on 2008-04-16
Nope....neither one did it, I guess I'll have to re-download them and, hopefully, they will install?

NOW, I have a problem with Firefox locking up! (SIGH)

I had to reinstall unbuntu because the partitions weren't the right size, then I did an update/upgrade, now Firefox locks up!?:confused:

Thanks,
QBall

---

