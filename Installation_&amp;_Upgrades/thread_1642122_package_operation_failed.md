---
title: "package operation failed"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by randy48 on 2010-12-09
Hi when I try to update with update manager 

I'm running ubuntu netbook remix 10.10 here is the error I get every time I try to use update manager to update 

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: failed to read on buffer copy for copy info file `/var/lib/dpkg/available': Input/output error 


anyone know what might cause this error?

thx

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

Go to Applications > Accessories > Terminal and try this command.

```
sudo dpkg --clear-avail
```

Then post the output of this one.

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by randy48 on 2010-12-13
Thanks it installed the packages I had already downloaded and i also managed to download a few apps

---

