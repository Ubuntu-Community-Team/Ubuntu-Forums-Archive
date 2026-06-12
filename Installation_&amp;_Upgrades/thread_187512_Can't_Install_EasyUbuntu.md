---
title: "Can't Install EasyUbuntu"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by markfasano on 2006-06-03
I don't seem to be able to complete an installation of EasyUbuntu. Furthermore, when I attempt to install individual packages, I get the following:

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Any ideas?

---

### Post by Jussi Kukkonen on 2006-06-03
Have you done what the error message suggests?
```
sudo apt-get -f install
```
Also, make sure you have Multiverse repository enabled: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

