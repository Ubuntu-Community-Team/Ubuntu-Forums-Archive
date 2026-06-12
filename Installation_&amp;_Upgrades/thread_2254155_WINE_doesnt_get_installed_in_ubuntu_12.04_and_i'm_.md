---
title: "WINE doesnt get installed in ubuntu 12.04 and i'm stuck with dependency error"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by aanchal2 on 2014-11-25
**i get following information in the error message when i try to install WINE from ubuntu software center:**
Package dependencies cannot be resolved     This error could be caused  by required additional software packages which are missing or not  installable. Furthermore there could be a conflict between software  packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.5 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.7 is to be installed
         Depends: wine1.4-amd64  1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed
         Depends: wine1.4-i386  1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package





[B]any idea on how to solve the problem?
any help is much appreciated

Aanchal[/B]

---

### Post by carlwsnyder on 2014-11-25
Have you tried these commands from a terminal window:```
sudo apt-get -f install
``` to see if you can resolve the dependency issue automatically?

---

### Post by aanchal2 on 2014-11-26
i've tried that and it gives a message stating: 0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
what am i supposed to do now?

---

### Post by carlwsnyder on 2014-11-26
Have you actually had problems operating under WINE?  According to your error messages, you actually meet the requirements for the dependencies, so the problem would be in a package which may not be in the repositories.

Is there a reason you did not install WINE before Ubuntu 14.04 was released?  WINE seems to be supported mainly in 14.04 Trusty Tahr for the latest releases, which may be part of the problem reported.

Yes, 12.04 is supported for its own packages, but third party packages may not continue support.

---

