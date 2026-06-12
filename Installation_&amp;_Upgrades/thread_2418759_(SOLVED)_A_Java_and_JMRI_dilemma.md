---
title: "(SOLVED) A Java and JMRI dilemma"
date: 2019-05-10
forum: Installation &amp; Upgrades
---

### Post by djsroknrol on 2019-05-10
I hope that I can find a solution to this with the forums’ help….

A little background:  The machine is a P3, 1.3MHz, 512 RAM and I’m trying to install Java on so I can run JMRI, a Digital Command Control program for model railroading via a serial port connection.

Yeah, Yeah…I know…get a newer computer, but I can’t really do it right now and besides, the computer is in great shape and I’m not doing anything on the net with it, just JMRI.  I put 8.04 Hardy on it and it runs ok, but I can’t install through the repositories as they’re closed for Hardy. I have 12.04 Precise and I could start a fresh install but a 7 year old version will more than likely have  closed repositories as well….I downloaded the tar.gz from Java.com and it seemed like it all went well, but when I run a ```
-version
``` it comes up “Java not found”.

When I try to start JMRI, I get “JMRI needs Java 1.6 or higher to run” so I know it didn’t install. I reinstalled Java again, but the results were the same. I installed JMRI and didn't have a problem. I don't know if maybe jre1.8 is "overload" for Hardy or something is missing somewhere.

Does anyone have any ideas as to what I might be doing wrong, or have a better idea as to how I can fix this?

---

### Post by Xian on 2019-05-10
Can you install by switching repos to  old-releases.ubuntu.com? 

See here for more details: [https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release?answertab=active#tab-top](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release?answertab=active#tab-top)

---

### Post by djsroknrol on 2019-05-12
I'll give it a try and report back...

---

### Post by djsroknrol on 2019-05-12
Well after trying multiple times to get the syntax right, I finally got the repositories straight and have Java on the computer...next to see if JMRI functions...thanks for your help Xian.

---

