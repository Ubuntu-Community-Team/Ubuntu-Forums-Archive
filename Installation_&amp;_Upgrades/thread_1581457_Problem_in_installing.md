---
title: "Problem in installing"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by robinpaschal on 2010-09-25
When i am following with the command 

> sudo aptitude install sun-java6-[jre]("http://en.kioskea.net/telecharger/telecharger-101-java-runtime-environment") sun-java6-plugin

The following error occurring.


> dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.



What should i do?

---

### Post by CharlesA on 2010-09-25
What happens if you run this:

```
sudo dpkg --configure -a
```

---

### Post by robinpaschal on 2010-09-25
Well charles...thanks.

The putput of your command is following. 

Setting up java-common (0.30ubuntu5) ...

> Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

---

### Post by lisati on 2010-09-25
It looks like it worked. Did the command run to completion without errors?

---

### Post by robinpaschal on 2010-09-25
Ya It is....Thanks for sharing.

---

