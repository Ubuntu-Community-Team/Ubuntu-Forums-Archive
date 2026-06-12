---
title: "Problems finding and installing Open Office"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by rye37 on 2011-06-07
No matter how I try, or how many sources I go to, every instance of open office gives me an error message saying that the JRE (Java) file is corrupt.
I cannot find an instance of Open Office I can download regardless of the version.
I have no Open Office now. How can I find a version that will give me the entire package AND install?
I've had a lot of  trouble getting any version to install...but that may be due to the corruption of the JRE file

---

### Post by wildmanne39 on 2011-06-07
> **rye37 said:**
> No matter how I try, or how many sources I go to, every instance of open office gives me an error message saying that the JRE (Java) file is corrupt.
I cannot find an instance of Open Office I can download regardless of the version.
I have no Open Office now. How can I find a version that will give me the entire package AND install?
I've had a lot of  trouble getting any version to install...but that may be due to the corruption of the JRE file

Hi, first libre office comes with natty and openoffice comes with all previous versions of ubuntu. You should remove that version of java that is corrupt with this command.
```
sudo apt-get --purge remove packagename
```Install java with
```
sudo apt-get install openjdk-6-jdk openjdk-6-jre
```or just use software center to install it you have to accept the agreement and then it should install. Make sure it get rid of the old one first.

---

