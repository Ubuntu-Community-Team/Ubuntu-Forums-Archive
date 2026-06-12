---
title: "Ubuntu 14.04 Fresh Install for Upgrade from Ubuntu 13.10"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-18
hello i am muhammad ahmad mujtaba

and i am using Ubuntu 13.10 right now at it's full peak.
I have installed fresh Ubuntu 14.04 LTS on another partition which will be my primary operating system choice in coming days.

Before, i switch completely to Ubuntu 14.04 i have a scheme to follow and that scheme needs some advice:

Scheme is:

I have installed bunch of programs over Ubuntu 13.10 i don't want to install them again over Ubuntu 14.04 LTS.

Therefore, if i make backup of following folders 

/bin
/usr/bin
/opt

which mostly contains all softwares of my OS and restore them over Ubuntu 14.04 LTS would that be okay?

Is there are any other folders that should i also backup then tell me please.
Moreover what else i should be backing up? instead of my /home/user-name/... [documents, downloads,music etc]

thanks in advance!

---

### Post by monkeybrain20122 on 2014-04-18
No it won't be OK if you plan to copy them over to 14.04. Software that compiled against 13.10 libraries may not work with 14.04. It is not just the binaries.

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-18
i don't have such softwares, i didn't compile any softwares before making backup! if i get any problems , sudo apt-get clean ; sudo apt-get autoclean; sudo aptitude remove ; should done the job of uninstalling incomplete, bad packages so that i may reinstall them but that should be very rare case!

---

### Post by monkeybrain20122 on 2014-04-18
All applications are compiled before you can run them. You may not have compiled them yourself, but they are compiled by someone else, say the Ubuntu maintainers. They require a whole support structure to work (e.g correct versions of libraries).

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-20
I got it thanks !

---

