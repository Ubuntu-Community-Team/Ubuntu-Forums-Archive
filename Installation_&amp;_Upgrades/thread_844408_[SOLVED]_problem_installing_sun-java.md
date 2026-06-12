---
title: "[SOLVED] problem installing sun-java"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by rocky_snist on 2008-06-29
hi, 
    iam a new kubuntu user ,when i was installing sun java on to my system i got a problem , when i opened the "adept manager" it showed a message "the application  Adept manager crashed and caused the signal6(SIGABRT)"....i was installing the package using "$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts"  command ..
  please help to get rid of this problem and carry with installation..

---

### Post by Pumalite on 2008-06-29
Run:
sudo dpkg --configure -a
And post the output.

---

### Post by rocky_snist on 2008-06-29
the output is " dpkg: status database area is locked by another process"

---

### Post by Pumalite on 2008-06-29
You might have Synaptic open. Close it. Try again.

---

### Post by rocky_snist on 2008-06-29
i closed syneptic and tried out the command u have suggested ,it showed "dpkg: requested operation requires superuser privilege" message

---

