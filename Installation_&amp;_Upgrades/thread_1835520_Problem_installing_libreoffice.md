---
title: "Problem installing libreoffice"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2011-08-29
I just did an upgrade from 9.10 to 10.04. Pretty smooth. 
I am trying to go from open office to libreoffice. I am following the [instructions on the wiki]("https://wiki.ubuntu.com/LibreOffice"). I am receiving dependency errors when try to install
```
sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libreoffice: Depends: libreoffice-core (= 1:3.3.2-1ubuntu2~lucid1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.3.2~) but it is not going to be installed
E: Broken packages

```
I did not receive any error when adding the repository or when I updated. Is the repository broken by any chance?

---

