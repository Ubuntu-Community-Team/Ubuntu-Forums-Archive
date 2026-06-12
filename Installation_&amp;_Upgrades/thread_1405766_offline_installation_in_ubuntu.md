---
title: "offline installation in ubuntu"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by mirinamulhaq on 2010-02-13
hi guys, i downloaded some packages from ubuntu website on my pen-drive now i want to install those on my ubuntu karmic using synaptic package manager , but whenever i try to install them it shows check network connection .however i dont have any internet a my home and i just want to directly install these packages from my pendrive .how can i do so.

---

### Post by byStanderone on 2010-02-13
...not sure in what file format those files are (packages), synaptic acknowledges file install only from its source list , unless of course you have made your cd in such a way as to be recognized by synaptic as such.

unlike .deb and .tar, these type of packages can be installed by other applications.

had came across this process of making a synaptic recognizable cd, but
haven't done this again since gutsy, and am not sure it that gutsy process would work in karmic.

---

### Post by MelDJ on 2010-02-13
maybe the packages have dependencies which need to be downloaded.

---

### Post by prshah on 2010-02-13
> **mirinamulhaq said:**
> downloaded some packages from ubuntu website ... now i want to install those on ... karmic using synaptic package manager ... shows check network connection ... directly install these packages from my pendrive

If the filenames end in ".deb" (and that you have downloaded dependent files) then you can install them by using the terminal (Applications-Accessories-Terminal)```
cd /media/FA0C-BAC1 # change as suitable to your pen drive
sudo dpkg -i *.deb
```

Typically, you will be alerted if you have missing dependencies.

---

### Post by mikewhatever on 2010-02-13
If you want to install the downloaded packages from Synaptic, you'll need to create a local repository, otherwise, it's double clicking, or <sudo dpkg -i package-name> command. There is also a tool called Keryx.
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by mirinamulhaq on 2010-02-13
when i try to install a package it shows some additional files are required but i dont know why they are not present in the package itself if we download it from ubuntu official website.what is the other alternative for downloading these additional files because i dont know what additional files the package manager is asking for.

---

### Post by MelDJ on 2010-02-13
you can install them from the ubuntu packages site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/). but it will be troublesome as the dependencies might have their own dependencies

---

