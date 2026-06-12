---
title: "Package system is broken"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by dparla on 2011-09-29
I am getting the following error when running update manager:
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
The following packages have unmet dependencies:
jonas-5.2: Depends: java5-jdk but it is not installed
           Depends: upstart-job but it is a virtual package

I tried to enter  apt-get install -f in my terminal but it doesn't recognize the command.

---

### Post by collisionystm on 2011-09-29
sudo apt-get install -f

---

