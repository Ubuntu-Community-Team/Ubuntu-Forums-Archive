---
title: "Why CD needed when install"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by Sladi on 2007-05-19
Why is the CD needed sometimes when installing programs? I use Xubuntu. 

Regards, 
Sladi

---

### Post by Metacarpal on 2007-05-19
Open up Synaptic, then go to your Settings menu > Repositories.

I'm guessing that you have an entry under "Installable from CD-ROM/DVD".  If you do, remove it.

The system's logic is that, if you have your installation CD and you're trying to install a package present on that CD, then it's faster to spin up the CD-ROM than to download new packages.  If you remove the CD-ROM entry from your repositories, it will instead look for the packages in the Ubuntu online repos.

---

### Post by Sladi on 2007-05-19
Thank you very much Metacarpal! :) 

Regards, 
Sladi

---

