---
title: "dpkg --configure -a"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by chrisjgillis on 2008-07-04
This is my first time using Ubuntu. I had installed and run an update. I had over 120 updates to perform however, when I try to install the updates I receive an error which reads run 'dpkg --configure -a" to correct the problem E:_cache->open() failed, please report. How do I fix?

---

### Post by Pumalite on 2008-07-04
In the Terminal:
sudo dpkg --configure -a

---

### Post by VMC on 2008-07-04
Do as Pumalite suggested. What version of ubuntu did you download? There is a newer version with many updates included : [Ubuntu 8.04.1 LTS]("http://releases.ubuntu.com/8.04.1/")

---

### Post by chrisjgillis on 2008-07-05
I did use the mentioned version. I downloaded from web just last week.

---

### Post by Pumalite on 2008-07-05
Are you upgrading from Alternate or are you preparing for a clean install?

---

### Post by chrisjgillis on 2008-07-07
I did a clean install. Should I just try it again?

---

### Post by chrisjgillis on 2008-07-07
I did a new install, should I try again?

---

### Post by Bubba64 on 2008-07-07
If you ran the command it should have finished the install but not the upgrade packages generally if it is now ready for the 120 upgrade packages generally you should be okay. Sometimes in a new install or a upgrade a glitch can cause the need of this command, it generally doesn't mean a failure.

---

