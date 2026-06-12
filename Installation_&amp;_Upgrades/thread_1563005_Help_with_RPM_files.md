---
title: "Help with RPM files"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by om.rameshwar on 2010-08-28
Hello everyone,
 
I need some help in installin application from rpm packages... could u jus help me out wid this... thanks in advance :)

---

### Post by TBABill on 2010-08-28
Why are you trying to install from RPM? Debian based distros use .deb files. It is possible, but what is the application you are trying to install, is it in the repos already (or Medibuntu), etc.??

---

### Post by om.rameshwar on 2010-08-30
well am tryin to install MySQL... in the homepage i got rpm file of MySQL... so downloaded that... so need lil help wid tat... :)

---

### Post by AlphaLexman on 2010-08-30
The program 'alien' will convert rpm's to deb's.

---

### Post by oldos2er on 2010-08-30
> **om.rameshwar said:**
> well am tryin to install MySQL... in the homepage i got rpm file of MySQL... so downloaded that... so need lil help wid tat... :)

mysql is in the repositories. ```
sudo apt-get update && sudo apt-get install mysql-client mysql-server
``` for example.

---

