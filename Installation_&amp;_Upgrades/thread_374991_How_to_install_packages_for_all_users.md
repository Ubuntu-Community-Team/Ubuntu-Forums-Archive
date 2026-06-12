---
title: "How to install packages for all users?"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by darklobin on 2007-03-03
hello! well this is the first post here in this forum and i really hope you guys can help me. my problem is basically what the title says: i need to install a package for all users. example, the java 6 and plugin for firefox package, right now i need to install it for every new user i create. isn't there a way to do this only one time?

thanks in advance :)

---

### Post by darklobin on 2007-03-04
anyone?

---

### Post by bollix47 on 2007-03-04
You shouldn't have to install java for each user.  Once it's installed it should be available to all users.

Try running:

 ```
sudo update-alternatives --config java

```

and select java-6-sun

---

### Post by darklobin on 2007-03-05
hey! thanks for the info! i'll try that, but what about flash player? i had to download it again too. :(

---

