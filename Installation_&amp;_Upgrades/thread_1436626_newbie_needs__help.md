---
title: "newbie needs  help"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by tazmania123 on 2010-03-22
i've just installed ubuntu 9.04 (had the disc from before) and i'm upgrading to 9.10 of course but i have a question.

how do i check that i have the latest drivers installed for everything in my laptop? i'm the kind of person that has that nagging feeling in the back of my head telling me that everything isn't installed perfectly and i need to install my drivers properly (or at least ask). any help with this?

---

### Post by 2hot6ft2 on 2010-03-22
> **tazmania123 said:**
> i've just installed ubuntu 9.04 (had the disc from before) and i'm upgrading to 9.10 of course but i have a question.

how do i check that i have the latest drivers installed for everything in my laptop? i'm the kind of person that has that nagging feeling in the back of my head telling me that everything isn't installed perfectly and i need to install my drivers properly (or at least ask). any help with this?
If you've just installed it why not download the 9.10 version or the 10.04 beta and do a fresh install?
Otherwise I would say just do it and if there are any issues it may clear them up but a fresh install is almost always better than an upgrade.

You may even have newer drivers available after the upgrade and updates then check System > Administration > Hardware Drivers

It really wont do you any good to check the drivers first that I know of. If everything works then they are up to date for the OS you have installed.

---

### Post by tazmania123 on 2010-03-22
what difference does it make installing it from scratch or just upgrading it anyway? i just didn't feel like redownloading the entire thing and just went with what i had. i just upgraded and it's working fine

---

### Post by aviedw on 2010-03-22
Clean installs are always better than upgrades. If your 9.4 is a new install, and u do plan on using the next version i would just download the 9.10 iso, burn and install it. If you do choose to upgrade, maybe here have voices many issues with their system after the upgrade. Either the sound or the network card or what ever might not work right. Sometimes are taken out or added when you upgrade. Dont necessary take our word for it do you research, or in fact try it out so that way you will have first had knowledge.

---

### Post by tazmania123 on 2010-03-22
alright thanks for the help, just one last question.

how do i check for overall updates for all software/anything i have? i can't remember the way i used to do it a while ago

---

### Post by gogadan on 2010-03-23
it should be 
  system>administration>update manager

thats the only way i know i be intreged to hear more as i am also a noob :)

---

### Post by jimmers on 2010-03-23
Taken from a tutorial in Linux Format:- Master your Packages,
The first thing you should type is simply:** sudo apt-get update**, this forces apt-get to update its information about available packages, using details gleaned from the **sources.list** file.
Its important that you do this before you go any further, so as to ensure that you have the latest information about the most update packages, once apt-get has finished processing, you can issue the command;
**sudo apt-get upgrade**.
This will download any newer versions of currently installed applications, along with their dependencies.  It then does the necessary.

No harm in trying.

---

