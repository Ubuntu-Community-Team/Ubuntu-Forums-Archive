---
title: "Dependency problems when installing program"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by river226 on 2011-08-28
I am trying to install SloMoVideo on my computer, and have been running into issues with dependencies. I have managed to grab everything that I need, but then run into an issue during install. The package i am having issues with is Nvidia-current which from what i can tell is installed. 

I run a modest system over all, with ATI graphics which may be messing stuff up. But the Nvidia installers seem fine installing along side ATI's drivers so i am not sure what to make of it. Any advice?

[IMG]http://dl.dropbox.com/u/129650/Screenshot.png[/IMG]

---

### Post by Frogs Hair on 2011-08-28
It looks like the program uses Nvidia drivers as part of the dependencies and you have an ATI card . Do you have a link to the software because it is not in the 11.04 software center .

---

### Post by LifeBringer on 2011-08-29
The site says that it's graphic cards neutral, but the dependencies are old. So much for being an ETH Zurich thesis.

---

### Post by Hakunka-Matata on 2011-08-29
river226:  I notice you're on 11.04 64bit.  I know some program's dependencies for 64bit vs. 32bit are different.  Maybe you'd like to try to install it on a 32 bit Architecture OS as a test?
**EDIT:  **I just noticed it's a 64bit.deb, sorry

After a bit more investigating, I downloaded the .deb, software center opened automatically as it does when downloading .deb, and showed the dependency problem straight out of the gate.......... see attached.

**EDIT: (again)**, the list goes on, after installing the lib shown in the .png, I tried once again to download and install the application, more dependency problems, and looking into those dependencies i see references to 10.04, and other earlier Releases of Ubuntu. My guess is that the package will be a big hassle to get running in natty, I'll try it on 10.10, or 10.04 later, and see if that works.

---

