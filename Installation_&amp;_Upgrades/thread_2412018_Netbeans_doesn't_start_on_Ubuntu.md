---
title: "Netbeans doesn't start on Ubuntu"
date: 2019-02-07
forum: Installation &amp; Upgrades
---

### Post by theasianmamba24 on 2019-02-07
With Java installed and JDK installed (in /usr/lib/jvm directory), I can't seem to open Netbeans via the terminal. I installed it with "sudo apt-get install netbeans". I've recently installed Netbeans 8.2 with the **.sh** file I downloaded online, I ran the script and I could open it, but I got the error message when I tried to create a new Java Project:

"Not all requested modules can be enabled."

I have also tried changing **netbeans_jdkhome **in the /etc directory to "/usr/lib/jvm/java-8-oracle".

What should I do?

---

### Post by slickymaster on 2019-02-07
Make sure the variable **netbeans_jdkhome** in **/etc/netbeans.conf** has the correct value```
netbeans_jdkhome="/usr/lib/jvm/java-8-oracle"
```

---

### Post by theasianmamba24 on 2019-02-07
Thanks for the quick response. I have checked my variable and it is in the exact format and java-8-oracle is in fact in that directory, but the issue remains.

---

